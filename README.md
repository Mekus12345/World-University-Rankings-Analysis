# World-University-Rankings-Analysis

CREATE DATABASE UniversityRankings;

USE UniversityRankings;

-- 1. import table
select * from uni_rankings2024;

/* Data Exploration Using SQL
Explore the structure of the dataset using basic SQL queries 
(e.g., SELECT, COUNT(), GROUP BY, etc.).*/

-- 2. View the structure of the table
describe uni_rankings2024;

-- Check the total number of record
select count(*) from uni_rankings2024;

-- 3. Analysis Questions
-- i. Top Universities by Overall Score
-- Create view Top10_uni as
select university, 
overall from uni_rankings2024
order by Overall 
desc
limit 10;

-- ii. Top Countries by Research Performance
-- Create view Top10_countryR as
select country,
avg(Research) as avg_research_score
from uni_rankings2024
group by country
order by avg_research_score
desc
limit 10;

-- iii. Impact of International Outlook on Rankings
-- Create view International_Outlook as
SELECT University, 
  `rank`, 
  `international outlook`
FROM uni_rankings2024
WHERE `international outlook` > 90;

-- iv. Overall best university in teaching
-- Create view max_teaching as
select university, 
max(teaching) from uni_rankings2024
group by University
order by max(Teaching) desc
limit 1;

-- v. Correlation Between Industry Income and Rankings
-- Create view industry_income as
select university,
`rank`,
`industry income`
from uni_rankings2024
where `industry income` > 90;


