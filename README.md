# SQL-Project-Customer-to-Customer-C2C-Ecommerce-Platform-Analysis
# 🎯 Objective
This project demonstrates my SQL skills through analysis on a C2C ecommerce platform, where users act as buyers or sellers. By exploring a large users database, we derive business insights, user behavior, and demographic patterns for platform improvement.
# 📝 Project Structure
* Schema Creation: Create the ecommerce schema.
* Data Import: Load the users_data.csv file into MySQL.
* Data Exploration: View table structure and sample data.
* Business Analysis: Answer 18 core business questions using SQL.
# Tasks
1. Create new schema as ecommerce
```MySql
CREATE SCHEMA ecommerce;
```
2. Run SQL command to see the structure of table
```MySql
USE ecommerce;
DESC users_data;
```
3. Run SQL command to select first 100 rows of the database
```MySql
SELECT * FROM users_data LIMIT 100;
```
4. How many distinct values exist in table for field country and language
```MySql
SELECT COUNT(DISTINCT country) No_of_country,
COUNT(DISTINCT language) No_of_language FROM users_data;
```
5. Check whether male users are having maximum followers or female users.
```MySql
SELECT gender, SUM(socialNbFollowers) Sum_of_followers
FROM users_data GROUP BY gender;
```
6. Calculate the total users those\
a. Uses Profile Picture in their Profile\
b. Uses Application for Ecommerce platform\
c. Uses Android app\
d. Uses ios app\
```MySql
SELECT COUNT(hasProfilePicture) Users_with_profilePicture FROM users_data
WHERE hasProfilePicture = 'TRUE';
SELECT COUNT(hasAnyApp) Users_with_Application FROM users_data WHERE hasAnyApp = 'TRUE' ;
SELECT COUNT(hasAndroidApp) Users_with_Android FROM users_data WHERE hasAndroidApp = 'TRUE' ;
SELECT COUNT(hasIosApp) Users_with_Ios FROM users_data WHERE hasIosApp = 'TRUE' ;
```
7. Calculate the total number of buyers for each country and sort the result in descending order of total number of buyers. (Hint: consider only those users having at least 1 product bought.)
```MySql
SELECT DISTINCT(country),COUNT(productsBought) total_buyers FROM users_data 
WHERE productsBought != 0 GROUP BY country ORDER BY COUNT(productsBought) DESC;
```
8. Calculate the total number of sellers for each country and sort the result in ascending order of total number of sellers. (Hint: consider only those users having at least 1 product sold.)
```MySql
SELECT DISTINCT(country),COUNT(productsSold) total_sellers FROM users_data 
WHERE productsSold != 0 GROUP BY country ORDER BY COUNT(productsSold) ASC;
```
9. Display name of top 10 countries having maximum products pass rate.
```MySql
SELECT DISTINCT country,MAX(productsPassRate) Max_productsPassRate FROM users_data 
GROUP BY country ORDER BY MAX(productsPassRate) DESC LIMIT 10;
```
10. Calculate the number of users on an ecommerce platform for different language choices.
```MySql
SELECT language, COUNT(language) no_of_users FROM users_data GROUP BY language;
```
11. Check the choice of female users about putting the product in a wishlist or to like socially on an ecommerce platform.
```MySql
SELECT COUNT(productsWished) Choices FROM users_data WHERE gender = 'F' AND productsWished > 0 UNION
SELECT COUNT(socialProductsLiked) Choices FROM users_data WHERE gender = 'F' AND socialProductsLiked > 0;
```
12. Check the choice of male users about being seller or buyer.
```MySql
SELECT COUNT(productsBought) Choices FROM users_data WHERE gender = 'M' AND productsBought > 0 UNION 
SELECT COUNT(productsSold) Choices FROM users_data WHERE gender = 'M' AND productsSold > 0 ;
```
13. Which country is having maximum number of buyers?
```MySql
SELECT country ,COUNT(productsBought) Max_no_of_buyers FROM users_data 
GROUP BY country ORDER BY COUNT(productsBought) DESC LIMIT 1;
```
14. List the name of 10 countries having zero number of sellers.
```MySql
SELECT country FROM users_data WHERE productsSold = 0 
GROUP BY country  LIMIT 10; 
```
15. Display record of top 110 users who have used ecommerce platform recently.
```MySql
SELECT * FROM users_data ORDER BY daysSinceLastLogin LIMIT 110;
```
16. Calculate the number of female users those who have not logged in since last 100 days.
```MySql
SELECT COUNT(gender) Female_user FROM users_Data WHERE daysSinceLastLogin > 100 AND gender = 'F';
```
17. Display the number of female users of each country at ecommerce platform.
```MySql
SELECT country,COUNT(gender) Female_user FROM users_data 
WHERE gender = 'F' AND hasAnyApp = 'TRUE' GROUP BY country;
```
18. Display the number of male users of each country at ecommerce platform.
```MySql
SELECT country,COUNT(gender) Male_user FROM users_data 
WHERE gender = 'M' AND hasAnyApp = 'TRUE' GROUP BY country;
```
19. Calculate the average number of products sold and bought on ecommerce platform by male users for each country.
```MySql
SELECT country,AVG(productsSold) Average_sold ,AVG(productsBought) Average_bought 
FROM users_data WHERE gender = 'M'GROUP BY country;
```
# 📖 Conclusion
This project showcases my proficiency in writing and executing advanced SQL queries while addressing practical business challenges for a C2C ecommerce platform. It reflects a systematic approach to problem-solving, strong data handling and manipulation skills, and the capability to uncover actionable insights that can drive platform growth and user engagement.

































































































