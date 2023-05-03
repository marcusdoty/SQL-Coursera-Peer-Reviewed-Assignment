# SQL-Coursera-Peer-Reviewed-Assignment
03-05-2023

Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

This is a 2-part assignment. In the first part, you are asked a series of questions that 
will help you profile and understand the data just like a data scientist would. For this 
first part of the assignment, you will be assessed both on the correctness of your 
findings, as well as the code you used to arrive at your answer. You will be graded on 
how easy your code is to read, so remember to use proper formatting and comments where 
necessary.

In the second part of the assignment, you are asked to come up with your own inferences 
and analysis of the data for a particular research question you want to answer. You will be 
required to prepare the dataset for the analysis you choose to do. As with the first part, 
you will be graded, in part, on how easy your code is to read, so use proper formatting 
and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions 
you are being asked, and your job will be to transfer your answers and SQL coding where
indicated into this worksheet so that your peers can review your work. You should be able 
to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) 
to copy and paste your answers. If you are going to use Word or some other page layout
application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact
for you reviewer.

Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:
	
SELECT Count(*) AS Total_Number
From Table

i. Attribute table = 10000
ii. Business table = 10000
iii. Category table = 10000
iv. Checkin table = 10000
v. elite_years table = 10000
vi. friend table = 10000
vii. hours table = 10000
viii. photo table = 10000
ix. review table = 10000
x. tip table = 10000
xi. user table = 10000

2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

SELECT Count(Distinct (key)) AS Total_Key
From Table

i. Business = 10000 (id)
ii. Hours = 1562 (business_id)
iii. Category = 2643 (business_id)
iv. Attribute = 1115 (business_id)
v. Review = 1000 (id), 8090 (business_id), 9581 (user_id)
vi. Checkin = 493 (business_id)
vii. Photo = 10000 (id), 6493 (business_id)
viii. Tip = 537 (user_id), 3979 (business_id)
ix. User = 10000 (id)
x. Friend = 11 (user_id)
xi. Elite_years = 2780 (user_id)

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	
3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

Answer: NO
	
SQL code used to arrive at answer:
	
SELECT count(*)
FROM user
WHERE id is NULL OR	
name IS NULL OR
review_count IS NULL OR
yelping_since IS NULL OR
useful IS NULL OR
funny IS NULL OR
cool IS NULL OR
fans IS NULL OR
average_stars IS NULL OR
compliment_hot IS NULL OR
compliment_more IS NULL OR
compliment_profile IS NULL OR
compliment_cute IS NULL OR
compliment_list IS NULL OR
compliment_note IS NULL OR
compliment_plain IS NULL OR
compliment_cool IS NULL OR
compliment_funny IS NULL OR
compliment_writer IS NULL OR
compliment_photos IS NULL 

4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

i. Table: Review, Column: Stars
	
min: 1		max: 5		avg: 3.7082
	
SELECT min(stars), max(stars), avg(stars) FROM review
	
ii. Table: Business, Column: Stars
	
min: 1.0		max: 5.0		avg: 3.6549
		
SELECT min(stars), max(stars), avg(stars) FROM business

iii. Table: Tip, Column: Likes
	
min: 0		max: 2		avg: 0.0144
		
SELECT min(likes), max(likes), avg(likes) FROM tip

iv. Table: Checkin, Column: Count
	
min: 1		max: 53		avg: 1.9414
		
SELECT min(count), max(count), avg(count) FROM checkin
	
v. Table: User, Column: Review_count
	
min: 0		max: 2000		avg: 24.2995
		
SELECT min(review_count), max(review_count), avg(review_count) FROM user

5. List the cities with the most reviews in descending order:

SQL code used to arrive at answer:
	
SELECT city, sum(review_count) as Reviews
FROM business
GROUP BY city
ORDER BY Reviews DESC
	
Copy and Paste the Result Below:
	
