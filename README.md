
13/09/24
-------------------------------------------------
Practising - SQL from Hacker Rank
-------------------------------------------------

 
select Name from city
where population >120000 and countrycode ='USA';

 id%2=0; for even number we use this 
 id%2<>0; for ODD number we use this 

select Count(
(city)-distinct(city)
) from station;

while using aggregation you have to use it evenly 
aggregate funtion to get result

select count (city)-count(distinct (city)) from station;

select min(city), len (min(city)) from station
order by  min(city) ;
select max(city), len (max(city)) from station
order by  min(city) ;

select top 1 city, len (city) from station order by len (city),city asc;
select top 1 city, len (city) from station order by len (city) desc, city desc;
i got stuck in this query as im using MIN&MAX aggregate function.

select name from students
where marks>75 
order by right(name,3),ID asc ;
(in this query i found that i shld also right functions with order by.
as i till know tht it only used with select statement)

Q.
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Q.
Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than  per month who have been employees for less than  months. Sort your result by ascending employee_id.

select name from employee
where salary >2000 and months < 10
order by employee_id asc;

Q.
Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7780. 
Round your answer to  decimal places

select round(min(LAT_N),4) from station
where LAT_N>38.7780;

result-38.8526

Q.
Query the Western Longitude (LONG_W)where the smallest 
Northern Latitude (LAT_N) in STATION is greater than 38.7780 .
Round your answer to 4 decimal places.

select ROUND(min(lat_n),4) as long_w from station
where long_w > 38.7780; 
25.0735

select top 1 format(round (MIN(LAT_N),4),'##.####'
) as LONG_W from station
where LONG_W > 38.7780
order by lat_n;

select TOP 1 format(round(long_W,4),'##.####') from station
where lat_n>38.7780
order by LAT_N;

70.1378



------------------------------
16/09/24
------------------------------


Q.
Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.
OUTPUT

select
CASE 
     when A+B<=C OR B+C<=A OR C+A<=B THEN 'Not A Triangle'
     when A=B AND B=C AND B=C then 'Equilateral'
     when A=B OR B=C OR C=A then 'Isosceles'
     when A<>B OR B<>C OR C<>A then 'Scalene'
     END as 'tuple'
from TRIANGLES;


Q.
Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

There are a total of [occupation_count] [occupation]s.
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

select CONCAT(name,'(',left(occupation,1),')') 
from OCCUPATIONS 
order by name;

select CONCAT('There are a total of',' ',count(occupation),' ',lower(occupation),'s.') 
from OCCUPATIONS 
group by occupation 
order by count(occupation), occupation;

--

select 
case
when P = 15 then 'ROOT'
when P in (2,4,6,9,11,13) and N in (2,4,6,9,13) then 'Inner'
when N in (1,3,5,7,8,10,12,14) then 'Leaf'
end as 'type of node'
from bst;


select roll_number,name 
from student_information
 INNER JOIN on student_information.roll_number=examination_marks.roll_number
where subject_one+subject_two+subject_three>100;

Practise of SQL Basic On HackerRANK
&
Also got certified for SQL BASIC from HackerRank.

POWER BI:-

Also started working on Power BI (Maven Market Report)

PART 1: Connecting & Shaping the Data(BackEnd Related)





------------------------------------------
17/09/2024
POWER BI Maven REPORT 
------------------------------------------
POWER Bi
PART 2: Creating the Data Model-Made a relation between tables .
PART 3: Adding DAX Measures to 

SQL 
Practise  SQL BASIC on HackerRank & also got certification for SQL BASIC from HackerRank.

Q.
In the Customers table, add a column named "Priority"
Equals "High" for customers who own homes and have Golden membership cards (otherwise "Standard") 


1) In the DATA view, add the following calculated columns:

a)In the Calendar table, add a column named "Weekend"
Equals "Y" for Saturdays or Sundays (otherwise "N")

Weekend = 
if(
    Calandar[Day Name]="saturday","y",
    if(
        Calandar[Day Name]="sunday","y","n"
    )
)

b)In the Calendar table, add a column named "End of Month"
Returns the last date of the current month for each row

End of Month = EOMONTH(
    Calandar[Start of Month],0) 

to get the LAST DATE OF MONTH


c)In the Customers table, add a column named "Current Age"
Calculates current customer ages using the "birthdate" column and the TODAY() function

Current Age = DATEDIFF(Customers[birthdate], TODAY(), YEAR)
to get current date you use today function = for current date
birthdate= from which you got the date.
year= as interval to get Current age

