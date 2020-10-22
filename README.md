## MOVIES

## CREATE DATABASE movies;
USE movies;
SHOW TABLES;
DESCRIBE moviestwo;
CREATE TABLE moviestwo(
MovieID INT AUTO_INCREMENT,
Title VARCHAR(30),
Runtime INT,
Genre VARCHAR(30),
IMDB_Score FLOAT(2.1),
Rating VARCHAR(6),
PRIMARY KEY (MovieID)
);
 -- SHOW TABLES;
INSERT INTO moviestwo VALUES (1, 'Howard the Duck', 110, 'Sci-Fi', 4.6, 'PG');
INSERT INTO moviestwo VALUES (2, 'Lavalantula', 83, 'Horror', 4.7, 'TV-14');
INSERT INTO moviestwo VALUES (3, 'Starship Troopers', 129, 'Sci-Fi', 7.2, 'PG-13');
INSERT INTO moviestwo VALUES (4, 'Waltz With Bashir', 90, 'Documentary', 8.0, 'R');
INSERT INTO moviestwo VALUES (5, 'Spaceballs', 96, 'Comedy', 7.1, 'PG');
INSERT INTO moviestwo VALUES (6, 'Monsters Inc.', 92, 'Animation', 8.1, 'G');
INSERT INTO moviestwo VALUES (7, 'Nemo', 136, 'Animation', 8.7, 'PG');
INSERT INTO moviestwo VALUES (8, 'Good Burger', 89,'Comedy', 7.3, 'PG'); 

SELECT * FROM moviestwo;
 
## Create a query to find all movies in the Sci-Fi genre.
SELECT * FROM moviestwo WHERE genre = 'Sci-Fi';

## Create a query to find all films that scored at least a 6.5 on IMDB
SELECT * FROM moviestwo WHERE IMDB_Score >= 6.5;

## For parents who have young kids, but who don't want to sit through long children's movies, create a query to find all of the movies rated G or PG that are less than 100 minutes long.
SELECT * FROM moviestwo WHERE Runtime < 100 AND Rating = 'PG' OR 'G';

-- SELECT * FROM moviestwo;

## Create a query to show the average runtimes of movies scoring below a 7.5 on imdb, grouped by their respective genres.
SELECT AVG(runtime) FROM moviestwo WHERE IMDB_Score < 7.5 GROUP BY genre;

## There's been a data entry mistake; Starship Troopers is actually rated R, not PG-13. Create a query that finds the movie by its title and changes its rating to R.
UPDATE moviestwo SET rating = 'R' WHERE title = 'Starship Troopers';

SELECT ALL * FROM moviestwo;

## Show the ID number and rating of all of the Horror and Documentary movies in the database. Do this in only one query.
SELECT MovieID, rating FROM moviestwo WHERE genre IN ('Horror', 'Documentary');

## This time let's find the average, maximum, and minimum IMDB score for movies of each rating. That last query isn't very informative for ratings that only have 1 entry. 
## Use a HAVING COUNT(*) > 1 clause to only show ratings with multiple movies showing.
SELECT rating, MAX(IMDB_Score), MIN(IMDB_Score), AVG(IMDB_Score) FROM moviestwo GROUP BY rating
HAVING COUNT(*) > 1;

## DOING 3 NEW QUERIES
-- PICK OUT ALL THE ANIMATION GENRE MOVIES:
SELECT * FROM moviestwo WHERE genre = 'Animation';

-- UPDATE BOTH ANIMATION MOVIES TO COMEDY
UPDATE moviestwo SET genre = 'Comedy' WHERE genre = 'Animation';
SELECT * FROM moviestwo; 

-- CHANGE THE NAME OF A MOVIE TO 'THIS IS YAS'
UPDATE moviestwo SET Title = 'THIS IS YAS' WHERE Title = 'Starship Troopers';
SELECT * FROM moviestwo;

-- ADD A NEW TABLE DATA
INSERT INTO moviestwo (MovieID, Title, Runtime, Genre, IMDB_Score, Rating) VALUES (9, 'Black Panther', 150, 'Action', 9.0, 'PG');
Describe moviestwo;
show tables; 
SELECT * FROM moviestwo;