+-----------------+-------------------+
| city            | sum(review_count) |
+-----------------+-------------------+
| Las Vegas       |             82854 |
| Phoenix         |             34503 |
| Toronto         |             24113 |
| Scottsdale      |             20614 |
| Charlotte       |             12523 |
| Henderson       |             10871 |
| Tempe           |             10504 |
| Pittsburgh      |              9798 |
| Montreal        |              9448 |
| Chandler        |              8112 |
| Mesa            |              6875 |
| Gilbert         |              6380 |
| Cleveland       |              5593 |
| Madison         |              5265 |
| Glendale        |              4406 |
| Mississauga     |              3814 |
| Edinburgh       |              2792 |
| Peoria          |              2624 |
| North Las Vegas |              2438 |
| Markham         |              2352 |
| Champaign       |              2029 |
| Stuttgart       |              1849 |
| Surprise        |              1520 |
| Lakewood        |              1465 |
| Goodyear        |              1155 |
+-----------------+-------------------+
	
6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

SELECT stars AS star_rating, count(stars) AS count
FROM business
WHERE city = 'Avon'
GROUP BY stars
ORDER BY stars

Copy and Paste the Resulting Table Below (2 columns as star rating and count):

+-------------+-------+
| Star Rating | Count |
+-------------+-------+
|         1.5 |     1 |
|         2.5 |     2 |
|         3.5 |     3 |
|         4.0 |     2 |
|         4.5 |     1 |
|         5.0 |     1 |
+-------------+-------+

ii. Beachwood

SQL code used to arrive at answer:

SELECT stars AS star_rating, count(stars) AS count
FROM business
WHERE city = 'Beachwood'
GROUP BY stars
ORDER BY stars

Copy and Paste the Resulting Table Below (2 columns â€“ star rating and count):
		
+-------------+-------+
| Star Rating | Count |
+-------------+-------+
|         2.0 |     1 |
|         2.5 |     1 |
|         3.0 |     2 |
|         3.5 |     2 |
|         4.0 |     1 |
|         4.5 |     2 |
|         5.0 |     5 |
+-------------+-------+

7. Find the top 3 users based on their total number of reviews:
		
SQL code used to arrive at answer:
	
SELECT name, review_count
FROM user
ORDER BY review_count DESC
limit 3;

Copy and Paste the Result Below:

+--------+--------------+
| name   | review_count |
+--------+--------------+
| Gerald |         2000 |
| Sara   |         1629 |
| Yuri   |         1339 |
+--------+--------------+	

8. Does posing more reviews correlate with more fans?

Please explain your findings and interpretation of the results:
	
Given the table shown, we can see that Gerald who has the most reviews at 2000 has only 253 fans, whilst Mimi has 968 reviews and a significantly larger number of fans at 497 or Harald who has almost half the reviews at 1153 and 311 fans (more than Gerald). We can thus conclude that posing more reviews does not correlate with more fans and organising the review count in descending order has no significant impact on results.
	
9. Are there more reviews with the word "love" or with the word "hate" in them?

Answer: Yes, we there are more results for the word "love". There are 1780 instances of 'love' in reviews whilst there are 232 reviews for hate.
	
SQL code used to arrive at answer:

SELECT count(*)
FROM review 
WHERE text like '%love%'

= 1780

SELECT count(*)
FROM review
WHERE text like '%hate%'

= 232
	
10. Find the top 10 users with the most fans:

SQL code used to arrive at answer:
	
SELECT name, fans
FROM user
ORDER BY fans DESC
limit 10
	
Copy and Paste the Result Below:

+-----------+------+
| name      | fans |
+-----------+------+
| Amy       |  503 |
| Mimi      |  497 |
| Harald    |  311 |
| Gerald    |  253 |
| Christine |  173 |
| Lisa      |  159 |
| Cat       |  377 |  
| William   |  126 |
| Fran      |  124 |
| Lissa     |  120 |
+-----------+------+

Part 2: Preferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.
	
City: Toronto
Category: Nightlife

i. Do the two groups you chose to analyze have a different distribution of hours?

SELECT 
  CASE 
    WHEN stars >= 4.0 THEN '4-5 stars'
    WHEN stars >= 2.0 THEN '2-3 stars'
    ELSE 'below 2' 
  END AS 'STARS',
  COUNT(DISTINCT business.id) AS id_count,
  COUNT(hours) AS open_days_total,
  COUNT(hours)*1.0 / COUNT(DISTINCT business.id) AS open_days_avg
FROM 
  (
    (business 
      INNER JOIN hours ON business.id = hours.business_id) 
      INNER JOIN category ON business.id = category.business_id
  )
