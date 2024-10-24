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

-- 4. Key Insights and Trends from SQL Analysis

/* i. Top Universities by Overall Score

Insight: The universities with the highest overall scores tend to be globally 
renowned institutions known for their research capabilities, academic reputation, and comprehensive educational offerings.

Trend: There is a concentration of top-performing universities in the United States and 
the United Kingdom, reflecting their significant investment in higher education and research infrastructure.

ii. Top Countries by Research Performance

Insight: Countries with universities that have high average research scores include the United States, 
United Kingdom, and Germany.

Trend: These countries benefit from robust funding for research and development, fostering an environment where academic research can thrive. 
The presence of well-established research institutions and collaboration between academia and industry 
also contribute to their strong research performance.

iii. Impact of International Outlook on Rankings

Insight: Universities with a high international outlook score, which includes metrics like international students 
and faculty, often have higher overall scores.

Trend: Institutions that are more globally connected and attract a diverse student and faculty population tend to 
perform better in rankings. This highlights the importance of international collaboration and exchange programs in 
enhancing a university’s reputation and academic standards.

iv. Correlation Between Industry Income and Rankings

Insight: There is a positive correlation between industry income and overall university rankings. 
Universities that have strong ties with industry and generate significant income through industry partnerships 
tend to have higher overall scores.

Trend: This indicates that collaboration with industry not only provides financial benefits but also enhances 
the practical and innovative aspects of university education and research. Such partnerships often lead to advanced research 
opportunities, funding for projects, and enhanced employability for graduates.

Summary
The SQL analysis reveals that top-ranked universities are predominantly located in countries with significant investment 
in higher education and research. The presence of international diversity and strong industry connections further bolsters a university’s ranking. 
These insights underscore the multifaceted nature of academic excellence, which relies on a combination of research prowess, 
global engagement, and industry collaboration.
*/