d)In the Customers table, add a column named "Priority"
Equals "High" for customers who own homes and have Golden membership cards (otherwise "Standard")  


Priority = IF
(
    Customers[homeowner]="Y" && Customers[member_card]="golden",
    "high",
    "standard"
    
    )
 
e)In the Customers table, add a column named "Short_Country"
Returns the first three characters of the customer country, and converts to all uppercase 

Short_Country = UPPER(
    LEFT(Customers[Country/Region],3)
)




f)In the Customers table, add a column named "House Number"
Extracts all characters/numbers before the first space in the "customer_address" column (hint: use SEARCH)

House Number = LEFT(Customers[customer_address], 
SEARCH(" ", Customers[customer_address])
 - 1)


g)In the Products table, add a column named "Price_Tier"
Equals "High" if the retail price is >$3, "Mid" if the retail price is >$1, and "Low" otherwise

Price_Tier = IF(Products[product_retail_price]>3,"High",
IF(Products[product_retail_price]>1,"Mid",
"Low")
)


h)In the Stores table, add a column named "Years_Since_Remodel"
Calculates the number of years between the current date (TODAY()) and the last remodel date

Years_Since_Remodel = DATEDIFF(Stores[last_remodel_date],TODAY(),YEAR).



PART - 2 (DAX Queries solving to make MAven )


In the REPORT view, add the following measures (Assign to tables as you see fit, and use a matrix to match the "spot check" values)
a)
Create new measures named "Quantity Sold" and "Quantity Returned" to calculate the sum of quantity from each data table
Spot check: You should see total Quantity Sold = 833,489 and total Quantity Returned = 8,289

Quantity Sold

Quantity Sold = SUM(Transaction_Data[quantity])

"Quantity Returned"

Quantity Returned = SUM(
    Returns_Data[quantity]
)

b)
Create new measures named "Total Transactions" and "Total Returns" to calculate the count of rows from each data table
Spot check: You should see 269,720 transactions and 7,087 returns

Total Transactions = COUNT(
    Transaction_Data[quantity])


Total Returns = COUNT(
    Returns_Data[quantity])
    
c)
Create a new measure named "Return Rate" to calculate the ratio of quantity returned to quantity sold (format as %)
Spot check: You should see an overall return rate of 0.99%

Return Rate = [Quantity Returned]/[Quantity Sold]

Notes : || for OR , && for AND

d)
Create a new measure named "Weekend Transactions" to calculate transactions on weekends
Spot check: You should see 76,608 total weekend transactions

Weekend Transactions = CALCULATE([Total Transactions],Calandar[Weekend]="Y")

e)
Create a new measure named "% Weekend Transactions" to calculate weekend transactions as a percentage of total transactions (format as %)
Spot check: You should see 28.4% weekend transactions

% Weekend Transactions = [Weekend Transactions]/[Total Transactions]

f)
Create new measures named "All Transactions" and "All Returns" to calculate grand total transactions and returns (regardless of filter context)
Spot check: You should see 269,720 transactions and 7,087 returns across all rows (test with product_brand on rows)

g)
Create a new measure to calculate "Total Revenue" based on transaction quantity and product retail price, and format as $ (hint: you'll need an iterator)
Spot check: You should see a total revenue of $1,764,546

Total Revenue = SUMX(
    Transaction_Data,Transaction_Data[quantity]*RELATED(Products[product_retail_price]
    )
)

h)
Create a new measure to calculate "Total Cost" based on transaction quantity and product cost, and format as $ (hint: you'll need an iterator)
Spot check: You should see a total cost of $711,728

Total cost = SUMX(
    Transaction_Data,Transaction_Data[quantity]*RELATED(Products[product_cost])
)

i)
Create a new measure named "Total Profit" to calculate total revenue minus total cost, and format as $
Spot check: You should see a total profit of $1,052,819

j)
Create a new measure to calculate "Profit Margin" by dividing total profit by total revenue calculate total revenue (format as %)
Spot check: You should see an overall profit margin of 59.67%

Profit Margin = [Total Profit]/[Total Revenue] 

k)
Create a new measure named "Unique Products" to calculate the number of unique product names in the Products table
Spot check: You should see 1,560 unique products

Unique Products = DISTINCTCOUNT(Products[product_name])

l)
Create a new measure named "YTD Revenue" to calculate year-to-date total revenue, and format as $
Spot check: Create a matrix with "Start of Month" on rows; you should see $872,924 in YTD Revenue in September 1998

