
<img width="812" alt="hr-image-small" src="https://github.com/RashidTobrazune/Customer_analytics_Preparing_datafor_modeling/assets/150378293/c4669c8e-ce9a-4e48-b341-3706e4e8f6a2">

![pexels-rdne-4921150](https://github.com/RashidTobrazune/Customer_analytics_Preparing_datafor_modeling/assets/150378293/04671bfb-1fc6-4881-92db-aa7babf4feb6)

# Customer_analytics_Preparing_datafor_modeling
Datacamp Project

A common problem when creating models to generate business value from data is that the datasets can be so large that it can take days for the model to generate predictions. Ensuring that your dataset is stored as efficiently as possible is crucial for allowing these models to run on a more reasonable timescale without having to reduce the size of the dataset.

I was hired by a major online data science training provider called Training Data Ltd. to clean up one of their largest customer datasets. This dataset will eventually be used to predict whether their students are looking for a new job or not, information that they will then use to direct them to prospective recruiters.

I was given access to customer_train.csv, which is a subset of their entire customer dataset, so I can create a proof-of-concept of a much more efficient storage solution. The dataset contains anonymized student information, and whether they were looking for a new job or not during training:

Column	Description
student_id	 A unique ID for each student.
city	 A code for the city the student lives in.
city_development_index	 A scaled development index for the city.
gender	 The student's gender.
relevant_experience	 An indicator of the student's work relevant experience.
enrolled_university 	The type of university course enrolled in (if any).
education_level	 The student's education level.
major_discipline 	The educational discipline of the student.
experience	 The student's total work experience (in years).
company_size	 The number of employees at the student's current employer.
company_type	 The type of company employing the student.
last_new_job	 The number of years between the student's current and previous jobs.
training_hours	 The number of hours of training completed.
job_change	 An indicator of whether the student is looking for a new job (1) or not (0).

Task

The Head Data Scientist at Training Data Ltd. has asked you to create a DataFrame called ds_jobs_clean that stores the data in customer_train.csv much more efficiently. Specifically, they have set the following requirements:

Columns containing integers must be stored as 32-bit integers (int32).
Columns containing floats must be stored as 16-bit floats (float16).
Columns containing nominal categorical data must be stored as the category data type.
Columns containing ordinal categorical data must be stored as ordered categories, and not mapped to numerical values, with an order that reflects the natural order of the column.
The columns of ds_jobs_clean must be in the same order as the original dataset.
The DataFrame should be filtered to only contain students with 10 or more years of experience at companies with at least 1000 employees, as their recruiter base is suited to more experienced professionals at enterprise companies.
If you call .info() or .memory_usage() methods on ds_jobs and ds_jobs_clean after you’ve preprocessed it, you should notice a substantial decrease in memory usage.

I performed analysis on the data and answered the questions. 
I reduced the memory usage for this dataframe.
Here is a glance;

class 'pandas.core.frame.DataFrame'>
RangeIndex: 19158 entries, 0 to 19157
Data columns (total 14 columns):
 #   Column                  Non-Null Count  Dtype  
---  ------                  --------------  -----  
 0   student_id              19158 non-null  int64  
 1   city                    19158 non-null  object 
 2   city_development_index  19158 non-null  float64
 3   gender                  14650 non-null  object 
 4   relevant_experience     19158 non-null  object 
 5   enrolled_university     18772 non-null  object 
 6   education_level         18698 non-null  object 
 7   major_discipline        16345 non-null  object 
 8   experience              19093 non-null  object 
 9   company_size            13220 non-null  object 
 10  company_type            13018 non-null  object 
 11  last_new_job            18735 non-null  object 
 12  training_hours          19158 non-null  int64  
 13  job_change              19158 non-null  float64
dtypes: float64(2), int64(2), object(10)
memory usage: 2.0+ MB
<class 'pandas.core.frame.DataFrame'>
Int64Index: 2201 entries, 9 to 19143
Data columns (total 14 columns):
 #   Column                  Non-Null Count  Dtype   
---  ------                  --------------  -----   
 0   student_id              2201 non-null   int32   
 1   city                    2201 non-null   category
 2   city_development_index  2201 non-null   float16 
 3   gender                  1821 non-null   category
 4   relevant_experience     2201 non-null   bool    
 5   enrolled_university     2185 non-null   category
 6   education_level         2062 non-null   category
 7   major_discipline        2097 non-null   category
 8   experience              2201 non-null   category
 9   company_size            2201 non-null   category
 10  company_type            2144 non-null   category
 11  last_new_job            2184 non-null   category
 12  training_hours          2201 non-null   int32   
 13  job_change              2201 non-null   bool    
dtypes: bool(2), category(9), float16(1), int32(2)
memory usage: 69.5 KB