WHERE 
  city = 'Toronto' 
  AND category.category ='Nightlife'
GROUP BY STARS

The output from the table shows us no different distribution of hours as both the total open days and average open days is the exact same. Both have 13 open days total and both are open an average of 6.5.

+-----------+----------+-----------------+---------------+
| STARS     | id_count | open_days_total | open_days_avg |
+-----------+----------+-----------------+---------------+
| 2-3 stars |        2 |              13 |           6.5 |
| 4-5 stars |        2 |              13 |           6.5 |
+-----------+----------+-----------------+---------------+ 

ii. Do the two groups you chose to analyze have a different number of reviews?

SELECT 
CASE
WHEN stars >= 4.0 THEN '4-5 stars'
WHEN stars >= 2.0 THEN '2-3 stars'
ELSE 'below 2'
END AS 'STARS',
COUNT(DISTINCT business.id) AS id_count,
SUM(review_count) AS review_count_total,
SUM(review_count)*1.0/COUNT(DISTINCT business_id) AS review_count_avg
FROM
(
    (business
    INNER JOIN category ON business.id = category.business_id)
)
WHERE
city = 'Toronto'
AND category.category = 'Nightlife'
GROUP BY STARS
         
The raw count of review counts amongst nightlife joints in Toronto is relatively indifferent. Nightlife venues that are rated 2-3 stars have a review count of 45 and an average review count of 22.5. On the other hand, nightlife venues with 4-5 stars have 41 total review counts and an avgerage of 20.5. Although there are more reviews for those rated 2-3 stars, it is relatively close.

+-----------+----------+--------------------+------------------+
| STARS     | id_count | review_count_total | review_count_avg |
+-----------+----------+--------------------+------------------+
| 2-3 stars |        2 |                 45 |             22.5 |
| 4-5 stars |        2 |                 41 |             20.5 |
+-----------+----------+--------------------+------------------+

iii. Are you able to infer anything from the location data provided between these two groups? Explain.

Of all the cities in the Yelp database, Toronto had the 3rd most sum of review counts behind Las Vegas, Nevada and Phoenix, Arizona. Toronto being the largest city in Canada has a range of affluential nightlife and food options. We can see from the table that the venues with 2-3 stars are located in the Entertainment District and the Greektown neighbourhoods. At the same time, the venues with 4-5 stars are in the High Park and Wallace Emerson neighbourhoods.

SQL code used for analysis:

SELECT CASE WHEN stars >= 4.0 THEN '4-5 stars'
            WHEN stars >= 2.0 THEN '2-3 stars'
            ELSE 'below 2' END AS 'STARS',
       business.neighborhood,
       business.address,
       business.postal_code
FROM business INNER JOIN category ON business.id = category.business_id
WHERE city = 'Toronto' AND category.category ='Nightlife'
ORDER BY STARS

+-----------+------------------------+---------------------+-------------+
| STARS     | neighborhood           | address             | postal_code |
+-----------+------------------------+---------------------+-------------+
| 2-3 stars | Entertainment District | 19 Charlotte Street | M5V 2H5     |
| 2-3 stars | Greektown              | 535 Danforth Ave    | M4K 1P7     |
| 4-5 stars | High Park              | 1669 Bloor Street W | M6P 1A6     |
| 4-5 stars | Wallace Emerson        | 247 Wallace Avenue  | M6H 1V5     |
+-----------+------------------------+---------------------+-------------+
		
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:

The first difference I notice is that there are a great disparity in the total overall number of reviews left for locations that are open vs those that are closed. Open places have 269,300 review counts in total vs 35,261 for those that are closed.       
         
ii. Difference 2:
         
Furthermore, we can see that the joints that remain open benefit in terms of the reviews they receive. For example, we can see that those that are closed have an average amount of stars of 3.52 vs 3.679 for the places that are open. Telling us that it is beneficial for these places to stay open. 
         
SQL code used for analysis:

Select Count(DISTINCT(id)), avg(review_count), sum(review_count), avg(stars)
, is_open
FROM business
GROUP BY is_open
	
+---------------------+-------------------+-------------------+---------------+---------+
| Count(DISTINCT(id)) | avg(review_count) | sum(review_count) |    avg(stars) | is_open |
+---------------------+-------------------+-------------------+---------------+---------+
|                1520 |     23.1980263158 |             35261 | 3.52039473684 |       0 |
|                8480 |     31.7570754717 |            269300 | 3.67900943396 |       1 |
+---------------------+-------------------+-------------------+---------------+---------+