YTD Revenue = 
CALCULATE([Total Revenue],
    DATESYTD(Calandar[date]))

---------------------------

18/09/24

---------------------------

m)
Create a new measure named "60-Day Revenue" to calculate a running revenue total over a 60-day period, and format as $
Spot check: Create a matrix with "date" on rows; you should see $97,570 in 60-Day Revenue on 4/14/1997

60 Day Revenue = CALCULATE(
    [Total Revenue],
    DATESINPERIOD(

        Calandar[date],MAX(
            Calandar[date]),-60,DAY

)
)

n)
Create new measures named  "Last Month Transactions", "Last Month Revenue", "Last Month Profit", and "Last Month Returns"
Spot check: Create a matrix with "Start of Month" on rows to confirm accuracy

Last Month Transactions = CALCULATE([Total Transactions],DATEADD(Calandar[date],
-1,
MONTH
)
)

-------------
Last Month Revenue= CALCULATE([Total Revenue],DATEADD(Calandar[date],
-1,
MONTH
)
)
--------------
Last Month Profit=CALCULATE([Total profit],DATEADD(Calandar[date],
-1,
MONTH
)
)

-------------
Last Month Return =CALCULATE([Total profit],DATEADD(Calandar[date],
-1,
MONTH
)
)

-----------

o)
Create a new measure named "Revenue Target" based on a 5% lift over the previous month revenue, and format as $
Spot check: You should see a Revenue Target of $99,223 in March 1998

Revenue Target = [Last Month Revenue]+[Last Month Revenue]*0.05


PowerBi
PART 4: Building the Report

1) Rename the tab "Topline Performance" and insert the Maven Market logo

Inserted LOGO
and Page 1 to Topline Performance renamed.

Done on Power Bi

2) Insert a Matrix visual to show Total Transactions, Total Profit, Profit Margin, and Return Rate by Product_Brand (on rows)

Add conditional formatting to show data bars on the Total Transactions column, and color scales on Profit Margin (White to Green) and Return Rate (White to Red)
Add a visual level Top N filter to only show the top 30 product brands, then sort descending by Total Transactions




-------------------------

practising SQL advance from hacker

Select c.company_code,
c.founder,
count(l.lead_manager_code),
count(s.senior_manager_code),
count(m.senior_manager_code),
count(e.employee_code)
from company as c 
join lead_manager as l on l.company_code=c.company_code
join senior_manager_code as s on s.company_code=l.company_code
join Manager as s on m.company_code=s.company_code
join Employee as e on e.company_code=m.company_code

order by company_code asc;

-----------------
SELECT c.Company_Code, c.founder, count(Distinct e.Lead_Manager_Code), 
count(distinct e.Senior_Manager_Code), count(distinct e.Manager_Code), 
count(distinct e.employee_Code) FROM Company c 
JOIN Employee e ON c.Company_Code = e.Company_Code GROUP BY c.Company_Code, c.Founder ORDER BY c.COMpany_Code;

---------------------


Query the difference between the maximum and minimum populations in CITY.

select max(population) - min(population) from city;

----------------------

Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.




select ceil(avg(salary)
-avg(replace
(salary,0,'')
)
) 
from EMPLOYEES;

ceil is used in mysql to round to smallest integer value.




-----------------------------------
Q.
We define an employee's total earnings to be their monthly  worked, 
and the maximum total earnings to be the maximum total earnings 
for any employee in the Employee table. 
Write a query to find the maximum total earnings 
for all employees as well as the total number 
of employees who have maximum total earnings. 
Then print these values as  space-separated integers.


select top 1 max(salary*months)  as totalearning ,count(employee_id)  from  employee
group by salary*months
order by totalearning desc;



-------------------------------------------


Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of  decimal places.
The sum of all values in LONG_W rounded to a scale of  decimal places.

select format(round(sum(LAT_N),2),'####.##'),format(round(sum (LONG_W) ,2),'####.##') from station;



-------------------------------


Query the sum of Northern Latitudes (LAT_N) from STATION
 having values greater than  and less than . 
Truncate your answer to  decimal places.




select round(sum(LAT_N),4) from station
where LAT_N>38.7880 and LAT_N<137.2345;

----------------------------------

Query the greatest value of the Northern Latitudes (LAT_N) 
from STATION that is less than . Truncate your answer to  decimal places.

