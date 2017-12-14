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

