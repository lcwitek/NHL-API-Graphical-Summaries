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