select round(max(LAT_N),4) from station
where LAT_N<137.2345;
--------------------------------------

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.



select top 1 format(round(LONG_W,4),".####") from station
where LAT_N<137.2345
order by LAT_N DESC;

select round(LONG_W,4) from station
where LAT_N<137.2345
order by LAT_N DESC
limit 1;


-----------------------------------------------------
Query the smallest Northern Latitude (LAT_N) from STATION that is greater than . Round your answer to  decimal places.


select round(Min(LAT_N),4) from station
where LAT_N>38.7780;


----------------------------------------------------------
Query the Western Longitude (LONG_W)where the 
smallest Northern Latitude (LAT_N) in STATION is greater than . 
Round your answer to  decimal places.

select round(LONG_W,4) from station
where LAT_N>38.7780
order by LAT_N 
limit 1;

--------------------------------------------------------------

19/09/2024

MANHATTAN DISTANCE: 
The distance between two points measured along axes at right angles. 
In a plane with p1 at (a, b) and p2 at (c, d), it is |a - c| + |b - d|. Lm distance.

In a plane with p1 at (x1, y1) and p2 at (x2, y2), it is |x1 - x2| + |y1 - y2|. Lm distance.


min lat_n=25.07352606
min long_w= 25.10565434
max lat_n=144.98906270
max long_w=164.87604770

select Format(Round(ABS(min(lat_n)- max(lat_n) + min(long_w)- max(long_w)),4),".####")   from station;

-----------------------------------------------------------------------------------------------------------

20/09/2024 

SQL - Basic Join 

1) 

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'. 

 Sol: 

 

SELECT SUM(ci.population) from city as ci 

JOIN country as co ON ci.CountryCode = co.Code 

where continent = 'Asia';  

  

2) 

  

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'. 

 Sol: 

 

SELECT City.Name  

FROM City, Country  

WHERE City.CountryCode = Country.Code AND Continent = 'Africa' ; 

  

3) 

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'. 

 Sol: 

 

  

SELECT ci.NAME from city as ci 

JOIN country as co ON ci.CountryCode = co.Code 

WHERE CONTINENT  = 'Africa'; 

  

  

4) Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.  

Sol:  

 

Select co.continent , Avg(ci.population) from city as ci 

JOIN country as co ON ci.CountryCode=co.Code 

group by co.continent; 

 

5) You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks. 

Sol: 

 

select case when g.grade<8 then null 

else s.name 

end as name, g.grade, s.marks 

from students as s 

JOIN grades as g ON s.marks between g.min_mark and g.max_mark 

order by g.grade desc,s.name asc; 

 

  

  

6) 

Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id. 

 

Input Format 

The following tables contain contest data: 

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.  

Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the score of the challenge for the difficulty level.  

Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge.  

Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission.  

Sol: 

 

SELECT h.hacker_id , h.name 

FROM submissions s 

join hackers h on h.hacker_id = s.hacker_id 

join challenges c on c.challenge_id = s.challenge_id 

join difficulty d on d.difficulty_level = c.difficulty_level 

where s.score = d.score 

and c.difficulty_level = d.difficulty_level 

group by h.hacker_id ,h.name 

having COUNT(s.submission_id) > 1 

order by COUNT(s.submission_id) desc, h.hacker_id asc; 

 

7) 

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates. 

Input Format 

The STATION table is described as follows: 

 

where LAT_N is the northern latitude and LONG_W is the western longitude. 

 

Sol: 

 

 

select distinct city from station  

where city like '[aeiou]%[aeiou]'; 

 

8) 

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates. 

Sol: 

 

select distinct city from station   

where left(city,1) not in ('a', 'e', 'i', 'o', 'u'); 

 

9) Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates. 

Sol: 

 

select distinct city from station  

 where right(city,1) not in ('a', 'e', 'i', 'o', 'u'); 

 

10) 

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates. 

Input Format 

The STATION table is described as follows: 

 

 

Sol: 

 

select distinct city from station   

where  

left(city,1) not in ('a', 'e', 'i', 'o', 'u') or 

right(city,1) not in ('a', 'e', 'i', 'o', 'u'); 

 

 

 

 



Consider  and  to be two points on a 2D plane where  are the respective minimum and maximum values of Northern Latitude (LAT_N) and  are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION.

Query the Euclidean Distance between points  and  and format your answer to display  decimal digits.


select Format(ROUND(SQRT(SQUARE(max(lat_n)-min(lat_n))
+SQUARE(max(long_w)-min(long_w))),4),".####") from station;

