# SQL CRUD

# part 1: 
## Restaurant Table Strucutre 

The following lines were used to make the table: 

    create table restaurants (

     ID INTEGER PRIMARY KEY, 

        name TEXT,

        category TEXT, 

        priceTier TEXT, 

        neighbourhood TEXT, 

        openHour DATETIME, 

        closeHour DATETIME, 

        averageRating INTEGER, 

        kidFriendly BIT
)

data was imported in the following way: 
.mode csv

.headers on 

.import ./restaurants.csv restaurants 

# snapshot of data: 
| ID | name                           | category    | priceTier | neighbourhood      | openHour | closeHour | averageRating | kidFriendly |
|----|--------------------------------|-------------|-----------|--------------------|----------|-----------|---------------|-------------|
| 1  | COMPLEXITY Restuarant          | Lebanese    | $         | Crown Heights      | 09:00    | 21:00     | 0             | TRUE        |
| 2  | SERVICE-DESK Restuarant        | Peruvian    | $$$       | Throgs Neck        | 07:00    | 22:00     | 0             | FALSE       |
| 3  | DISCRETE Restuarant            | Slovak      | $$$       | Silver Lake        | 08:00    | 18:00     | 1             | TRUE        |
| 4  | PROCESS IMPROVEMENT Restuarant | Goan        | $         | Arden Heights      | 07:00    | 21:00     | 0             | TRUE        |
| 5  | FUNCTIONALITIES Restuarant     | Arab        | $$        | Ocean Parkway      | 13:00    | 17:00     | 0             | FALSE       |
| 6  | ENCRYPTION Restuarant          | Peruvian    | $$        | Mapleton           | 13:00    | 22:00     | 0             | TRUE        |
| 7  | BENCHMARK Restuarant           | Greek       | $         | Upper West Side    | 08:00    | 21:00     | 0             | TRUE        |
| 8  | ENHANCED Restuarant            | Serbian     | $$$       | Blissville         | 10:00    | 23:00     | 0             | FALSE       |
| 9  | INCREMENTAL Restuarant         | British     | $         | Financial District | 09:00    | 22:00     | 0             | TRUE        |
| 10 | INCREMENTAL Restuarant         | American    | $$$       | Melrose            | 10:00    | 21:00     | 0             | FALSE       |
| 11 | CONTEXTUALLY-BASED Restuarant  | South       | $         | Williamsbridge     | 12:00    | 21:00     | 0             | TRUE        |
| 12 | INFRASTRUCTURE Restuarant      | British     | $         | Stapleton          | 07:00    | 15:00     | 0             | FALSE       |
| 13 | MULTI-STATE Restuarant         | Mexican     | $$$       | Bensonhurst        | 11:00    | 21:00     | 0             | TRUE        |
| 14 | PRICING STRUCTURE Restuarant   | Thai        | $$$       | Queensbridge       | 11:00    | 00:00     | 0             | FALSE       |
| 15 | DEDICATED Restuarant           | American    | $         | Astoria Heights    | 09:00    | 22:00     | 0             | FALSE       |
| 16 | ZERO TOLERANCE Restuarant      | Sri         | $$        | Harding Park       | 08:00    | 17:00     | 0             | TRUE        |
| 17 | LOGISTICAL Restuarant          | Crimean     | $         | Remsen Village     | 07:00    | 20:00     | 0             | TRUE        |
| 18 | RADICAL Restuarant             | Mennonite   | $$        | Hollis             | 07:00    | 22:00     | 0             | TRUE        |
| 19 | BENCHMARK Restuarant           | Slovenian   | $$$       | Crown Heights      | 09:00    | 23:00     | 0             | TRUE        |
| 20 | PERSEVERING Restuarant         | Singaporean | $$$       | Bedford Park       | 07:00    | 18:00     | 0             | FALSE       |

## queries done : 

Query 1: Find all cheap restaurants in a particular neighborhood (pick any neighborhood as an example)

    Q1: select name from restaurants where neighbourhood = "Coney Island" and priceTier = “$”;

Query 2: Find all restaurants in a particular genre (pick any genre as an example) with 3 stars or more, ordered by the number of stars in descending order.

    Q2: select name from restaurants where category = "Bangladeshi" and averageRating = 1 order by averageRating desc;

Query 3: Find all restaurants that are open now

    Q3: select * from restaurants where cast(strftime('%H', openHour) as INT)< strftime('%H', 'now') and cast(strftime('%H', closeHour) as INT) > strftime('%H', ‘now');

Query 4: Leave a review for a restaurant (pick any restaurant as an example).

    Q4: alter table restaurants add reviews TEXT;
    update restaurants SET reviews = "good place for coffee" where ID = 88;

Query 5: Delete all restaurants that are not good for kids.

    Q5: delete from restaurants where kidFriendly = FALSE; 

Query 6: Find the number of restaurants in each NYC neighborhood.

    Q6: select neighbourhood, count(name) from restaurants group by neighbourhood;

# part 2 social Media 

## users Table Strucutre 

The following lines were used to make the table: 
    create table:

        create table users (
        ...> id INTEGER PRIMARY KEY,

         ...> email TEXT,

        ...> password TEXT,

        ...> handle TEXT

        ...> );

## posts Table Strucutre 

The following lines were used to make the table: 
create table:

    sqlite> create table posts (

        ...> id INTEGER PRIMARY KEY,

        ...> text TEXT,

         ...> from_users_id INTEGER,

         ...> to_users_id INTEGER,

        ...> visibility INTEGER,

        ...> post_time DATETIME

        ...> );

   ## how data from users is supposed to be imported 

   .mode csv 

   .headers on 

   .import ./users.csv users

   ## how data from posts is supposed to be imported 

   .mode csv 

   .headers on 

   .import ./posts.csv posts 

   ## Queries should be performed in the following manner: 

   insert into users (id, email, password, handle) 
   values (1001, "alabla@hotmail.com", "EEEEEEEE1", "alalala"); 