3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:

For my analysis, my intention is to access the dataset related to the bars across the Pacific South-West region of the US. Working for a company that both manufactures and sells craft beer, we are keen to launch our latest range of craft beer in this market. This said, our intentions are to find and partner with a bar in the region to help promote and distribute our latest product. Finally, the ultimate goal of my analysis is to find the bar with the best reviews in said area to distribute my beer.

Through studying the level of how saturated different business opportunities are as well as how consumers perceive different businesses, I am confident that my client will be put in the best position to open a successful business in Toronto.       
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:

In order to conduct my analysis, extrapolating the correct data is critical to the overall success of my findings. In saying this, the data I am mostly looking to include will relate to how consumers perceive the different bars through the star ratings. In doing this, we will be able to make an informed judgement on the overall quality of the bars via the judgement of consumers. This evaluation is supported by the total number of reviews which proves to us that there is little bias in the rating given to us. By assessing the consumer perception of these different bars, we will develop an idea of the attitudes and opinions of different types of businesses, giving us a very reliable indicator on which type of business will be the most successful to market our beer. The data we derive from this analysis will be vital to marketing the product in the best way from the standpoint of ensuring adequate marketing information is processed correctly.                           
                  
iii. Output of your finished dataset:
         
+----------------------------+---------------------------------+------------+-------+-------------+--------------+----------+-----------+-------------+
| name                       | address                         | city       | state | postal_code | review_count | category | avg_stars | num_reviews |
+----------------------------+---------------------------------+------------+-------+-------------+--------------+----------+-----------+-------------+
| Chula Seafood              | 8015 E Roosevelt St             | Scottsdale | AZ    | 85257       |          106 | Bars     |       5.0 |         316 |
| La Maison de Maggie        | 3455 S Durango Dr, Ste 112      | Las Vegas  | NV    | 89117       |          260 | Bars     |       5.0 |         316 |
| Las Vegas Collision Center | 4705 W Post Rd                  | Las Vegas  | NV    | 89118       |          103 | Bars     |       5.0 |         316 |
| LasikPlus Vision Center    | 16427 N Scottsdale Rd, Ste 105  | Scottsdale | AZ    | 85254       |          115 | Bars     |       5.0 |         316 |
| Lori's Grooming            | 7000 E Shea Blvd, Ste 1360      | Scottsdale | AZ    | 85254       |          114 | Bars     |       5.0 |         316 |
| LunchboxWax Scottsdale     | 6590 N Scottsdale Blvd, Ste 130 | Scottsdale | AZ    | 85253       |          112 | Bars     |       5.0 |         316 |
| Master Lock & Security     |                                 | Las Vegas  | NV    | 89123       |          153 | Bars     |       5.0 |         316 |
| SPEEDVEGAS                 | 14200 S Las Vegas Blvd          | Las Vegas  | NV    | 89054       |          125 | Bars     |       5.0 |         316 |
| Tidy Casa                  | 600 N 4th St, Ste 866           | Phoenix    | AZ    | 85004       |          149 | Bars     |       5.0 |         316 |
| UpTown Barbershop          | 1515 E Bethany Home Rd, Ste 170 | Phoenix    | AZ    | 85014       |          176 | Bars     |       5.0 |         316 |
+----------------------------+---------------------------------+------------+-------+-------------+--------------+----------+-----------+-------------+
         
iv. Provide the SQL code you used to create your final dataset:

SELECT DISTINCT b.name, b.address, b.city, b.state, b.postal_code, b.stars, b.review_count, c.category,
    AVG(b.stars) as avg_stars,
    COUNT(b.review_count) as num_reviews
FROM business b
JOIN category c ON business_id = c.business_id
WHERE c.category LIKE '%Bars%' AND b.stars >= 4 AND
    b.review_count >= 100 AND b.city in ('Las Vegas', 'Phoenix', 'Glendale', 'Scottsdale', 'Chandler')
GROUP BY b.name, b.address, b.city, b.state, b.postal_code
ORDER BY avg_stars DESC, num_reviews DESC
LIMIT 10;
