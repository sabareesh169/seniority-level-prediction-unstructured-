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

#### Skill Set WordCloud

![image](https://user-images.githubusercontent.com/25951391/79076024-976d5c80-7cab-11ea-884f-2690d1d725fc.png)

Database, project mangement, customer service seems to be some of the most common skills. This means that while these skills are good to have, these might not be the differentiating skills between candidates. Also, these skills can be considered as essential skills to have.

#### Distribution of people against their highest degree
![image](https://user-images.githubusercontent.com/25951391/79076043-caafeb80-7cab-11ea-86ac-85e35a85e97d.png)

This will now be the reference distribution when we plota feature w.r.t their degree. If education degree had no effect on a feature, the count plot at each level of the feature should be distributed in the same manner with Bachelors being the highest and Masters second at approximately half the amount.

#### Distribution of years of experience

![image](https://user-images.githubusercontent.com/25951391/79076170-d819a580-7cac-11ea-924c-b0f696984bce.png)

The distribution doesn't throw up any surprises and is slightly skewed to the right as expected.

#### Unemployment rate with degree

![image](https://user-images.githubusercontent.com/25951391/79076661-cb974c00-7cb0-11ea-8f5b-cd15e2ac1900.png)

Looks like a decreasing trend with education. Smallest ratio is for PhD degree while Diploma has a surprisingly high number as well

#### Distribution of education level for each seniority level.

![image](https://user-images.githubusercontent.com/25951391/79076681-f4b7dc80-7cb0-11ea-9cb5-29e1be008df4.png)
The trend more or less proportional to the count of each degree. MBA degree gaining prominence at higher level. Management becomes more and more important at higher seniority level.

#### Distribution of experience at each seniority level

![image](https://user-images.githubusercontent.com/25951391/79076760-7871c900-7cb1-11ea-836c-7f138e6f70ad.png)
Apart from the initial blip of 'Entry' having less experience than 'Intern', the trend is pretty much what you would expect with experience increasing with each level. This is logical since it takes time for someone to rise to higher ranks and hence will have gained higher experience.

#### Distribution of years of experience vs education for each seniority level.

![image](https://user-images.githubusercontent.com/25951391/79076814-c71f6300-7cb1-11ea-9b08-561a687052f5.png)
Surprisingly, no trend visible. The number of people with degree less than Bachelors become sparse for higher seniority level. These graphs are interesting since they seem to suggest that inspite of some people having higher education like PhD, MBA, they still need the same years experience as the people with Associate degree or a diploma. This begs the question if it is more useful to start work early and gain knowledge in a hands-on way rather than gain knowledge in a academic setting. 

#### Distribution of seniority level based on degree.
![image](https://user-images.githubusercontent.com/25951391/79076915-46149b80-7cb2-11ea-8d20-4e10954f8e01.png)
The trends seem to suggest that it might be difficult to advance to higher seniority level (Senior or more) unless you have a Bachelor or higher degree.

#### Distribution of number of skills with seniority

![image](https://user-images.githubusercontent.com/25951391/79076937-67758780-7cb2-11ea-9c26-b2f2d8a9e026.png)
The red line shows the mean of number of skills at each seniority level. Continuously increasing at each level (apart from intern). You need to always learn to climb the seniority level. Don’t stagnate.

#### Distribution of number of jobs with seniority level
![image](https://user-images.githubusercontent.com/25951391/79076967-a7d50580-7cb2-11ea-9c60-2c775915b40e.png)
Higher the seniority level, higher the number of jobs they had till then. 

#### Distribution of jobs and companies
![image](https://user-images.githubusercontent.com/25951391/79076994-dce15800-7cb2-11ea-8ba2-78435b75cbc8.png)
A small gap between the number of jobs and companies. Less growth opportunities within the company? 
Scope for the companies to provide more promotions to retain workforce. 

#### Distribution of seniority for each major
![image](https://user-images.githubusercontent.com/25951391/79077028-07331580-7cb3-11ea-85e3-320966f97daa.png)
No surprising or visible trends other than the one we have seen already. Requiring management skills for higher seniority levels.

### Model for predicting seniority level
Built Decision Trees and Random Forests with hyperparameter tuning to obtain an accuracy of 0.52
