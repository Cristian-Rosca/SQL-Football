# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE season = 2017;

```

2) Find all the matches featuring Barcelona.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE hometeam = 'Barcelona' OR awayteam = 'Barcelona';

```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here -->
SELECT name FROM divisions WHERE country = 'Scotland';

```

4) Find the division code for the Bundesliga. Use that code to find out how many matches Freiburg have played in the Bundesliga since the data started being collected.

```sql
<!-- Copy solution here -->
SELECT code FROM divisions WHERE name = 'Bundesliga'

(Show all matches from D1 where Freiburg played)
SELECT * FROM matches WHERE matches.division_code = 'D1' AND (hometeam = 'Freiburg' OR awayteam = 'Freiburg');

SELECT COUNT (*) FROM matches WHERE matches.division_code = 'D1' AND (hometeam = 'Freiburg' OR awayteam = 'Freiburg');
```

5) Find the unique names of the teams which include the word "City" in their name (as entered in the database)

```sql
<!-- Copy solution here -->
(Only examining hometeam - struggling to combine search across both hometeam and awayteam)
SELECT COUNT (DISTINCT hometeam) FROM matches WHERE LOWER(hometeam) LIKE LOWER ('%City%'); 

(The ids of all matches where hometeam or awayteam has 'City')
SELECT COUNT (DISTINCT id) FROM matches WHERE LOWER(hometeam) OR WHERE LOWER(awayteam) LIKE LOWER ('%City%');



```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here -->
SELECT code FROM divisions WHERE country = 'France';

(Gets the number of distinct hometeams in F1 from dataset)
SELECT COUNT (DISTINCT hometeam) FROM matches WHERE matches.division_code = 'F1';

(Gets the number of distinct hometeams in F1 and F2from dataset)
SELECT COUNT (DISTINCT hometeam) FROM matches WHERE matches.division_code = 'F1' OR matches.division_code = 'F2';

```

7) Have Huddersfield played Swansea in the period covered?

```sql
<!-- Copy solution here -->
(Only examines one possibility)
SELECT * FROM matches WHERE hometeam = 'Huddersfield' AND awayteam = 'Swansea';

(Examines both possibilities)
SELECT * FROM matches WHERE hometeam = 'Huddersfield' AND awayteam = 'Swansea' OR (hometeam = 'Swansea' AND awayteam = 'Huddersfield');

```

8) How many draws were there in the Eredivisie between 2010 and 2015?

```sql
<!-- Copy solution here -->
(Getting matches.division_code = 'N1')
SELECT code FROM divisions WHERE name = 'Eredivisie';

(All data where division is N1 and result is draw)
SELECT * FROM matches WHERE division_code = 'N1' AND ftr = 'D';

(All data where division is N1 and result is draw between 2010 and 2015)
SELECT * FROM matches WHERE division_code = 'N1' AND ftr = 'D' AND season BETWEEN 2010 AND 2015;

(Count all data where division is N1 and result is draw between 2010 and 2015)
SELECT COUNT (*) FROM matches WHERE division_code = 'N1' AND ftr = 'D' AND season BETWEEN 2010 AND 2015;


```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. Where there is a tie the match with more home goals should come first.

```sql
<!-- Copy solution here -->
(Getting code for Premier League = E0)
SELECT code FROM divisions WHERE name = 'Premier League';

(Select matches played in PL)
SELECT * FROM matches WHERE division_code = 'E0';

(Sum of all goals scored in the PL)
SELECT SUM(fthg + ftag) FROM matches WHERE division_code = 'E0';

SELECT * FROM matches WHERE SUM (fthg + ftag ) > 0;

```

10) In which division and which season were the most goals scored?

```sql
<!-- Copy solution here -->


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)