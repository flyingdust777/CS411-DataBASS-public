# Travelations - CS411 Project
This project is a social traveling Android app where users challenge themselves to travel to as many cities as possible.  We want to provide a social game that rewards people for traveling the world.

As users travel to multiple cities, the database will collect information about the users that have visited each city.  Then the app will allow users to monitor the cities they have visited as well as the cities their friends have visited.

## Screenshots
<p align="center">
  <img src="https://raw.githubusercontent.com/flyingdust777/CS411-DataBASS-public/master/Screenshot_20171207-125122.jpg" width="250"/>
  <img src="https://raw.githubusercontent.com/flyingdust777/CS411-DataBASS-public/master/Screenshot_20171207-125127.jpg" width="250"/>
  <img src="https://raw.githubusercontent.com/flyingdust777/CS411-DataBASS-public/master/Screenshot_20171207-125055.jpg" width="250"/>
</p>

## Video
<p align="center">
  <a href="https://www.youtube.com/watch?v=P-jm9EzAeh8"><img src="https://img.youtube.com/vi/P-jm9EzAeh8/0.jpg" alt="Travelations Demo" </a>
</p>

## Description
This project is a traveling social media Android app where users challenge themselves to travel to as many cities as possible.  We want to provide a social game that rewards people for traveling the world. As users travel to multiple cities, the database will collect information about the users that have visited each city.  Then the app will allow users to monitor the cities they have visited as well as the cities their friends have visited.  When they arrive at a city, a new record will be inserted into a table in the database with the user’s username, the city, and the time of arrival.

## Usefulness
We think this app would be useful because it would give people an incentive to travel to many locations of the world, challenge themselves, compete with their friends, and have fun all the time. We are targeting the average individual, especially the people that like to travel a lot. It would also be useful for connecting people together inside of a social network, and eventually, the app could be used to store photos and reviews of different cities and places, so users could quickly see what exciting places are around them.

## Dataset
The dataset we will be using is the [World Cities Dataset](https://www.kaggle.com/max-mind/world-cities-database) which contains over 1,000,000 rows. The dataset contains fields such as country code, ASCII city name, city name, region, population, latitude, and longitude. More details about this dateset can be found [here](https://www.maxmind.com/en/free-world-cities-database).

## Functionality
We will have a table in the database that contains what users visit certain locations and when. In addition, there will be another table that contains follower followee relationships between users.

## Basic Functions
Insertion functions will be used in several places. Every time a user visits a location, the app will insert a new record of the username, the location, the time of visit, etc. This will be performed by the server after it receives a request from the GPS when the user gets near the location. Insert functions will also happen when a new user is created, or when a user follows another user.

Deletion functions will be used in several places as well. If a user resets their statistics to start the game over, all their raw data records are removed from the database. If a user stops following someone, the corresponding relationship will be removed from the database.

Select functions will be used in different places too. After raw data has been accumulated, users will be able to search/query it to generate a summary page of statistics displayed on his or her profile. This information will answer questions like the following:
- What is the total number of miles traveled among all users?
- Which markers have been visited the most?
- Which user has visited the most markers?
- What is the total number of cities a user has visited?

## Advanced Functions
One advanced function we might use is a KD Tree or R-Tree that will be used to search and identify nearby cities by latitude and longitude. Since the Earth is round, we would have to be careful of cities that are on the edge of the Eastern and Western hemispheres. The purpose of this function is to efficiently identify cities near users. However, we may end up using an advanced SQL query that could locate the closest city based off polar coordinate conversions.

Another advanced function we plan on creating is an interactive map that plots the cities and the paths that users have traveled. We could show the most traveled or walked paths on a map and label the most visited cities and summary statistics about each of them. This would be a cool function because it would let users learn interesting facts about their travels, their friends’ travels, and the overall user group for the app.

## Advanced Techniques
The current list of advanced techniques is contingent based off what has been taught in lecture so far.
- Indexing
- Transactions
- Prepared Statements
- Compound Statements
- Parallel query execution
- Stored procedure

## ER Diagram
<p align="center">
  <img src="https://raw.githubusercontent.com/flyingdust777/CS411-DataBASS-public/master/er.png" width="500"/>
</p>

## ER Description
The people that use the app (the Users entity set) will travel to cities (the Cities entity set) and check-in to them when they arrive (the Check-In relationship).  Users can also follow other users (the Follow relationship) to keep track of other users’ stats and compare their own stats against the stats of other users.  There are also achievements (the Achievements entity set) that users can achieve (the Achieve relationship).

For their attributes, users have a unique username, an email address, an encrypted password (a password hash), the date they created their account for the app (a join date), a number of points they achieved from achievements (a score), an access token to verify the validity of their login session, the number of times they have checked into cities (a checkin count), and a name they can display to other users (a display name).  Each city has a unique ID (City ID) that we create, a population size, a name, a country code, a latitude, a longitude, and a region.  All these attributes except for the unique ID come from the World Cities Dataset and will allow us to understand the locations and names of the cities.  Every achievement has a unique ID, a title, a description of the requirement to achieve it, and a point value associated with it.  This points attribute represents the number by which a user's score will increase when this achievement is acquired.

When a user checks-in at a city, a record containing his/her username, the ID representing the city, and the timestamp of the check-in is inserted into the Check-In relation in the database.  Since a user can check-in at multiple cities and a city can be checked-in at by multiple users, we believe the Check-In relationship should have many-many multiplicity constraint.  Furthermore, because a user can check in at a city multiple times to record all his/her visits to that city, we believe that the timestamp of the check-in needs to serve as an attribute of the key for each tuple in the Check-In relation.

Since a user can follow multiple users and a user can be followed by multiple users, we believe the Follow relationship should have many-many multiplicity constraint.

When a user acquires an achievement, the user's score attribute in the User relation increases by the number of points associated with that achievement in the Achievement relation.  A record containing his/her username and the ID representing the achievement is also inserted into the Achieve relation in the database.  Since a user can acquire many achievements and an achievement can be acquired by many users,  we believe the Acquire relationship should have many-many multiplicity constraint.