20/09/2024  

SQL -   Join 

1) 

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'. 

 Sol: 

 

SELECT SUM(ci.population) from city as ci 

JOIN country as co ON ci.CountryCode = co.Code 

where continent = 'Asia';  

  

2) 

  

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'. 

 Sol: 

 

SELECT City.Name  

FROM City, Country  

WHERE City.CountryCode = Country.Code AND Continent = 'Africa' ; 

  

3) 

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'. 

 Sol: 

 

  

SELECT ci.NAME from city as ci 

JOIN country as co ON ci.CountryCode = co.Code 

WHERE CONTINENT  = 'Africa'; 

  

  

4) Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.  

Sol:  

 

Select co.continent , Avg(ci.population) from city as ci 

JOIN country as co ON ci.CountryCode=co.Code 

group by co.continent; 

 

5) You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks. 

Sol: 

 

select case when g.grade<8 then null 

else s.name 

end as name, g.grade, s.marks 

from students as s 

JOIN grades as g ON s.marks between g.min_mark and g.max_mark 

order by g.grade desc,s.name asc; 

 

  

  

6) 

Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id. 

 

Input Format 

The following tables contain contest data: 

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.  

Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the score of the challenge for the difficulty level.  

Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge.  

Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission.  

Sol: 

 

SELECT h.hacker_id , h.name 

FROM submissions s 

join hackers h on h.hacker_id = s.hacker_id 

join challenges c on c.challenge_id = s.challenge_id 

join difficulty d on d.difficulty_level = c.difficulty_level 

where s.score = d.score 

and c.difficulty_level = d.difficulty_level 

group by h.hacker_id ,h.name 

having COUNT(s.submission_id) > 1 

order by COUNT(s.submission_id) desc, h.hacker_id asc; 

 

7) 

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates. 

Input Format 

The STATION table is described as follows: 

 

where LAT_N is the northern latitude and LONG_W is the western longitude. 

 

Sol: 

 

 

select distinct city from station  

where city like '[aeiou]%[aeiou]'; 

 

8) 

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates. 

Sol: 

 

select distinct city from station   

where left(city,1) not in ('a', 'e', 'i', 'o', 'u'); 

 

9) Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates. 

Sol: 

 

select distinct city from station  

 where right(city,1) not in ('a', 'e', 'i', 'o', 'u'); 

 

10) 

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates. 

Input Format 

The STATION table is described as follows: 

 

 

Sol: 

 

select distinct city from station   

where  

left(city,1) not in ('a', 'e', 'i', 'o', 'u') or 

right(city,1) not in ('a', 'e', 'i', 'o', 'u'); 

 

11) 

Julia asked her students to create some coding challenges. Write a query to print the hacker_id, name, and the total number of challenges created by each student. Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id. If more than one student created the same number of challenges and the count is less than the maximum number of challenges created, then exclude those students from the result. 

Input Format 

The following tables contain challenge data: 

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.  

Challenges: The challenge_id is the id of the challenge, and hacker_id is the id of the student who created the challenge.  

 

 

Sol:  

 

SELECT c.hacker_id, h.name, count(c.challenge_id) AS tnc  

--total no. challenges 

FROM Hackers AS h JOIN Challenges AS c ON h.hacker_id = c.hacker_id 

GROUP BY c.hacker_id, h.name  

HAVING tnc = (SELECT count(c1.challenge_id) FROM Challenges AS c1 GROUP BY c1.hacker_id  

              ORDER BY count(*) desc limit 1) or 

tnc NOT IN (SELECT count(c2.challenge_id) FROM Challenges AS c2 GROUP BY c2.hacker_id  

            HAVING c2.hacker_id <> c.hacker_id) 

ORDER BY tnc DESC, c.hacker_id; 

12) 

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates. 

Input Format 

The STATION table is described as follows: 

 

where LAT_N is the northern latitude and LONG_W is the western longitude 

 

Sol: 

SELECT DISTINCT CITY FROM STATION 

WHERE CITY NOT LIKE '[A,E,I,O,U]%' AND CITY NOT LIKE '%[A,E,I,O,U]'; 

 

 

13) 

Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID. 

Input Format 

The STUDENTS table is described as follows:  The Name column only contains uppercase (A-Z) and lowercase (a-z) letters 

 

 

 

Sol:  

SELECT name FROM STUDENTS 

WHERE MARKS>75 

