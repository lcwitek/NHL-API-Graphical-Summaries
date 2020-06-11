Project 1
================
Lauren Witek
6/12/2020

  - [Introduction to JSON data](#introduction-to-json-data)
      - [What is JSON?](#what-is-json)
      - [Where does JSON get used? Why is it a good way to store
        data?](#where-does-json-get-used-why-is-it-a-good-way-to-store-data)
      - [Packages/Functions available for reading JSON data into
        R](#packagesfunctions-available-for-reading-json-data-into-r)
      - [References](#references)
  - [Data: National Hockey League (NHL)
    API](#data-national-hockey-league-nhl-api)

# Introduction to JSON data

## What is JSON?

JSON (JavaScript Object Notation) is a open standard file format and a
data-interchange format that was derived from JavaScript and is easy to
read and
write.<sup>[1](https://www.json.org/json-en.htmlhttps://www.json.org/json-en.html)</sup>
It uses readable text to store and transmit data
objects.<sup>[2](https://en.wikipedia.org/wiki/JSON)</sup> JSON uses
conventions that are familiar to programmers of the C-family (ex. C,
C++, C\#, Java, etc) but is completely language
dependent.<sup>[1](https://www.json.org/json-en.htmlhttps://www.json.org/json-en.html)</sup>

JSON is built on two
structures<sup>[1](https://www.json.org/json-en.htmlhttps://www.json.org/json-en.html)</sup>

1.  *object* - A collection of name/value pairs
2.  *array* - An ordered list of values

JSON Structure<sup>[3](http://secretgeek.net/json_3mins)</sup>

1.  An *object* is contained in a squiggly bracket (**{}**)
2.  An *array* is surrounded by a square bracket (**\[\]**)
3.  *Names* (with double quptes) and *values* are separated by a colon
    (**:**)
      - A *value* can be a *string* with double quotes, a *number*, a
        *Boolean*, null, an *object* or an *array*
4.  *Array* elements are separated by commas (**,**)

Here is a small sample of
JSON:<sup>[4](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)</sup>

``` r
{
  "squadName": "Super hero squad",
  "homeTown": "Metro City",
  "formed": 2016,
  "secretBase": "Super tower",
  "active": true,
  "members": [
    {
      "name": "Molecule Man",
      "age": 29,
      "secretIdentity": "Dan Jukes",
      "powers": [
        "Radiation resistance",
        "Turning tiny",
        "Radiation blast"
      ]
    },
    {
      "name": "Madame Uppercut",
      "age": 39,
      "secretIdentity": "Jane Wilson",
      "powers": [
        "Million tonne punch",
        "Damage resistance",
        "Superhuman reflexes"
      ]
    },
    {
      "name": "Eternal Flame",
      "age": 1000000,
      "secretIdentity": "Unknown",
      "powers": [
        "Immortality",
        "Heat Immunity",
        "Inferno",
        "Teleportation",
        "Interdimensional travel"
      ]
    }
  ]
}
```

## Where does JSON get used? Why is it a good way to store data?

JSON is commonly used in web applications for transmitting data due to
its text only format. For example, sending some data from the server to
the client, so that it can be displayed on the webpage. It has also
become a popular format for database migration from modern apps over to
SQL
databases.<sup>[5](https://blog.sqlizer.io/posts/json-store-data/#:~:text=It%20all%20depends%20on%20what%20you%20need%20to%20do&text=Stored%20JSON%20data%20must%20be,a%20bonus%20for%20database%20migration.)</sup>

JSON is perfect for storing temporary data without the need for
reporting. JSON provides a high level of interoperability since it can
be used as a data format for any programming language. Stored JSON data
*must* be text which allows them to be easily sent between
servers.<sup>[5](https://blog.sqlizer.io/posts/json-store-data/#:~:text=It%20all%20depends%20on%20what%20you%20need%20to%20do&text=Stored%20JSON%20data%20must%20be,a%20bonus%20for%20database%20migration.)</sup>

## Packages/Functions available for reading JSON data into R

There are three major packages for JSON Data

1.  `jsonlite`
2.  `rjson`
3.  `RJSONIO`

I have chosen to use `jsonlite` when pulling in JSON data. `jsonlite`
can be combined with `dplyr` to work with JSON data easier and faster in
R. Its main strength is that it can convert between R objects and JSON
without loss of type or information. It is also ideal for interacting
with web APIs which will be demonstrated
below.<sup>[6](https://cran.r-project.org/web/packages/jsonlite/vignettes/json-aaquickstart.html)</sup>

## References

Information was procured from each of the following sites:

1.  [Introducting JSON](https://www.json.org/json-en.html)
2.  [JSON](https://en.wikipedia.org/wiki/JSON)
3.  [What is JSON: the 3 minute JSON
    Tutorial](http://secretgeek.net/json_3mins)
4.  [Working with
    JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
5.  [When should you store data as a JSON
    string?](https://blog.sqlizer.io/posts/json-store-data/#:~:text=It%20all%20depends%20on%20what%20you%20need%20to%20do&text=Stored%20JSON%20data%20must%20be,a%20bonus%20for%20database%20migration.)
6.  [Getting started with JSON and
    jsonlite](https://cran.r-project.org/web/packages/jsonlite/vignettes/json-aaquickstart.html)

# Data: National Hockey League (NHL) API

Exploring the dataset from the National Hockey League by reading the
JSON file pulled from the [NHL API](https://records.nhl.com/site/api)

| ID | First Season | Last Season | Team ID | Team Name      | Team Location |
| -: | -----------: | ----------: | ------: | :------------- | :------------ |
|  1 |     19171918 |          NA |       8 | Canadiens      | Montréal      |
|  2 |     19171918 |    19171918 |      41 | Wanderers      | Montreal      |
|  3 |     19171918 |    19341935 |      45 | Eagles         | St. Louis     |
|  4 |     19191920 |    19241925 |      37 | Tigers         | Hamilton      |
|  5 |     19171918 |          NA |      10 | Maple Leafs    | Toronto       |
|  6 |     19241925 |          NA |       6 | Bruins         | Boston        |
|  7 |     19241925 |    19371938 |      43 | Maroons        | Montreal      |
|  8 |     19251926 |    19411942 |      51 | Americans      | Brooklyn      |
|  9 |     19251926 |    19301931 |      39 | Quakers        | Philadelphia  |
| 10 |     19261927 |          NA |       3 | Rangers        | New York      |
| 11 |     19261927 |          NA |      16 | Blackhawks     | Chicago       |
| 12 |     19261927 |          NA |      17 | Red Wings      | Detroit       |
| 13 |     19671968 |    19771978 |      49 | Barons         | Cleveland     |
| 14 |     19671968 |          NA |      26 | Kings          | Los Angeles   |
| 15 |     19671968 |          NA |      25 | Stars          | Dallas        |
| 16 |     19671968 |          NA |       4 | Flyers         | Philadelphia  |
| 17 |     19671968 |          NA |       5 | Penguins       | Pittsburgh    |
| 18 |     19671968 |          NA |      19 | Blues          | St. Louis     |
| 19 |     19701971 |          NA |       7 | Sabres         | Buffalo       |
| 20 |     19701971 |          NA |      23 | Canucks        | Vancouver     |
| 21 |     19721973 |          NA |      20 | Flames         | Calgary       |
| 22 |     19721973 |          NA |       2 | Islanders      | New York      |
| 23 |     19741975 |          NA |       1 | Devils         | New Jersey    |
| 24 |     19741975 |          NA |      15 | Capitals       | Washington    |
| 25 |     19791980 |          NA |      22 | Oilers         | Edmonton      |
| 26 |     19791980 |          NA |      12 | Hurricanes     | Carolina      |
| 27 |     19791980 |          NA |      21 | Avalanche      | Colorado      |
| 28 |     19791980 |          NA |      53 | Coyotes        | Arizona       |
| 29 |     19911992 |          NA |      28 | Sharks         | San Jose      |
| 30 |     19921993 |          NA |       9 | Senators       | Ottawa        |
| 31 |     19921993 |          NA |      14 | Lightning      | Tampa Bay     |
| 32 |     19931994 |          NA |      24 | Ducks          | Anaheim       |
| 33 |     19931994 |          NA |      13 | Panthers       | Florida       |
| 34 |     19981999 |          NA |      18 | Predators      | Nashville     |
| 35 |     19992000 |          NA |      52 | Jets           | Winnipeg      |
| 36 |     20002001 |          NA |      29 | Blue Jackets   | Columbus      |
| 37 |     20002001 |          NA |      30 | Wild           | Minnesota     |
| 38 |     20172018 |          NA |      54 | Golden Knights | Vegas         |

|  ID | Active Franchise | First Season | Franchise ID | Game Type | Games Played | Goals Against | Goals For | Home Losses | Home Overtime Losses | Home Ties | Home Wins | Last Season | Losses | Overtime Losses | Penalty Minutes | Points Percent per Game | Points | Road Losses | Road Overtime Losses | Road Ties | Road Wins | Shootout Losses | Shootout Wins | Shutouts | Team ID | Team Name               | Ties | Tri-Code | Wins |
| --: | ---------------: | -----------: | -----------: | --------: | -----------: | ------------: | --------: | ----------: | -------------------: | --------: | --------: | ----------: | -----: | --------------: | --------------: | ----------------------: | -----: | ----------: | -------------------: | --------: | --------: | --------------: | ------------: | -------: | ------: | :---------------------- | ---: | :------- | ---: |
|   1 |                1 |     19821983 |           23 |         2 |         2937 |          8708 |      8647 |         507 |                   82 |        96 |       783 |          NA |   1181 |             162 |           44397 |                  0.5330 |   3131 |         674 |                   80 |       123 |       592 |              79 |            78 |      193 |       1 | New Jersey Devils       |  219 | NJD      | 1375 |
|   2 |                1 |     19821983 |           23 |         3 |          257 |           634 |       697 |          53 |                    0 |        NA |        74 |          NA |    120 |               0 |            4266 |                  0.0039 |      2 |          67 |                    0 |        NA |        63 |               0 |             0 |       25 |       1 | New Jersey Devils       |   NA | NJD      |  137 |
|   3 |                1 |     19721973 |           22 |         2 |         3732 |         11779 |     11889 |         674 |                   81 |       170 |       942 |          NA |   1570 |             159 |           57422 |                  0.5115 |   3818 |         896 |                   78 |       177 |       714 |              67 |            82 |      167 |       2 | New York Islanders      |  347 | NYI      | 1656 |
|   4 |                1 |     19721973 |           22 |         3 |          272 |           806 |       869 |          46 |                    1 |        NA |        84 |          NA |    124 |               0 |            5356 |                  0.0147 |      8 |          78 |                    0 |        NA |        64 |               0 |             0 |        9 |       2 | New York Islanders      |   NA | NYI      |  148 |
|   5 |                1 |     19261927 |           10 |         2 |         6504 |         19863 |     19864 |        1132 |                   73 |       448 |      1600 |          NA |   2693 |             147 |           85564 |                  0.5125 |   6667 |        1561 |                   74 |       360 |      1256 |              66 |            78 |      403 |       3 | New York Rangers        |  808 | NYR      | 2856 |
|   6 |                1 |     19261927 |           10 |         3 |          515 |          1436 |      1400 |         103 |                    0 |         1 |       137 |          NA |    263 |               0 |            8132 |                  0.0000 |      0 |         160 |                    0 |         7 |       107 |               0 |             0 |       44 |       3 | New York Rangers        |    8 | NYR      |  244 |
|   7 |                1 |     19671968 |           16 |         3 |          433 |          1292 |      1297 |          93 |                    0 |        NA |       131 |          NA |    212 |               0 |            8937 |                  0.0046 |      4 |         119 |                    0 |        NA |        90 |               0 |             0 |       31 |       4 | Philadelphia Flyers     |   NA | PHI      |  221 |
|   8 |                1 |     19671968 |           16 |         2 |         4115 |         12054 |     13527 |         572 |                   89 |       193 |      1204 |          NA |   1429 |             175 |           75761 |                  0.5759 |   4740 |         857 |                   86 |       264 |       850 |              88 |            50 |      245 |       4 | Philadelphia Flyers     |  457 | PHI      | 2054 |
|   9 |                1 |     19671968 |           17 |         2 |         4115 |         13893 |     13678 |         679 |                   58 |       205 |      1116 |          NA |   1718 |             148 |           65826 |                  0.5180 |   4263 |        1039 |                   90 |       178 |       750 |              53 |            80 |      184 |       5 | Pittsburgh Penguins     |  383 | PIT      | 1866 |
|  10 |                1 |     19671968 |           17 |         3 |          381 |          1100 |      1166 |          82 |                    0 |        NA |       111 |          NA |    175 |               0 |            6030 |                  0.0157 |     12 |          93 |                    1 |        NA |        95 |               0 |             0 |       30 |       5 | Pittsburgh Penguins     |   NA | PIT      |  206 |
|  11 |                1 |     19241925 |            6 |         2 |         6570 |         19001 |     20944 |         953 |                   89 |       376 |      1867 |          NA |   2387 |             184 |           88037 |                  0.5625 |   7391 |        1434 |                   95 |       415 |      1341 |              80 |            64 |      500 |       6 | Boston Bruins           |  791 | BOS      | 3208 |
|  12 |                1 |     19241925 |            6 |         3 |          651 |          1836 |      1894 |         144 |                    2 |         3 |       189 |          NA |    324 |               0 |           10355 |                  0.0307 |     40 |         180 |                    0 |         3 |       132 |               0 |             0 |       49 |       6 | Boston Bruins           |    6 | BOS      |  321 |
|  13 |                1 |     19701971 |           19 |         2 |         3889 |         11767 |     12333 |         623 |                   80 |       197 |      1045 |          NA |   1530 |             160 |           60329 |                  0.5334 |   4149 |         907 |                   80 |       212 |       745 |              71 |            77 |      194 |       7 | Buffalo Sabres          |  409 | BUF      | 1790 |
|  14 |                1 |     19701971 |           19 |         3 |          256 |           765 |       763 |          54 |                    0 |        NA |        73 |          NA |    132 |               0 |            4682 |                  0.0000 |      0 |          78 |                    0 |        NA |        51 |               0 |             0 |       18 |       7 | Buffalo Sabres          |   NA | BUF      |  124 |
|  15 |                1 |     19171918 |            1 |         3 |          749 |          1908 |      2248 |         128 |                    0 |         3 |       252 |          NA |    312 |               0 |           11916 |                  0.0000 |      0 |         184 |                    0 |         5 |       177 |               0 |             0 |       65 |       8 | Montréal Canadiens      |    8 | MTL      |  429 |
|  16 |                1 |     19171918 |            1 |         2 |         6731 |         18092 |     21632 |         870 |                   91 |       381 |      2025 |          NA |   2281 |             164 |           87019 |                  0.5868 |   7899 |        1411 |                   73 |       456 |      1424 |              63 |            68 |      542 |       8 | Montréal Canadiens      |  837 | MTL      | 3449 |
|  17 |                1 |     19921993 |           30 |         2 |         2139 |          6390 |      6093 |         403 |                   89 |        60 |       519 |          NA |    912 |             164 |           29175 |                  0.5084 |   2175 |         509 |                   75 |        55 |       429 |              78 |            56 |      135 |       9 | Ottawa Senators         |  115 | OTT      |  948 |
|  18 |                1 |     19921993 |           30 |         3 |          151 |           372 |       357 |          35 |                    0 |        NA |        37 |          NA |     79 |               0 |            2102 |                  0.0000 |      0 |          44 |                    0 |        NA |        35 |               0 |             0 |       12 |       9 | Ottawa Senators         |   NA | OTT      |   72 |
|  19 |                1 |     19271928 |            5 |         2 |         6460 |         19805 |     19793 |        1075 |                   82 |       388 |      1684 |          NA |   2682 |             167 |           91941 |                  0.5121 |   6616 |        1607 |                   85 |       385 |      1154 |              77 |            58 |      419 |      10 | Toronto Maple Leafs     |  773 | TOR      | 2838 |
|  20 |                1 |     19271928 |            5 |         3 |          533 |          1465 |      1370 |         115 |                    0 |         2 |       147 |          NA |    276 |               0 |            8444 |                  0.0113 |     12 |         161 |                    0 |         1 |       107 |               0 |             0 |       48 |      10 | Toronto Maple Leafs     |    3 | TOR      |  254 |
|  21 |                1 |     19992000 |           35 |         2 |          902 |          3014 |      2465 |         204 |                   38 |        26 |       183 |    20102011 |    437 |              78 |           13727 |                  0.4473 |    807 |         233 |                   40 |        19 |       159 |              29 |            37 |       41 |      11 | Atlanta Thrashers       |   45 | ATL      |  342 |
|  22 |                1 |     19992000 |           35 |         3 |            4 |            17 |         6 |           2 |                    0 |        NA |         0 |    20102011 |      4 |               0 |             115 |                  0.0000 |      0 |           2 |                    0 |        NA |         0 |               0 |             0 |        0 |      11 | Atlanta Thrashers       |   NA | ATL      |    0 |
|  23 |                1 |     19971998 |           26 |         3 |           93 |           233 |       219 |          19 |                    0 |        NA |        27 |          NA |     44 |               0 |            1117 |                  0.0860 |     16 |          25 |                    1 |        NA |        22 |               0 |             0 |       10 |      12 | Carolina Hurricanes     |   NA | CAR      |   49 |
|  24 |                1 |     19971998 |           26 |         2 |         1756 |          5004 |      4735 |         320 |                   72 |        52 |       433 |          NA |    713 |             166 |           19015 |                  0.5222 |   1834 |         393 |                   94 |        34 |       358 |              59 |            46 |       93 |      12 | Carolina Hurricanes     |   86 | CAR      |  791 |
|  25 |                1 |     19931994 |           33 |         2 |         2053 |          5969 |      5476 |         385 |                  112 |        65 |       465 |          NA |    856 |             203 |           28603 |                  0.4990 |   2049 |         471 |                   91 |        77 |       387 |              95 |            70 |      112 |      13 | Florida Panthers        |  142 | FLA      |  852 |
|  26 |                1 |     19931994 |           33 |         3 |           44 |           115 |       108 |          12 |                    0 |        NA |        11 |          NA |     26 |               0 |             623 |                  0.0000 |      0 |          14 |                    0 |        NA |         7 |               0 |             0 |        3 |      13 | Florida Panthers        |   NA | FLA      |   18 |
|  27 |                1 |     19921993 |           31 |         2 |         2138 |          6499 |      6035 |         407 |                   67 |        56 |       538 |          NA |    930 |             147 |           30489 |                  0.5044 |   2157 |         523 |                   80 |        56 |       411 |              57 |            67 |      118 |      14 | Tampa Bay Lightning     |  112 | TBL      |  949 |
|  28 |                1 |     19921993 |           31 |         3 |          137 |           370 |       362 |          34 |                    0 |        NA |        36 |          NA |     64 |               0 |            1962 |                  0.0803 |     22 |          30 |                    0 |        NA |        37 |               0 |             0 |       11 |      14 | Tampa Bay Lightning     |   NA | TBL      |   73 |
|  29 |                1 |     19741975 |           24 |         2 |         3577 |         11390 |     11325 |         612 |                   80 |       153 |       942 |          NA |   1452 |             158 |           56928 |                  0.5296 |   3789 |         840 |                   78 |       150 |       722 |              69 |            65 |      174 |      15 | Washington Capitals     |  303 | WSH      | 1664 |
|  30 |                1 |     19741975 |           24 |         3 |          282 |           797 |       813 |          72 |                    1 |        NA |        73 |          NA |    147 |               0 |            5004 |                  0.0674 |     38 |          75 |                    0 |        NA |        62 |               0 |             0 |       19 |      15 | Washington Capitals     |   NA | WSH      |  135 |
|  31 |                1 |     19261927 |           11 |         3 |          539 |          1639 |      1539 |         103 |                    0 |         1 |       163 |          NA |    270 |               0 |            8796 |                  0.0000 |      0 |         167 |                    0 |         4 |       101 |               0 |             0 |       32 |      16 | Chicago Blackhawks      |    5 | CHI      |  264 |
|  32 |                1 |     19261927 |           11 |         2 |         6504 |         19501 |     19376 |        1117 |                   82 |       410 |      1642 |          NA |   2736 |             166 |           91917 |                  0.5040 |   6556 |        1619 |                   84 |       404 |      1146 |              68 |            73 |      435 |      16 | Chicago Blackhawks      |  814 | CHI      | 2788 |
|  33 |                1 |     19321933 |           12 |         2 |         6237 |         18710 |     19423 |         929 |                   94 |       368 |      1729 |          NA |   2419 |             173 |           83995 |                  0.5363 |   6690 |        1490 |                   79 |       405 |      1143 |              73 |            69 |      421 |      17 | Detroit Red Wings       |  773 | DET      | 2872 |
|  34 |                1 |     19321933 |           12 |         3 |          618 |          1565 |      1745 |         126 |                    0 |         0 |       188 |          NA |    293 |               0 |            8735 |                  0.0000 |      0 |         167 |                    0 |         0 |       137 |               0 |             0 |       66 |      17 | Detroit Red Wings       |    0 | DET      |  325 |
|  35 |                1 |     19981999 |           34 |         2 |         1675 |          4554 |      4574 |         272 |                   73 |        34 |       459 |          NA |    633 |             161 |           19409 |                  0.5561 |   1863 |         361 |                   88 |        26 |       362 |              70 |            69 |      129 |      18 | Nashville Predators     |   60 | NSH      |  821 |
|  36 |                1 |     19981999 |           34 |         3 |          111 |           304 |       280 |          25 |                    0 |        NA |        31 |          NA |     60 |               0 |            1285 |                  0.0811 |     18 |          35 |                    1 |        NA |        20 |               0 |             0 |        6 |      18 | Nashville Predators     |   NA | NSH      |   51 |
|  37 |                1 |     19671968 |           18 |         2 |         4117 |         12518 |     12658 |         663 |                   67 |       218 |      1110 |          NA |   1625 |             158 |           65152 |                  0.5336 |   4394 |         962 |                   91 |       214 |       792 |              66 |            72 |      251 |      19 | St. Louis Blues         |  432 | STL      | 1902 |
|  38 |                1 |     19671968 |           18 |         3 |          391 |          1175 |      1074 |          86 |                    2 |        NA |       108 |          NA |    211 |               0 |            7594 |                  0.0409 |     32 |         125 |                    0 |        NA |        72 |               0 |             0 |       21 |      19 | St. Louis Blues         |   NA | STL      |  180 |
|  39 |                1 |     19801981 |           21 |         3 |          211 |           703 |       663 |          49 |                    1 |        NA |        58 |          NA |    113 |               0 |            5025 |                  0.0047 |      2 |          64 |                    1 |        NA |        40 |               0 |             0 |       12 |      20 | Calgary Flames          |   NA | CGY      |   98 |
|  40 |                1 |     19801981 |           21 |         2 |         3098 |          9660 |     10101 |         496 |                   68 |       135 |       848 |          NA |   1209 |             147 |           54974 |                  0.5423 |   3360 |         713 |                   79 |       136 |       623 |              64 |            51 |      140 |      20 | Calgary Flames          |  271 | CGY      | 1471 |
|  41 |                1 |     19951996 |           27 |         2 |         1922 |          5325 |      5660 |         323 |                   60 |        55 |       521 |          NA |    715 |             138 |           24911 |                  0.5658 |   2175 |         392 |                   78 |        46 |       447 |              41 |            73 |      116 |      21 | Colorado Avalanche      |  101 | COL      |  968 |
|  42 |                1 |     19951996 |           27 |         3 |          194 |           492 |       549 |          40 |                    0 |        NA |        60 |          NA |     85 |               0 |            2755 |                  0.0464 |     18 |          45 |                    0 |        NA |        49 |               0 |             0 |       21 |      21 | Colorado Avalanche      |   NA | COL      |  109 |
|  43 |                1 |     19791980 |           25 |         2 |         3179 |         10479 |     10593 |         575 |                   74 |       125 |       814 |          NA |   1318 |             165 |           54574 |                  0.5182 |   3295 |         743 |                   91 |       137 |       620 |              69 |            75 |      119 |      22 | Edmonton Oilers         |  262 | EDM      | 1434 |
|  44 |                1 |     19791980 |           25 |         3 |          264 |           795 |       971 |          45 |                    0 |        NA |        90 |          NA |    105 |               0 |            5694 |                  0.0000 |      0 |          60 |                    0 |        NA |        69 |               0 |             0 |       14 |      22 | Edmonton Oilers         |   NA | EDM      |  159 |
|  45 |                1 |     19701971 |           20 |         2 |         3889 |         12811 |     11987 |         724 |                   81 |       210 |       930 |          NA |   1717 |             155 |           66305 |                  0.4883 |   3798 |         993 |                   74 |       181 |       696 |              75 |            69 |      168 |      23 | Vancouver Canucks       |  391 | VAN      | 1626 |
|  46 |                1 |     19701971 |           20 |         3 |          229 |           735 |       634 |          63 |                    0 |        NA |        53 |          NA |    128 |               0 |            4540 |                  0.0000 |      0 |          65 |                    0 |        NA |        48 |               0 |             0 |       12 |      23 | Vancouver Canucks       |   NA | VAN      |  101 |
|  47 |                1 |     19931994 |           32 |         3 |          162 |           421 |       433 |          34 |                    0 |        NA |        51 |          NA |     73 |               0 |            2302 |                  0.0000 |      0 |          39 |                    0 |        NA |        38 |               0 |             0 |       16 |      24 | Anaheim Ducks           |   NA | ANA      |   89 |
|  48 |                1 |     19931994 |           32 |         2 |         2055 |          5659 |      5567 |         341 |                   78 |        58 |       551 |          NA |    804 |             171 |           30079 |                  0.5411 |   2224 |         463 |                   93 |        49 |       422 |              76 |            69 |      133 |      24 | Anaheim Ducks           |  107 | ANA      |  973 |
|  49 |                1 |     19931994 |           15 |         2 |         2053 |          5455 |      5864 |         307 |                   73 |        65 |       581 |          NA |    719 |             148 |           27640 |                  0.5833 |   2395 |         412 |                   75 |        60 |       480 |              56 |            71 |      146 |      25 | Dallas Stars            |  125 | DAL      | 1061 |
|  50 |                1 |     19931994 |           15 |         3 |          173 |           422 |       433 |          39 |                    0 |        NA |        49 |          NA |     83 |               0 |            2330 |                  0.0405 |     14 |          44 |                    2 |        NA |        41 |               0 |             0 |       14 |      25 | Dallas Stars            |   NA | DAL      |   90 |
|  51 |                1 |     19671968 |           14 |         2 |         4116 |         13591 |     12910 |         762 |                   66 |       211 |      1018 |          NA |   1801 |             158 |           65480 |                  0.4917 |   4048 |        1039 |                   92 |       213 |       715 |              70 |            68 |      232 |      26 | Los Angeles Kings       |  424 | LAK      | 1733 |
|  52 |                1 |     19671968 |           14 |         3 |          255 |           851 |       745 |          60 |                    0 |        NA |        62 |          NA |    144 |               0 |            4399 |                  0.0000 |      0 |          84 |                    0 |        NA |        49 |               0 |             0 |       14 |      26 | Los Angeles Kings       |   NA | LAK      |  111 |
|  53 |                1 |     19961997 |           28 |         2 |         1360 |          3824 |      3632 |         249 |                   48 |        43 |       340 |    20132014 |    546 |             105 |           19860 |                  0.5254 |   1429 |         297 |                   57 |        51 |       275 |              49 |            52 |      105 |      27 | Phoenix Coyotes         |   94 | PHX      |  615 |
|  54 |                1 |     19961997 |           28 |         3 |           57 |           169 |       133 |          19 |                    0 |        NA |        10 |    20132014 |     35 |               0 |             837 |                  0.0000 |      0 |          16 |                    0 |        NA |        12 |               0 |             0 |        4 |      27 | Phoenix Coyotes         |   NA | PHX      |   22 |
|  55 |                1 |     19911992 |           29 |         3 |          241 |           691 |       631 |          52 |                    0 |        NA |        67 |          NA |    122 |               0 |            3034 |                  0.0664 |     32 |          70 |                    1 |        NA |        52 |               0 |             0 |       15 |      28 | San Jose Sharks         |   NA | SJS      |  119 |
|  56 |                1 |     19911992 |           29 |         2 |         2218 |          6419 |      6339 |         394 |                   80 |        58 |       578 |          NA |    892 |             156 |           31225 |                  0.5354 |   2375 |         498 |                   76 |        63 |       471 |              64 |            71 |      155 |      28 | San Jose Sharks         |  121 | SJS      | 1049 |
|  57 |                1 |     20002001 |           36 |         2 |         1512 |          4425 |      3955 |         291 |                   69 |        18 |       379 |          NA |    672 |             147 |           19444 |                  0.4960 |   1500 |         381 |                   78 |        15 |       281 |              69 |            68 |      103 |      29 | Columbus Blue Jackets   |   33 | CBJ      |  660 |
|  58 |                1 |     20002001 |           36 |         3 |           31 |           109 |        86 |          10 |                    0 |        NA |         5 |          NA |     20 |               0 |             328 |                  0.2581 |     16 |          10 |                    1 |        NA |         6 |               0 |             0 |        0 |      29 | Columbus Blue Jackets   |   NA | CBJ      |   11 |
|  59 |                1 |     20002001 |           37 |         2 |         1511 |          3975 |      3985 |         238 |                   82 |        28 |       408 |          NA |    583 |             149 |           16636 |                  0.5467 |   1652 |         345 |                   67 |        27 |       316 |              69 |            70 |      109 |      30 | Minnesota Wild          |   55 | MIN      |  724 |
|  60 |                1 |     20002001 |           37 |         3 |           73 |           199 |       164 |          20 |                    0 |        NA |        14 |          NA |     47 |               0 |             775 |                  0.0137 |      2 |          27 |                    0 |        NA |        12 |               0 |             0 |        4 |      30 | Minnesota Wild          |   NA | MIN      |   26 |
|  61 |                1 |     19671968 |           15 |         2 |         2062 |          7373 |      6690 |         391 |                   NA |       163 |       477 |    19921993 |    970 |              NA |           36310 |                  0.4486 |   1850 |         579 |                   NA |       171 |       281 |               0 |             0 |       70 |      31 | Minnesota North Stars   |  334 | MNS      |  758 |
|  62 |                1 |     19671968 |           15 |         3 |          166 |           580 |       552 |          33 |                   NA |        NA |        45 |    19921993 |     86 |              NA |            3468 |                  0.0000 |      0 |          53 |                   NA |        NA |        35 |               0 |             0 |        9 |      31 | Minnesota North Stars   |   NA | MNS      |   80 |
|  63 |                1 |     19791980 |           27 |         3 |           80 |           286 |       247 |          17 |                   NA |        NA |        21 |    19941995 |     45 |              NA |            2434 |                  0.0000 |      0 |          28 |                   NA |        NA |        14 |               0 |             0 |        1 |      32 | Quebec Nordiques        |   NA | QUE      |   35 |
|  64 |                1 |     19791980 |           27 |         2 |         1256 |          4883 |      4625 |         245 |                   NA |        83 |       300 |    19941995 |    599 |              NA |           27013 |                  0.4594 |   1154 |         354 |                   NA |        77 |       197 |               0 |             0 |       28 |      32 | Quebec Nordiques        |  160 | QUE      |  497 |
|  65 |                1 |     19791980 |           28 |         2 |         1338 |          5347 |      4762 |         274 |                   NA |        88 |       307 |    19951996 |    660 |              NA |           27371 |                  0.4425 |   1184 |         386 |                   NA |        84 |       199 |               0 |             0 |       37 |      33 | Winnipeg Jets (1979)    |  172 | WIN      |  506 |
|  66 |                1 |     19791980 |           28 |         3 |           62 |           253 |       177 |          16 |                   NA |        NA |        12 |    19951996 |     43 |              NA |            1546 |                  0.0000 |      0 |          27 |                   NA |        NA |         7 |               0 |             0 |        0 |      33 | Winnipeg Jets (1979)    |   NA | WIN      |   19 |
|  67 |                1 |     19791980 |           26 |         2 |         1420 |          5345 |      4704 |         297 |                   NA |        95 |       318 |    19961997 |    709 |              NA |           29656 |                  0.4384 |   1245 |         412 |                   NA |        82 |       216 |               0 |             0 |       50 |      34 | Hartford Whalers        |  177 | HFD      |  534 |
|  68 |                1 |     19791980 |           26 |         3 |           49 |           177 |       143 |          10 |                   NA |        NA |        12 |    19961997 |     31 |              NA |            1273 |                  0.0000 |      0 |          21 |                   NA |        NA |         6 |               0 |             0 |        1 |      34 | Hartford Whalers        |   NA | HFD      |   18 |
|  69 |                1 |     19761977 |           23 |         2 |          480 |          1957 |      1426 |         115 |                   NA |        47 |        78 |    19811982 |    281 |              NA |            6216 |                  0.3250 |    312 |         166 |                   NA |        39 |        35 |               0 |             0 |        3 |      35 | Colorado Rockies        |   86 | CLR      |  113 |
|  70 |                1 |     19761977 |           23 |         3 |            2 |             6 |         3 |           1 |                   NA |        NA |         0 |    19811982 |      2 |              NA |              25 |                  0.0000 |      0 |           1 |                   NA |        NA |         0 |               0 |             0 |        0 |      35 | Colorado Rockies        |   NA | CLR      |    0 |
|  71 |                0 |     19171918 |            3 |         3 |           41 |            84 |        91 |           7 |                   NA |         4 |         6 |    19331934 |     17 |              NA |             497 |                  0.0000 |      0 |          10 |                   NA |         2 |        12 |               0 |             0 |        9 |      36 | Ottawa Senators (1917)  |    6 | SEN      |   18 |
|  72 |                0 |     19171918 |            3 |         2 |          542 |          1333 |      1458 |          81 |                   NA |        30 |       160 |    19331934 |    221 |              NA |            5667 |                  0.5341 |    579 |         140 |                   NA |        33 |        98 |               0 |             0 |       91 |      36 | Ottawa Senators (1917)  |   63 | SEN      |  258 |
|  73 |                0 |     19201921 |            4 |         2 |          126 |           475 |       414 |          30 |                   NA |         0 |        33 |    19241925 |     78 |              NA |            1042 |                  0.3770 |     95 |          48 |                   NA |         1 |        14 |               0 |             0 |        8 |      37 | Hamilton Tigers         |    1 | HAM      |   47 |
|  74 |                0 |     19251926 |            9 |         2 |          212 |           519 |       376 |          55 |                   NA |        10 |        41 |    19291930 |    122 |              NA |            1620 |                  0.3703 |    157 |          67 |                   NA |        13 |        26 |               0 |             0 |       33 |      38 | Pittsburgh Pirates      |   23 | PIR      |   67 |
|  75 |                0 |     19251926 |            9 |         3 |            4 |            12 |         8 |           1 |                   NA |         0 |         0 |    19291930 |      2 |              NA |              20 |                  0.0000 |      0 |           1 |                   NA |         1 |         1 |               0 |             0 |        0 |      38 | Pittsburgh Pirates      |    1 | PIR      |    1 |
|  76 |                0 |     19301931 |            9 |         2 |           44 |           184 |        76 |          17 |                   NA |         2 |         3 |    19301931 |     36 |              NA |             503 |                  0.1364 |     12 |          19 |                   NA |         2 |         1 |               0 |             0 |        1 |      39 | Philadelphia Quakers    |    4 | QUA      |    4 |
|  77 |                1 |     19261927 |           12 |         2 |          176 |           380 |       353 |          42 |                   NA |        11 |        35 |    19291930 |     87 |              NA |            1718 |                  0.4347 |    153 |          45 |                   NA |        14 |        29 |               0 |             0 |       29 |      40 | Detroit Cougars         |   25 | DCG      |   64 |
|  78 |                1 |     19261927 |           12 |         3 |            2 |             7 |         2 |           1 |                   NA |         0 |         0 |    19291930 |      2 |              NA |              24 |                  0.0000 |      0 |           1 |                   NA |         0 |         0 |               0 |             0 |        0 |      40 | Detroit Cougars         |    0 | DCG      |    0 |
|  79 |                0 |     19171918 |            2 |         2 |            6 |            37 |        17 |           2 |                   NA |         0 |         1 |    19171918 |      5 |              NA |              27 |                  0.1667 |      2 |           3 |                   NA |         0 |         0 |               0 |             0 |        0 |      41 | Montreal Wanderers      |    0 | MWN      |    1 |
|  80 |                0 |     19191920 |            4 |         2 |           24 |           177 |        91 |           8 |                   NA |         0 |         4 |    19191920 |     20 |              NA |             119 |                  0.1667 |      8 |          12 |                   NA |         0 |         0 |               0 |             0 |        0 |      42 | Quebec Bulldogs         |    0 | QBD      |    4 |
|  81 |                0 |     19241925 |            7 |         2 |          622 |          1405 |      1474 |         107 |                   NA |        48 |       156 |    19371938 |    260 |              NA |            7330 |                  0.5088 |    633 |         153 |                   NA |        43 |       115 |               0 |             0 |       75 |      43 | Montreal Maroons        |   91 | MMR      |  271 |
|  82 |                0 |     19241925 |            7 |         3 |           50 |            79 |        74 |          12 |                   NA |         8 |         9 |    19371938 |     21 |              NA |             535 |                  0.0000 |      0 |           9 |                   NA |         1 |        11 |               0 |             0 |       13 |      43 | Montreal Maroons        |    9 | MMR      |   20 |
|  83 |                0 |     19251926 |            8 |         2 |          736 |          2007 |      1510 |         154 |                   NA |        67 |       147 |    19401941 |    373 |              NA |            6348 |                  0.4090 |    602 |         219 |                   NA |        57 |        92 |               0 |             0 |       84 |      44 | New York Americans      |  124 | NYA      |  239 |
|  84 |                0 |     19251926 |            8 |         3 |           18 |            42 |        32 |           3 |                   NA |         1 |         4 |    19401941 |     11 |              NA |             155 |                  0.0000 |      0 |           8 |                   NA |         0 |         2 |               0 |             0 |        3 |      44 | New York Americans      |    1 | NYA      |    6 |
|  85 |                0 |     19341935 |            3 |         2 |           48 |           144 |        86 |          14 |                   NA |         3 |         7 |    19341935 |     31 |              NA |             408 |                  0.2917 |     28 |          17 |                   NA |         3 |         4 |               0 |             0 |        3 |      45 | St. Louis Eagles        |    6 | SLE      |   11 |
|  86 |                0 |     19671968 |           13 |         2 |          226 |           713 |       541 |          46 |                   NA |        23 |        44 |    19691970 |    118 |              NA |            2443 |                  0.3850 |    174 |          72 |                   NA |        19 |        22 |               0 |             0 |       11 |      46 | Oakland Seals           |   42 | OAK      |   66 |
|  87 |                0 |     19671968 |           13 |         3 |           11 |            36 |        31 |           4 |                   NA |        NA |         2 |    19691970 |      8 |              NA |             152 |                  0.0000 |      0 |           4 |                   NA |        NA |         1 |               0 |             0 |        0 |      46 | Oakland Seals           |   NA | OAK      |    3 |
|  88 |                1 |     19721973 |           21 |         2 |          636 |          2013 |      2057 |         104 |                   NA |        53 |       161 |    19791980 |    260 |              NA |            7608 |                  0.5063 |    644 |         156 |                   NA |        55 |       107 |               0 |             0 |       34 |      47 | Atlanta Flames          |  108 | AFM      |  268 |
|  89 |                1 |     19721973 |           21 |         3 |           17 |            62 |        32 |           6 |                   NA |        NA |         2 |    19791980 |     15 |              NA |             461 |                  0.0000 |      0 |           9 |                   NA |        NA |         0 |               0 |             0 |        0 |      47 | Atlanta Flames          |   NA | AFM      |    2 |
|  90 |                1 |     19741975 |           23 |         2 |          160 |           679 |       374 |          44 |                   NA |        16 |        20 |    19751976 |    110 |              NA |            1726 |                  0.2406 |     77 |          66 |                   NA |         7 |         7 |               0 |             0 |        0 |      48 | Kansas City Scouts      |   23 | KCS      |   27 |
|  91 |                0 |     19761977 |           13 |         2 |          160 |           617 |       470 |          34 |                   NA |        18 |        28 |    19771978 |     87 |              NA |            2021 |                  0.3750 |    120 |          53 |                   NA |         8 |        19 |               0 |             0 |        6 |      49 | Cleveland Barons        |   26 | CLE      |   47 |
|  92 |                1 |     19301931 |           12 |         2 |           92 |           213 |       197 |          10 |                   NA |        11 |        25 |    19311932 |     41 |              NA |             858 |                  0.4620 |     85 |          31 |                   NA |         6 |         9 |               0 |             0 |       12 |      50 | Detroit Falcons         |   17 | DFL      |   34 |
|  93 |                1 |     19301931 |           12 |         3 |            2 |             3 |         1 |           0 |                   NA |         1 |         0 |    19311932 |      1 |              NA |              12 |                  0.0000 |      0 |           1 |                   NA |         0 |         0 |               0 |             0 |        0 |      50 | Detroit Falcons         |    1 | DFL      |    0 |
|  94 |                0 |     19411942 |            8 |         2 |           48 |           175 |       133 |          12 |                   NA |         2 |        10 |    19411942 |     29 |              NA |             425 |                  0.3646 |     35 |          17 |                   NA |         1 |         6 |               0 |             0 |        1 |      51 | Brooklyn Americans      |    3 | BRK      |   16 |
|  95 |                1 |     20112012 |           35 |         3 |           27 |            74 |        78 |           9 |                    0 |        NA |         5 |          NA |     16 |               0 |             221 |                  0.4074 |     22 |           7 |                    0 |        NA |         6 |               0 |             0 |        2 |      52 | Winnipeg Jets           |   NA | WPG      |   11 |
|  96 |                1 |     20112012 |           35 |         2 |          693 |          1997 |      2039 |         123 |                   31 |        NA |       194 |          NA |    269 |              72 |            7217 |                  0.5599 |    776 |         146 |                   41 |        NA |       158 |              28 |            36 |       41 |      52 | Winnipeg Jets           |   NA | WPG      |  352 |
|  97 |                1 |     20142015 |           28 |         2 |          480 |          1443 |      1192 |         108 |                   26 |        NA |       104 |          NA |    236 |              54 |            4269 |                  0.4521 |    434 |         128 |                   28 |        NA |        86 |              20 |            23 |       24 |      53 | Arizona Coyotes         |   NA | ARI      |  190 |
|  98 |                1 |     20172018 |           38 |         2 |          235 |           669 |       748 |          33 |                   11 |        NA |        75 |          NA |     80 |              22 |            1709 |                  0.6128 |    288 |          47 |                   11 |        NA |        58 |               7 |            10 |       20 |      54 | Vegas Golden Knights    |   NA | VGK      |  133 |
|  99 |                1 |     20172018 |           38 |         3 |           27 |            70 |        82 |           4 |                    1 |        NA |         9 |          NA |     11 |               0 |             357 |                  0.5926 |     32 |           7 |                    1 |        NA |         7 |               0 |             0 |        5 |      54 | Vegas Golden Knights    |   NA | VGK      |   16 |
| 100 |                0 |     19701971 |           13 |         2 |          472 |          1867 |      1285 |         100 |                   NA |        52 |        84 |    19751976 |    283 |              NA |            5594 |                  0.3231 |    305 |         183 |                   NA |        21 |        32 |               0 |             0 |       15 |      56 | California Golden Seals |   73 | CGS      |  116 |
| 101 |                1 |     19171918 |            5 |         2 |           40 |           201 |       173 |           5 |                   NA |         0 |        15 |    19181919 |     22 |              NA |             696 |                  0.4500 |     36 |          17 |                   NA |         0 |         3 |               0 |             0 |        0 |      57 | Toronto Arenas          |    0 | TAN      |   18 |
| 102 |                1 |     19171918 |            5 |         3 |            7 |            28 |        28 |           2 |                   NA |         0 |         4 |    19181919 |      3 |              NA |             176 |                  0.0000 |      0 |           1 |                   NA |         0 |         0 |               0 |             0 |        0 |      57 | Toronto Arenas          |    0 | TAN      |    4 |
| 103 |                1 |     19191920 |            5 |         3 |           11 |            25 |        23 |           4 |                   NA |         0 |         4 |    19261927 |      6 |              NA |             123 |                  0.0000 |      0 |           2 |                   NA |         1 |         0 |               0 |             0 |        2 |      58 | Toronto St. Patricks    |    1 | TSP      |    4 |
| 104 |                1 |     19191920 |            5 |         2 |          230 |           768 |       724 |          37 |                   NA |         5 |        73 |    19261927 |    111 |              NA |            2339 |                  0.4957 |    228 |          74 |                   NA |         5 |        36 |               0 |             0 |        9 |      58 | Toronto St. Patricks    |   10 | TSP      |  109 |

| id | fewestGoals | fewestGoalsAgainst | fewestGoalsAgainstSeasons | fewestGoalsSeasons | fewestLosses | fewestLossesSeasons | fewestPoints | fewestPointsSeasons | fewestTies | fewestTiesSeasons                        | fewestWins | fewestWinsSeasons | franchiseId | franchiseName         | homeLossStreak | homeLossStreakDates                                  | homePointStreak | homePointStreakDates      | homeWinStreak | homeWinStreakDates                                   | homeWinlessStreak | homeWinlessStreakDates                               | lossStreak | lossStreakDates                                                                 | mostGameGoals | mostGameGoalsDates           | mostGoals | mostGoalsAgainst | mostGoalsAgainstSeasons | mostGoalsSeasons | mostLosses | mostLossesSeasons | mostPenaltyMinutes | mostPenaltyMinutesSeasons | mostPoints | mostPointsSeasons | mostShutouts | mostShutoutsSeasons        | mostTies | mostTiesSeasons | mostWins | mostWinsSeasons | pointStreak | pointStreakDates          | roadLossStreak | roadLossStreakDates       | roadPointStreak | roadPointStreakDates      | roadWinStreak | roadWinStreakDates                                   | roadWinlessStreak | roadWinlessStreakDates    | winStreak | winStreakDates            | winlessStreak | winlessStreakDates        |
| -: | ----------: | -----------------: | :------------------------ | :----------------- | -----------: | :------------------ | -----------: | :------------------ | ---------: | :--------------------------------------- | ---------: | :---------------- | ----------: | :-------------------- | -------------: | :--------------------------------------------------- | --------------: | :------------------------ | ------------: | :--------------------------------------------------- | ----------------: | :--------------------------------------------------- | ---------: | :------------------------------------------------------------------------------ | ------------: | :--------------------------- | --------: | ---------------: | :---------------------- | :--------------- | ---------: | :---------------- | -----------------: | :------------------------ | ---------: | :---------------- | -----------: | :------------------------- | -------: | :-------------- | -------: | :-------------- | ----------: | :------------------------ | -------------: | :------------------------ | --------------: | :------------------------ | ------------: | :--------------------------------------------------- | ----------------: | :------------------------ | --------: | :------------------------ | ------------: | :------------------------ |
| 29 |         164 |                187 | 2019-20 (82)              | 2001-02 (82)       |           22 | 2019-20 (82)        |           57 | 2001-02 (82)        |          8 | 2001-02 (82), 2002-03 (82), 2003-04 (82) |         22 | 2001-02 (82)      |          36 | Columbus Blue Jackets |              6 | Oct 12 2001 - Nov 09 2001, Oct 09 2015 - Nov 10 2015 |              12 | Feb 11 2013 - Mar 31 2013 |             8 | Nov 29 2016 - Jan 03 2017, Feb 24 2018 - Mar 22 2018 |                 8 | Oct 04 2001 - Nov 09 2001, Dec 04 2003 - Dec 31 2003 |          8 | Nov 17 2000 - Dec 03 2000, Mar 03 2004 - Mar 18 2004, Oct 09 2015 - Oct 22 2015 |            10 | Nov 04 2016 - MTL 0 @ CBJ 10 |       258 |              279 | 2005-06 (82)            | 2018-19 (82)     |         47 | 2001-02 (82)      |               1505 | 2002-03 (82)              |        108 | 2016-17 (82)      |           11 | 2007-08 (82), 2008-09 (82) |        9 | 2000-01 (82)    |       50 | 2016-17 (82)    |          18 | Nov 25 2016 - Jan 03 2017 |              9 | Oct 12 2005 - Nov 20 2005 |              11 | Nov 20 2016 - Dec 31 2016 |             8 | Mar 06 2015 - Mar 28 2015, Dec 01 2016 - Dec 31 2016 |                14 | Oct 09 2003 - Dec 20 2003 |        16 | Nov 29 2016 - Jan 03 2017 |             8 | Feb 08 2020 - Feb 22 2020 |

``` r
## Need to make graphs and charts of data 
```
