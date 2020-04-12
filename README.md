# seniority-level-prediction-unstructured

## Introduction
The dataset contains the profiles of different people with their seniority level (based on their current jobs), education and their experience. The dataset contains 29969 rows, each row corresponding to an individual. We will try to clean the data, visualize and hopefully draw some insights from the distributions. 

This data being parsed from resume will contain lot of errors as well as missing values as some fields are optional in most applications. the first step therefore is to clean the data and then hopefully derive some insights into the distribution.

## Data visualization

First, we plot the number of people in each category of seniority level.
![image](https://user-images.githubusercontent.com/25951391/79074765-08f4dd00-7ca3-11ea-9a19-96d36309ebd5.png)

The distribution of the seniority level is shown here. We observe that number of people decrease with increase in seniority level. It is not surprising that most of the people fall into the ‘Entry’ level category. After all, most organizations have a funnel shaped hierarchical system with fewer people ascending to the next step.

### Feature extraction
We can extract features like major, highest degree, number of jobs and number of companies from the data.

The major is divided into 6 categories of STEM, Sciences, Administration, Marketing, Economics, Other(anything else like history, politics, etc) and Unknown(corresponding to not listed). Similarly, we take the highest degree listed and take each of the majors if he has two degrees. We also capture the number of different jobs and the different comapnies a person worked for throughout his/her career.

We also calculate the total experience taking out any overlap of listed experiences. So, if a person does two jobs at the same time, we only count as one job expreience. And also add other features like if he is currently in school or not, whether he is currently employed or not, whether he is someone who went back to studying after working for some time and whether he has a dual degree.

### Skill Set WordCloud

![image](https://user-images.githubusercontent.com/25951391/79076024-976d5c80-7cab-11ea-884f-2690d1d725fc.png)

Database, project mangement, customer service seems to be some of the most common skills. This means that while these skills are good to have, these might not be the differentiating skills between candidates. Also, these skills can be considered as essential skills to have.

Distribution of people against their highest degree
![image](https://user-images.githubusercontent.com/25951391/79076043-caafeb80-7cab-11ea-86ac-85e35a85e97d.png)

This will now be the reference distribution when we plota feature w.r.t their degree. If education degree had no effect on a feature, the count plot at each level of the feature should be distributed in the same manner with Bachelors being the highest and Masters second at approximately half the amount.

Distribution of years of experience

![image](https://user-images.githubusercontent.com/25951391/79076170-d819a580-7cac-11ea-924c-b0f696984bce.png)

The distribution doesn't throw up any surprises and is slightly skewed to the right as expected.