ORDER BY RIGHT(NAME,3),ID; 

 

14) Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than  per month who have been employees for less than  months. Sort your result by ascending employee_id. 

Input Format 

The Employee table containing employee data for a company is described as follows: 

 

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is the their monthly salary 

 

 

 

Sol: 

SELECT NAME FROM EMPLOYEE 

WHERE SALARY>2000 AND MONTHS<10 

ORDER BY EMPLOYEE_ID; 

 

 

15) 

Generate the following two result sets: 

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S). 

Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format: 
 

There are a total of [occupation_count] [occupation]s. 
 

where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically. 

Note: There will be at least two entries in the table for each type of occupation. 

Input Format 

The OCCUPATIONS table is described as follows:  Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor 

 

 

 Sol: 

SELECT CONCAT(NAME, '(' , LEFT(OCCUPATION, 1), ')') 

FROM OCCUPATIONS 

UNION 

SELECT CONCAT('There are a total of ', ' ', COUNT(OCCUPATION), ' ', LOWER(OCCUPATION), 's.') 

FROM OCCUPATIONS 

GROUP BY OCCUPATION; 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

23/09/2024 

 

 

 

 

16) Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table: 

Equilateral: It's a triangle with  sides of equal length. 

Isosceles: It's a triangle with  sides of equal length. 

Scalene: It's a triangle with  sides of differing lengths. 

Not A Triangle: The given values of A, B, and C don't form a triangle. 

Input Format 

The TRIANGLES table is described as follows: 

 

Each row in the table denotes the lengths of each of a triangle's three sides 

 

 

 

 

Sol: 

select  

case  

when A+B <= C or B+C <= A or C+A <= B then  'Not A Triangle' 

when A=B AND B=C  then 'Equilateral' 

when A=B or B=C or C=A then 'Isosceles' 

when A<>B AND B<>C  then 'Scalene' 

end as Triangleforms 

from TRIANGLES; 

 

 

17) Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively. 

Note: Print NULL when there are no more names corresponding to an occupation. 

Input Format 

The OCCUPATIONS table is described as follows: 

 

Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor. 

 

 

 

Sol: 

 

 

 

18) Query a count of the number of cities in CITY having a Population larger than 1,00,000. 

Input Format 

The CITY table is described as follows:  

 

Sol: 

SELECT COUNT(*) FROM CITY 

WHERE POPULATION>100000; 

 

 

19) 

Query the total population of all cities in CITY where District is California. 

Input Format 

The CITY table is described as follows:  

 

 

Sol: 

 

 SELECT SUM(POPULATION) FROM CITY 

WHERE DISTRICT = 'California'; 

 

 

 

20) 

Query the average population of all cities in CITY where District is California. 

Input Format 

The CITY table is described as follows:  

 

 

 

Sol: 

SELECT AVG(POPULATION) FROM CITY 

WHERE District='California'; 

 

20)  

Query the average population for all cities in CITY, rounded down to the nearest integer. 

Input Format 

The CITY table is described as follows:  

 

  

  

  

  

  

Sol: 

SELECT ceiling(AVG(POPULATION)) FROM CITY ; 

 

21) You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too! 

The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of  from your result. 

Input Format 

The following tables contain contest data: 

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.  

Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge for which the submission belongs to, and score is the score of the submission.  

Sample 

  

 Sol: 
select h.hacker_id,h.name,sum(max_scores.max_score) as total_score 

from hackers h 

JOIN (select h.hacker_id,s.challenege_id,max(s.score) as max.score 

from submissions s 

      group by h.hacker_id,h.name ) as max_score 

      from submissions s 

ON h.hacker_id=max.hacker_id 

group by h.hacker_id,h.name    

having sum(s.max_score)>0 

order by toatal_score desc ,hacker_id ;-- failed attempt 

ANSWER: 

SELECT  

    h.hacker_id,  

    h.name,  

    SUM(max_scores.max_score) AS total_score 

FROM  

    hackers h 

JOIN  

    (SELECT  

        hacker_id,  

        challenge_id,  

        MAX(score) AS max_score 

     FROM  

        submissions 

     GROUP BY  

        hacker_id, challenge_id 

    ) max_scores 

ON  

    h.hacker_id = max_scores.hacker_id 

GROUP BY  

    h.hacker_id, h.name 

HAVING  

    SUM(max_scores.max_score) > 0  -- Exclude hackers with total score of 0 

ORDER BY  

    total_score DESC,  

    h.hacker_id ASC;
