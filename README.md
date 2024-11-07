# CognoRise-Infotech-

## EMPLOYEES SALARIES FOR DIFFERENT JOB ROLES (descriptive analysis)

### CONTENT

- [AIMS AND OBJECTIVES](#AIMS-AND-OBJECTIVES)
- [ANALYSIS](#ANALYSIS)
- [KEY INSIGHT](#KEY-INSIGHT)
- [CONCLUSION](#CONCLUSION)
- [SQL](#SQL)

This project aims to drive out all the data jobs, their experience level with their salary tailored with the cost of living in a particular country
### AIMS AND OBJECTIVES
1. Observed all the highest paid job variations across different country.
2. Drives out all the jobs with their level of experience.
3. Their respective average salary tailored with their cost of living to choose a preferable career in a particular country
4. All jobs with the level of their remote ratio in each country.
5. Job ranking with their respective salary

### ANALYSIS

Remote positions in 2021-2022, particularly in leadership and technical roles, show significantly high salaries, with averages over $400,000. Positions like Director of Data Science often allow remote work, with salaries around $325,000. In contrast, roles such as Machine Learning Scientist and Research Scientist, which are primarily on-site (remote ratio <10%), are also high-paying, with annual salaries above $240,000. This trend highlights a premium on remote flexibility for specialized and leadership roles during this period

In 2021 and 2022, senior-level data roles in the U.S. saw significant salary differences, with top-tier positions reaching over $400,000 annually. Key roles such as Financial Data Analyst, Principal Data Analyst, Principal Data Scientist, Data Analyst Lead, and Applied Data Scientist also commanded high salaries, averaging over $220,000. However, the highest-paid senior roles each year consistently exceeded the $400,000 threshold, highlighting a premium on advanced expertise in the data field in both years.

Senior roles such as Director of Data Science and top-tier Data Analysts show the highest earnings, with most of these positions concentrated in the financial and tech industries, reflecting these sectors' demand for advanced data expertise.Mid-level data scientists consistently earn more than entry-level counterparts and are predominantly employed in Canada and the USA, where demand and compensation for mid-level talent are strong.Entry-level positions have lower earnings, but progression to mid-level and senior roles offers significant salary increases, especially in financial and tech sectors, where data science expertise is highly valued.

From 2020 to 2022, data role salaries showed stark disparities by role and experience level. In 2020, Product Data Analysts earned as low as $13,000, while Directors of Data Science earned up to $325,000. In 2021, 3D Computer Vision Researchers earned $5,409 on average at mid-level, whereas Financial Data Analysts reached $405,000. By 2022, entry-level Data Analyst Engineers earned $20,000, with senior counterparts making up to $405,000. This trend reflects an increasing emphasis on experience and specialization, particularly in tech and finance.  Most higher paid remote jobs are available in the united state (more emphasis on financial data analyst and director of data scientist).

From 2020 to 2022, data role salaries varied widely, reflecting cost-of-living adjustments in the USA and Canada. Lower salaries, such as Product Data Analysts earning $13,000 (2020) or 3D Computer Vision Researchers at $5,409 (2021), fall below sustainable income levels in high-cost areas. By contrast, high-paying roles, like Directors of Data Science ($325,000 in 2020) and Financial Data Analysts ($405,000 in 2021), align better with the high cost of living, especially in major cities. For Data Analyst Engineers in 2022, salaries spanned from $20,000 (entry) to $405,000 (senior), illustrating a significant gap in affordability and quality of life based on experience.

![cog_viz1](https://github.com/user-attachments/assets/c96f5212-faf9-46c6-b79b-9322633c83ae)


### KEY INSIGHT (descriptive analysis)
This insight is going to be based on the year 2020,2021 and 2022

1. Most of the remote jobs are high paid mostly in year (2021 and 2022) which pay scale is over $400000 on annual average salary
2. A Mid-level data scientist earn more than the entry level and they tends to get jobs mostly in Canada and USA
3. Most director of data scientist and top senior(higher class) data analyst tend to earn more and due to the analysis more attention is shifted to financial and tech companies
4. In year 2020, product data analyst earn as low as $13000 while a director of data scientist earn as high as $325000 on an average.
5. In 2021, 3D computer vision researcher earn as low as $5409 while a financial data analyst earn as high as $405000 on an average both on mid level class of experience
6. In 2022, a data analyst engineer earn as low as $20000 on an average as an entry level while $405000 on an average as a senior level.
7.  Most higher paid remote jobs are on available in the united state (more emphasis on financial data analyst and director of data scientist)

![cog_viz2](https://github.com/user-attachments/assets/9932a6eb-d59c-4e80-8406-c938bc471201)


### CONCLUSION on Top 3 Highest-Paid Data Roles (USA and Canada, 2020-2022)
1. Financial Data Analyst (2021) - $405,000
2. Data Analyst Engineer (Senior, 2022) - $405,000
3. Director of Data Science (2020) - $325,000
These top roles offered the most competitive salaries, aligning well with the high cost of living in major cities across the USA and Canada, especially in tech and finance.

### SQL
CODE USED FOR DATA CLEANING

``` SQL
drop database employee_salary;

create database employee_salary;

drop table ds_salaries;
create table ds_salaries(
		NUM int,
        work_year INT,
        experience_level varchar(3),
        employment_type varchar(3),
        job_title varchar(30),
        salary decimal(12,3),
        salary_currency varchar(5),
        salary_in_usd decimal(12,3),
        employee_residence varchar(5),
        remote_ratio int,
        company_location varchar(5),
        company_size varchar(5)
);

select 
	*
from
	ds_salaries;
    
select 
	*,
    row_number() over(partition by num, work_year, experience_level)
from
	ds_salaries;

drop table if exists ds_salaries_2;
CREATE TABLE `ds_salaries_2` (
  `NUM` int DEFAULT NULL,
  `work_year` int DEFAULT NULL,
  `experience_level` varchar(3) DEFAULT NULL,
  `employment_type` varchar(3) DEFAULT NULL,
  `job_title` varchar(30) DEFAULT NULL,
  `salary` decimal(12,3) DEFAULT NULL,
  `salary_currency` varchar(5) DEFAULT NULL,
  `salary_in_usd` decimal(12,3) DEFAULT NULL,
  `employee_residence` varchar(5) DEFAULT NULL,
  `remote_ratio` int DEFAULT NULL,
  `company_location` varchar(5) DEFAULT NULL,
  `company_size` varchar(5) DEFAULT NULL,
  `row_num` int DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

insert into ds_salaries_2
select 
	*,
    row_number() over(partition by num, work_year, experience_level) as row_num
from
	ds_salaries;
    

select 
	*
from
	ds_salaries_2
where row_num > 1;

delete 
from 
ds_salaries_2
where row_num > 1;

alter table ds_salaries_2
drop column row_num;

select 
	*
from
	ds_salaries_2;
```
### THIS CODE WAS USED FOR DATA CLEANING

#### For more information view the tableau dashboard
