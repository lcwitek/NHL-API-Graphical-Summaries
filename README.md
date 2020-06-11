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

## Data: National Hockey League (NHL) API

Exploring the dataset from the National Hockey League by reading the
JSON file pulled from the [NHL API](https://records.nhl.com/site/api)

    ## # A tibble: 38 x 6
    ##       ID `First Season` `Last Season` `Team ID` `Team Name`    `Team Location`
    ##    <int>          <int>         <int>     <int> <chr>          <chr>          
    ##  1     1       19171918            NA         8 Canadiens      Montréal       
    ##  2     2       19171918      19171918        41 Wanderers      Montreal       
    ##  3     3       19171918      19341935        45 Eagles         St. Louis      
    ##  4     4       19191920      19241925        37 Tigers         Hamilton       
    ##  5     5       19171918            NA        10 Maple Leafs    Toronto        
    ##  6     6       19241925            NA         6 Bruins         Boston         
    ##  7     7       19241925      19371938        43 Maroons        Montreal       
    ##  8     8       19251926      19411942        51 Americans      Brooklyn       
    ##  9     9       19251926      19301931        39 Quakers        Philadelphia   
    ## 10    10       19261927            NA         3 Rangers        New York       
    ## 11    11       19261927            NA        16 Blackhawks     Chicago        
    ## 12    12       19261927            NA        17 Red Wings      Detroit        
    ## 13    13       19671968      19771978        49 Barons         Cleveland      
    ## 14    14       19671968            NA        26 Kings          Los Angeles    
    ## 15    15       19671968            NA        25 Stars          Dallas         
    ## 16    16       19671968            NA         4 Flyers         Philadelphia   
    ## 17    17       19671968            NA         5 Penguins       Pittsburgh     
    ## 18    18       19671968            NA        19 Blues          St. Louis      
    ## 19    19       19701971            NA         7 Sabres         Buffalo        
    ## 20    20       19701971            NA        23 Canucks        Vancouver      
    ## 21    21       19721973            NA        20 Flames         Calgary        
    ## 22    22       19721973            NA         2 Islanders      New York       
    ## 23    23       19741975            NA         1 Devils         New Jersey     
    ## 24    24       19741975            NA        15 Capitals       Washington     
    ## 25    25       19791980            NA        22 Oilers         Edmonton       
    ## 26    26       19791980            NA        12 Hurricanes     Carolina       
    ## 27    27       19791980            NA        21 Avalanche      Colorado       
    ## 28    28       19791980            NA        53 Coyotes        Arizona        
    ## 29    29       19911992            NA        28 Sharks         San Jose       
    ## 30    30       19921993            NA         9 Senators       Ottawa         
    ## 31    31       19921993            NA        14 Lightning      Tampa Bay      
    ## 32    32       19931994            NA        24 Ducks          Anaheim        
    ## 33    33       19931994            NA        13 Panthers       Florida        
    ## 34    34       19981999            NA        18 Predators      Nashville      
    ## 35    35       19992000            NA        52 Jets           Winnipeg       
    ## 36    36       20002001            NA        29 Blue Jackets   Columbus       
    ## 37    37       20002001            NA        30 Wild           Minnesota      
    ## 38    38       20172018            NA        54 Golden Knights Vegas

    ## # A tibble: 104 x 30
    ##        ID `Active Franchise` `First Season` `Franchise ID` `Game Type`
    ##     <int>              <int>          <int>          <int>       <int>
    ##   1     1                  1       19821983             23           2
    ##   2     2                  1       19821983             23           3
    ##   3     3                  1       19721973             22           2
    ##   4     4                  1       19721973             22           3
    ##   5     5                  1       19261927             10           2
    ##   6     6                  1       19261927             10           3
    ##   7     7                  1       19671968             16           3
    ##   8     8                  1       19671968             16           2
    ##   9     9                  1       19671968             17           2
    ##  10    10                  1       19671968             17           3
    ##  11    11                  1       19241925              6           2
    ##  12    12                  1       19241925              6           3
    ##  13    13                  1       19701971             19           2
    ##  14    14                  1       19701971             19           3
    ##  15    15                  1       19171918              1           3
    ##  16    16                  1       19171918              1           2
    ##  17    17                  1       19921993             30           2
    ##  18    18                  1       19921993             30           3
    ##  19    19                  1       19271928              5           2
    ##  20    20                  1       19271928              5           3
    ##  21    21                  1       19992000             35           2
    ##  22    22                  1       19992000             35           3
    ##  23    23                  1       19971998             26           3
    ##  24    24                  1       19971998             26           2
    ##  25    25                  1       19931994             33           2
    ##  26    26                  1       19931994             33           3
    ##  27    27                  1       19921993             31           2
    ##  28    28                  1       19921993             31           3
    ##  29    29                  1       19741975             24           2
    ##  30    30                  1       19741975             24           3
    ##  31    31                  1       19261927             11           3
    ##  32    32                  1       19261927             11           2
    ##  33    33                  1       19321933             12           2
    ##  34    34                  1       19321933             12           3
    ##  35    35                  1       19981999             34           2
    ##  36    36                  1       19981999             34           3
    ##  37    37                  1       19671968             18           2
    ##  38    38                  1       19671968             18           3
    ##  39    39                  1       19801981             21           3
    ##  40    40                  1       19801981             21           2
    ##  41    41                  1       19951996             27           2
    ##  42    42                  1       19951996             27           3
    ##  43    43                  1       19791980             25           2
    ##  44    44                  1       19791980             25           3
    ##  45    45                  1       19701971             20           2
    ##  46    46                  1       19701971             20           3
    ##  47    47                  1       19931994             32           3
    ##  48    48                  1       19931994             32           2
    ##  49    49                  1       19931994             15           2
    ##  50    50                  1       19931994             15           3
    ##  51    51                  1       19671968             14           2
    ##  52    52                  1       19671968             14           3
    ##  53    53                  1       19961997             28           2
    ##  54    54                  1       19961997             28           3
    ##  55    55                  1       19911992             29           3
    ##  56    56                  1       19911992             29           2
    ##  57    57                  1       20002001             36           2
    ##  58    58                  1       20002001             36           3
    ##  59    59                  1       20002001             37           2
    ##  60    60                  1       20002001             37           3
    ##  61    61                  1       19671968             15           2
    ##  62    62                  1       19671968             15           3
    ##  63    63                  1       19791980             27           3
    ##  64    64                  1       19791980             27           2
    ##  65    65                  1       19791980             28           2
    ##  66    66                  1       19791980             28           3
    ##  67    67                  1       19791980             26           2
    ##  68    68                  1       19791980             26           3
    ##  69    69                  1       19761977             23           2
    ##  70    70                  1       19761977             23           3
    ##  71    71                  0       19171918              3           3
    ##  72    72                  0       19171918              3           2
    ##  73    73                  0       19201921              4           2
    ##  74    74                  0       19251926              9           2
    ##  75    75                  0       19251926              9           3
    ##  76    76                  0       19301931              9           2
    ##  77    77                  1       19261927             12           2
    ##  78    78                  1       19261927             12           3
    ##  79    79                  0       19171918              2           2
    ##  80    80                  0       19191920              4           2
    ##  81    81                  0       19241925              7           2
    ##  82    82                  0       19241925              7           3
    ##  83    83                  0       19251926              8           2
    ##  84    84                  0       19251926              8           3
    ##  85    85                  0       19341935              3           2
    ##  86    86                  0       19671968             13           2
    ##  87    87                  0       19671968             13           3
    ##  88    88                  1       19721973             21           2
    ##  89    89                  1       19721973             21           3
    ##  90    90                  1       19741975             23           2
    ##  91    91                  0       19761977             13           2
    ##  92    92                  1       19301931             12           2
    ##  93    93                  1       19301931             12           3
    ##  94    94                  0       19411942              8           2
    ##  95    95                  1       20112012             35           3
    ##  96    96                  1       20112012             35           2
    ##  97    97                  1       20142015             28           2
    ##  98    98                  1       20172018             38           2
    ##  99    99                  1       20172018             38           3
    ## 100   100                  0       19701971             13           2
    ## 101   101                  1       19171918              5           2
    ## 102   102                  1       19171918              5           3
    ## 103   103                  1       19191920              5           3
    ## 104   104                  1       19191920              5           2
    ##     `Games Played` `Goals Against` `Goals For` `Home Losses`
    ##              <int>           <int>       <int>         <int>
    ##   1           2937            8708        8647           507
    ##   2            257             634         697            53
    ##   3           3732           11779       11889           674
    ##   4            272             806         869            46
    ##   5           6504           19863       19864          1132
    ##   6            515            1436        1400           103
    ##   7            433            1292        1297            93
    ##   8           4115           12054       13527           572
    ##   9           4115           13893       13678           679
    ##  10            381            1100        1166            82
    ##  11           6570           19001       20944           953
    ##  12            651            1836        1894           144
    ##  13           3889           11767       12333           623
    ##  14            256             765         763            54
    ##  15            749            1908        2248           128
    ##  16           6731           18092       21632           870
    ##  17           2139            6390        6093           403
    ##  18            151             372         357            35
    ##  19           6460           19805       19793          1075
    ##  20            533            1465        1370           115
    ##  21            902            3014        2465           204
    ##  22              4              17           6             2
    ##  23             93             233         219            19
    ##  24           1756            5004        4735           320
    ##  25           2053            5969        5476           385
    ##  26             44             115         108            12
    ##  27           2138            6499        6035           407
    ##  28            137             370         362            34
    ##  29           3577           11390       11325           612
    ##  30            282             797         813            72
    ##  31            539            1639        1539           103
    ##  32           6504           19501       19376          1117
    ##  33           6237           18710       19423           929
    ##  34            618            1565        1745           126
    ##  35           1675            4554        4574           272
    ##  36            111             304         280            25
    ##  37           4117           12518       12658           663
    ##  38            391            1175        1074            86
    ##  39            211             703         663            49
    ##  40           3098            9660       10101           496
    ##  41           1922            5325        5660           323
    ##  42            194             492         549            40
    ##  43           3179           10479       10593           575
    ##  44            264             795         971            45
    ##  45           3889           12811       11987           724
    ##  46            229             735         634            63
    ##  47            162             421         433            34
    ##  48           2055            5659        5567           341
    ##  49           2053            5455        5864           307
    ##  50            173             422         433            39
    ##  51           4116           13591       12910           762
    ##  52            255             851         745            60
    ##  53           1360            3824        3632           249
    ##  54             57             169         133            19
    ##  55            241             691         631            52
    ##  56           2218            6419        6339           394
    ##  57           1512            4425        3955           291
    ##  58             31             109          86            10
    ##  59           1511            3975        3985           238
    ##  60             73             199         164            20
    ##  61           2062            7373        6690           391
    ##  62            166             580         552            33
    ##  63             80             286         247            17
    ##  64           1256            4883        4625           245
    ##  65           1338            5347        4762           274
    ##  66             62             253         177            16
    ##  67           1420            5345        4704           297
    ##  68             49             177         143            10
    ##  69            480            1957        1426           115
    ##  70              2               6           3             1
    ##  71             41              84          91             7
    ##  72            542            1333        1458            81
    ##  73            126             475         414            30
    ##  74            212             519         376            55
    ##  75              4              12           8             1
    ##  76             44             184          76            17
    ##  77            176             380         353            42
    ##  78              2               7           2             1
    ##  79              6              37          17             2
    ##  80             24             177          91             8
    ##  81            622            1405        1474           107
    ##  82             50              79          74            12
    ##  83            736            2007        1510           154
    ##  84             18              42          32             3
    ##  85             48             144          86            14
    ##  86            226             713         541            46
    ##  87             11              36          31             4
    ##  88            636            2013        2057           104
    ##  89             17              62          32             6
    ##  90            160             679         374            44
    ##  91            160             617         470            34
    ##  92             92             213         197            10
    ##  93              2               3           1             0
    ##  94             48             175         133            12
    ##  95             27              74          78             9
    ##  96            693            1997        2039           123
    ##  97            480            1443        1192           108
    ##  98            235             669         748            33
    ##  99             27              70          82             4
    ## 100            472            1867        1285           100
    ## 101             40             201         173             5
    ## 102              7              28          28             2
    ## 103             11              25          23             4
    ## 104            230             768         724            37
    ##     `Home Overtime Losses` `Home Ties` `Home Wins` `Last Season` Losses
    ##                      <int>       <int>       <int>         <int>  <int>
    ##   1                     82          96         783            NA   1181
    ##   2                      0          NA          74            NA    120
    ##   3                     81         170         942            NA   1570
    ##   4                      1          NA          84            NA    124
    ##   5                     73         448        1600            NA   2693
    ##   6                      0           1         137            NA    263
    ##   7                      0          NA         131            NA    212
    ##   8                     89         193        1204            NA   1429
    ##   9                     58         205        1116            NA   1718
    ##  10                      0          NA         111            NA    175
    ##  11                     89         376        1867            NA   2387
    ##  12                      2           3         189            NA    324
    ##  13                     80         197        1045            NA   1530
    ##  14                      0          NA          73            NA    132
    ##  15                      0           3         252            NA    312
    ##  16                     91         381        2025            NA   2281
    ##  17                     89          60         519            NA    912
    ##  18                      0          NA          37            NA     79
    ##  19                     82         388        1684            NA   2682
    ##  20                      0           2         147            NA    276
    ##  21                     38          26         183      20102011    437
    ##  22                      0          NA           0      20102011      4
    ##  23                      0          NA          27            NA     44
    ##  24                     72          52         433            NA    713
    ##  25                    112          65         465            NA    856
    ##  26                      0          NA          11            NA     26
    ##  27                     67          56         538            NA    930
    ##  28                      0          NA          36            NA     64
    ##  29                     80         153         942            NA   1452
    ##  30                      1          NA          73            NA    147
    ##  31                      0           1         163            NA    270
    ##  32                     82         410        1642            NA   2736
    ##  33                     94         368        1729            NA   2419
    ##  34                      0           0         188            NA    293
    ##  35                     73          34         459            NA    633
    ##  36                      0          NA          31            NA     60
    ##  37                     67         218        1110            NA   1625
    ##  38                      2          NA         108            NA    211
    ##  39                      1          NA          58            NA    113
    ##  40                     68         135         848            NA   1209
    ##  41                     60          55         521            NA    715
    ##  42                      0          NA          60            NA     85
    ##  43                     74         125         814            NA   1318
    ##  44                      0          NA          90            NA    105
    ##  45                     81         210         930            NA   1717
    ##  46                      0          NA          53            NA    128
    ##  47                      0          NA          51            NA     73
    ##  48                     78          58         551            NA    804
    ##  49                     73          65         581            NA    719
    ##  50                      0          NA          49            NA     83
    ##  51                     66         211        1018            NA   1801
    ##  52                      0          NA          62            NA    144
    ##  53                     48          43         340      20132014    546
    ##  54                      0          NA          10      20132014     35
    ##  55                      0          NA          67            NA    122
    ##  56                     80          58         578            NA    892
    ##  57                     69          18         379            NA    672
    ##  58                      0          NA           5            NA     20
    ##  59                     82          28         408            NA    583
    ##  60                      0          NA          14            NA     47
    ##  61                     NA         163         477      19921993    970
    ##  62                     NA          NA          45      19921993     86
    ##  63                     NA          NA          21      19941995     45
    ##  64                     NA          83         300      19941995    599
    ##  65                     NA          88         307      19951996    660
    ##  66                     NA          NA          12      19951996     43
    ##  67                     NA          95         318      19961997    709
    ##  68                     NA          NA          12      19961997     31
    ##  69                     NA          47          78      19811982    281
    ##  70                     NA          NA           0      19811982      2
    ##  71                     NA           4           6      19331934     17
    ##  72                     NA          30         160      19331934    221
    ##  73                     NA           0          33      19241925     78
    ##  74                     NA          10          41      19291930    122
    ##  75                     NA           0           0      19291930      2
    ##  76                     NA           2           3      19301931     36
    ##  77                     NA          11          35      19291930     87
    ##  78                     NA           0           0      19291930      2
    ##  79                     NA           0           1      19171918      5
    ##  80                     NA           0           4      19191920     20
    ##  81                     NA          48         156      19371938    260
    ##  82                     NA           8           9      19371938     21
    ##  83                     NA          67         147      19401941    373
    ##  84                     NA           1           4      19401941     11
    ##  85                     NA           3           7      19341935     31
    ##  86                     NA          23          44      19691970    118
    ##  87                     NA          NA           2      19691970      8
    ##  88                     NA          53         161      19791980    260
    ##  89                     NA          NA           2      19791980     15
    ##  90                     NA          16          20      19751976    110
    ##  91                     NA          18          28      19771978     87
    ##  92                     NA          11          25      19311932     41
    ##  93                     NA           1           0      19311932      1
    ##  94                     NA           2          10      19411942     29
    ##  95                      0          NA           5            NA     16
    ##  96                     31          NA         194            NA    269
    ##  97                     26          NA         104            NA    236
    ##  98                     11          NA          75            NA     80
    ##  99                      1          NA           9            NA     11
    ## 100                     NA          52          84      19751976    283
    ## 101                     NA           0          15      19181919     22
    ## 102                     NA           0           4      19181919      3
    ## 103                     NA           0           4      19261927      6
    ## 104                     NA           5          73      19261927    111
    ##     `Overtime Losses` `Penalty Minutes` `Points Percent per Game` Points
    ##                 <int>             <int>                     <dbl>  <int>
    ##   1               162             44397                    0.533    3131
    ##   2                 0              4266                    0.0039      2
    ##   3               159             57422                    0.511    3818
    ##   4                 0              5356                    0.0147      8
    ##   5               147             85564                    0.512    6667
    ##   6                 0              8132                    0           0
    ##   7                 0              8937                    0.0046      4
    ##   8               175             75761                    0.576    4740
    ##   9               148             65826                    0.518    4263
    ##  10                 0              6030                    0.0157     12
    ##  11               184             88037                    0.562    7391
    ##  12                 0             10355                    0.0307     40
    ##  13               160             60329                    0.533    4149
    ##  14                 0              4682                    0           0
    ##  15                 0             11916                    0           0
    ##  16               164             87019                    0.587    7899
    ##  17               164             29175                    0.508    2175
    ##  18                 0              2102                    0           0
    ##  19               167             91941                    0.512    6616
    ##  20                 0              8444                    0.0113     12
    ##  21                78             13727                    0.447     807
    ##  22                 0               115                    0           0
    ##  23                 0              1117                    0.086      16
    ##  24               166             19015                    0.522    1834
    ##  25               203             28603                    0.499    2049
    ##  26                 0               623                    0           0
    ##  27               147             30489                    0.504    2157
    ##  28                 0              1962                    0.0803     22
    ##  29               158             56928                    0.530    3789
    ##  30                 0              5004                    0.0674     38
    ##  31                 0              8796                    0           0
    ##  32               166             91917                    0.504    6556
    ##  33               173             83995                    0.536    6690
    ##  34                 0              8735                    0           0
    ##  35               161             19409                    0.556    1863
    ##  36                 0              1285                    0.0811     18
    ##  37               158             65152                    0.534    4394
    ##  38                 0              7594                    0.0409     32
    ##  39                 0              5025                    0.0047      2
    ##  40               147             54974                    0.542    3360
    ##  41               138             24911                    0.566    2175
    ##  42                 0              2755                    0.0464     18
    ##  43               165             54574                    0.518    3295
    ##  44                 0              5694                    0           0
    ##  45               155             66305                    0.488    3798
    ##  46                 0              4540                    0           0
    ##  47                 0              2302                    0           0
    ##  48               171             30079                    0.541    2224
    ##  49               148             27640                    0.583    2395
    ##  50                 0              2330                    0.0405     14
    ##  51               158             65480                    0.492    4048
    ##  52                 0              4399                    0           0
    ##  53               105             19860                    0.525    1429
    ##  54                 0               837                    0           0
    ##  55                 0              3034                    0.0664     32
    ##  56               156             31225                    0.535    2375
    ##  57               147             19444                    0.496    1500
    ##  58                 0               328                    0.258      16
    ##  59               149             16636                    0.547    1652
    ##  60                 0               775                    0.0137      2
    ##  61                NA             36310                    0.449    1850
    ##  62                NA              3468                    0           0
    ##  63                NA              2434                    0           0
    ##  64                NA             27013                    0.459    1154
    ##  65                NA             27371                    0.442    1184
    ##  66                NA              1546                    0           0
    ##  67                NA             29656                    0.438    1245
    ##  68                NA              1273                    0           0
    ##  69                NA              6216                    0.325     312
    ##  70                NA                25                    0           0
    ##  71                NA               497                    0           0
    ##  72                NA              5667                    0.534     579
    ##  73                NA              1042                    0.377      95
    ##  74                NA              1620                    0.370     157
    ##  75                NA                20                    0           0
    ##  76                NA               503                    0.136      12
    ##  77                NA              1718                    0.435     153
    ##  78                NA                24                    0           0
    ##  79                NA                27                    0.167       2
    ##  80                NA               119                    0.167       8
    ##  81                NA              7330                    0.509     633
    ##  82                NA               535                    0           0
    ##  83                NA              6348                    0.409     602
    ##  84                NA               155                    0           0
    ##  85                NA               408                    0.292      28
    ##  86                NA              2443                    0.385     174
    ##  87                NA               152                    0           0
    ##  88                NA              7608                    0.506     644
    ##  89                NA               461                    0           0
    ##  90                NA              1726                    0.241      77
    ##  91                NA              2021                    0.375     120
    ##  92                NA               858                    0.462      85
    ##  93                NA                12                    0           0
    ##  94                NA               425                    0.365      35
    ##  95                 0               221                    0.407      22
    ##  96                72              7217                    0.560     776
    ##  97                54              4269                    0.452     434
    ##  98                22              1709                    0.613     288
    ##  99                 0               357                    0.593      32
    ## 100                NA              5594                    0.323     305
    ## 101                NA               696                    0.45       36
    ## 102                NA               176                    0           0
    ## 103                NA               123                    0           0
    ## 104                NA              2339                    0.496     228
    ##     `Road Losses` `Road Overtime Losses` `Road Ties` `Road Wins`
    ##             <int>                  <int>       <int>       <int>
    ##   1           674                     80         123         592
    ##   2            67                      0          NA          63
    ##   3           896                     78         177         714
    ##   4            78                      0          NA          64
    ##   5          1561                     74         360        1256
    ##   6           160                      0           7         107
    ##   7           119                      0          NA          90
    ##   8           857                     86         264         850
    ##   9          1039                     90         178         750
    ##  10            93                      1          NA          95
    ##  11          1434                     95         415        1341
    ##  12           180                      0           3         132
    ##  13           907                     80         212         745
    ##  14            78                      0          NA          51
    ##  15           184                      0           5         177
    ##  16          1411                     73         456        1424
    ##  17           509                     75          55         429
    ##  18            44                      0          NA          35
    ##  19          1607                     85         385        1154
    ##  20           161                      0           1         107
    ##  21           233                     40          19         159
    ##  22             2                      0          NA           0
    ##  23            25                      1          NA          22
    ##  24           393                     94          34         358
    ##  25           471                     91          77         387
    ##  26            14                      0          NA           7
    ##  27           523                     80          56         411
    ##  28            30                      0          NA          37
    ##  29           840                     78         150         722
    ##  30            75                      0          NA          62
    ##  31           167                      0           4         101
    ##  32          1619                     84         404        1146
    ##  33          1490                     79         405        1143
    ##  34           167                      0           0         137
    ##  35           361                     88          26         362
    ##  36            35                      1          NA          20
    ##  37           962                     91         214         792
    ##  38           125                      0          NA          72
    ##  39            64                      1          NA          40
    ##  40           713                     79         136         623
    ##  41           392                     78          46         447
    ##  42            45                      0          NA          49
    ##  43           743                     91         137         620
    ##  44            60                      0          NA          69
    ##  45           993                     74         181         696
    ##  46            65                      0          NA          48
    ##  47            39                      0          NA          38
    ##  48           463                     93          49         422
    ##  49           412                     75          60         480
    ##  50            44                      2          NA          41
    ##  51          1039                     92         213         715
    ##  52            84                      0          NA          49
    ##  53           297                     57          51         275
    ##  54            16                      0          NA          12
    ##  55            70                      1          NA          52
    ##  56           498                     76          63         471
    ##  57           381                     78          15         281
    ##  58            10                      1          NA           6
    ##  59           345                     67          27         316
    ##  60            27                      0          NA          12
    ##  61           579                     NA         171         281
    ##  62            53                     NA          NA          35
    ##  63            28                     NA          NA          14
    ##  64           354                     NA          77         197
    ##  65           386                     NA          84         199
    ##  66            27                     NA          NA           7
    ##  67           412                     NA          82         216
    ##  68            21                     NA          NA           6
    ##  69           166                     NA          39          35
    ##  70             1                     NA          NA           0
    ##  71            10                     NA           2          12
    ##  72           140                     NA          33          98
    ##  73            48                     NA           1          14
    ##  74            67                     NA          13          26
    ##  75             1                     NA           1           1
    ##  76            19                     NA           2           1
    ##  77            45                     NA          14          29
    ##  78             1                     NA           0           0
    ##  79             3                     NA           0           0
    ##  80            12                     NA           0           0
    ##  81           153                     NA          43         115
    ##  82             9                     NA           1          11
    ##  83           219                     NA          57          92
    ##  84             8                     NA           0           2
    ##  85            17                     NA           3           4
    ##  86            72                     NA          19          22
    ##  87             4                     NA          NA           1
    ##  88           156                     NA          55         107
    ##  89             9                     NA          NA           0
    ##  90            66                     NA           7           7
    ##  91            53                     NA           8          19
    ##  92            31                     NA           6           9
    ##  93             1                     NA           0           0
    ##  94            17                     NA           1           6
    ##  95             7                      0          NA           6
    ##  96           146                     41          NA         158
    ##  97           128                     28          NA          86
    ##  98            47                     11          NA          58
    ##  99             7                      1          NA           7
    ## 100           183                     NA          21          32
    ## 101            17                     NA           0           3
    ## 102             1                     NA           0           0
    ## 103             2                     NA           1           0
    ## 104            74                     NA           5          36
    ##     `Shootout Losses` `Shootout Wins` Shutouts `Team ID` `Team Name`            
    ##                 <int>           <int>    <int>     <int> <chr>                  
    ##   1                79              78      193         1 New Jersey Devils      
    ##   2                 0               0       25         1 New Jersey Devils      
    ##   3                67              82      167         2 New York Islanders     
    ##   4                 0               0        9         2 New York Islanders     
    ##   5                66              78      403         3 New York Rangers       
    ##   6                 0               0       44         3 New York Rangers       
    ##   7                 0               0       31         4 Philadelphia Flyers    
    ##   8                88              50      245         4 Philadelphia Flyers    
    ##   9                53              80      184         5 Pittsburgh Penguins    
    ##  10                 0               0       30         5 Pittsburgh Penguins    
    ##  11                80              64      500         6 Boston Bruins          
    ##  12                 0               0       49         6 Boston Bruins          
    ##  13                71              77      194         7 Buffalo Sabres         
    ##  14                 0               0       18         7 Buffalo Sabres         
    ##  15                 0               0       65         8 Montréal Canadiens     
    ##  16                63              68      542         8 Montréal Canadiens     
    ##  17                78              56      135         9 Ottawa Senators        
    ##  18                 0               0       12         9 Ottawa Senators        
    ##  19                77              58      419        10 Toronto Maple Leafs    
    ##  20                 0               0       48        10 Toronto Maple Leafs    
    ##  21                29              37       41        11 Atlanta Thrashers      
    ##  22                 0               0        0        11 Atlanta Thrashers      
    ##  23                 0               0       10        12 Carolina Hurricanes    
    ##  24                59              46       93        12 Carolina Hurricanes    
    ##  25                95              70      112        13 Florida Panthers       
    ##  26                 0               0        3        13 Florida Panthers       
    ##  27                57              67      118        14 Tampa Bay Lightning    
    ##  28                 0               0       11        14 Tampa Bay Lightning    
    ##  29                69              65      174        15 Washington Capitals    
    ##  30                 0               0       19        15 Washington Capitals    
    ##  31                 0               0       32        16 Chicago Blackhawks     
    ##  32                68              73      435        16 Chicago Blackhawks     
    ##  33                73              69      421        17 Detroit Red Wings      
    ##  34                 0               0       66        17 Detroit Red Wings      
    ##  35                70              69      129        18 Nashville Predators    
    ##  36                 0               0        6        18 Nashville Predators    
    ##  37                66              72      251        19 St. Louis Blues        
    ##  38                 0               0       21        19 St. Louis Blues        
    ##  39                 0               0       12        20 Calgary Flames         
    ##  40                64              51      140        20 Calgary Flames         
    ##  41                41              73      116        21 Colorado Avalanche     
    ##  42                 0               0       21        21 Colorado Avalanche     
    ##  43                69              75      119        22 Edmonton Oilers        
    ##  44                 0               0       14        22 Edmonton Oilers        
    ##  45                75              69      168        23 Vancouver Canucks      
    ##  46                 0               0       12        23 Vancouver Canucks      
    ##  47                 0               0       16        24 Anaheim Ducks          
    ##  48                76              69      133        24 Anaheim Ducks          
    ##  49                56              71      146        25 Dallas Stars           
    ##  50                 0               0       14        25 Dallas Stars           
    ##  51                70              68      232        26 Los Angeles Kings      
    ##  52                 0               0       14        26 Los Angeles Kings      
    ##  53                49              52      105        27 Phoenix Coyotes        
    ##  54                 0               0        4        27 Phoenix Coyotes        
    ##  55                 0               0       15        28 San Jose Sharks        
    ##  56                64              71      155        28 San Jose Sharks        
    ##  57                69              68      103        29 Columbus Blue Jackets  
    ##  58                 0               0        0        29 Columbus Blue Jackets  
    ##  59                69              70      109        30 Minnesota Wild         
    ##  60                 0               0        4        30 Minnesota Wild         
    ##  61                 0               0       70        31 Minnesota North Stars  
    ##  62                 0               0        9        31 Minnesota North Stars  
    ##  63                 0               0        1        32 Quebec Nordiques       
    ##  64                 0               0       28        32 Quebec Nordiques       
    ##  65                 0               0       37        33 Winnipeg Jets (1979)   
    ##  66                 0               0        0        33 Winnipeg Jets (1979)   
    ##  67                 0               0       50        34 Hartford Whalers       
    ##  68                 0               0        1        34 Hartford Whalers       
    ##  69                 0               0        3        35 Colorado Rockies       
    ##  70                 0               0        0        35 Colorado Rockies       
    ##  71                 0               0        9        36 Ottawa Senators (1917) 
    ##  72                 0               0       91        36 Ottawa Senators (1917) 
    ##  73                 0               0        8        37 Hamilton Tigers        
    ##  74                 0               0       33        38 Pittsburgh Pirates     
    ##  75                 0               0        0        38 Pittsburgh Pirates     
    ##  76                 0               0        1        39 Philadelphia Quakers   
    ##  77                 0               0       29        40 Detroit Cougars        
    ##  78                 0               0        0        40 Detroit Cougars        
    ##  79                 0               0        0        41 Montreal Wanderers     
    ##  80                 0               0        0        42 Quebec Bulldogs        
    ##  81                 0               0       75        43 Montreal Maroons       
    ##  82                 0               0       13        43 Montreal Maroons       
    ##  83                 0               0       84        44 New York Americans     
    ##  84                 0               0        3        44 New York Americans     
    ##  85                 0               0        3        45 St. Louis Eagles       
    ##  86                 0               0       11        46 Oakland Seals          
    ##  87                 0               0        0        46 Oakland Seals          
    ##  88                 0               0       34        47 Atlanta Flames         
    ##  89                 0               0        0        47 Atlanta Flames         
    ##  90                 0               0        0        48 Kansas City Scouts     
    ##  91                 0               0        6        49 Cleveland Barons       
    ##  92                 0               0       12        50 Detroit Falcons        
    ##  93                 0               0        0        50 Detroit Falcons        
    ##  94                 0               0        1        51 Brooklyn Americans     
    ##  95                 0               0        2        52 Winnipeg Jets          
    ##  96                28              36       41        52 Winnipeg Jets          
    ##  97                20              23       24        53 Arizona Coyotes        
    ##  98                 7              10       20        54 Vegas Golden Knights   
    ##  99                 0               0        5        54 Vegas Golden Knights   
    ## 100                 0               0       15        56 California Golden Seals
    ## 101                 0               0        0        57 Toronto Arenas         
    ## 102                 0               0        0        57 Toronto Arenas         
    ## 103                 0               0        2        58 Toronto St. Patricks   
    ## 104                 0               0        9        58 Toronto St. Patricks   
    ##      Ties `Tri-Code`  Wins
    ##     <int> <chr>      <int>
    ##   1   219 NJD         1375
    ##   2    NA NJD          137
    ##   3   347 NYI         1656
    ##   4    NA NYI          148
    ##   5   808 NYR         2856
    ##   6     8 NYR          244
    ##   7    NA PHI          221
    ##   8   457 PHI         2054
    ##   9   383 PIT         1866
    ##  10    NA PIT          206
    ##  11   791 BOS         3208
    ##  12     6 BOS          321
    ##  13   409 BUF         1790
    ##  14    NA BUF          124
    ##  15     8 MTL          429
    ##  16   837 MTL         3449
    ##  17   115 OTT          948
    ##  18    NA OTT           72
    ##  19   773 TOR         2838
    ##  20     3 TOR          254
    ##  21    45 ATL          342
    ##  22    NA ATL            0
    ##  23    NA CAR           49
    ##  24    86 CAR          791
    ##  25   142 FLA          852
    ##  26    NA FLA           18
    ##  27   112 TBL          949
    ##  28    NA TBL           73
    ##  29   303 WSH         1664
    ##  30    NA WSH          135
    ##  31     5 CHI          264
    ##  32   814 CHI         2788
    ##  33   773 DET         2872
    ##  34     0 DET          325
    ##  35    60 NSH          821
    ##  36    NA NSH           51
    ##  37   432 STL         1902
    ##  38    NA STL          180
    ##  39    NA CGY           98
    ##  40   271 CGY         1471
    ##  41   101 COL          968
    ##  42    NA COL          109
    ##  43   262 EDM         1434
    ##  44    NA EDM          159
    ##  45   391 VAN         1626
    ##  46    NA VAN          101
    ##  47    NA ANA           89
    ##  48   107 ANA          973
    ##  49   125 DAL         1061
    ##  50    NA DAL           90
    ##  51   424 LAK         1733
    ##  52    NA LAK          111
    ##  53    94 PHX          615
    ##  54    NA PHX           22
    ##  55    NA SJS          119
    ##  56   121 SJS         1049
    ##  57    33 CBJ          660
    ##  58    NA CBJ           11
    ##  59    55 MIN          724
    ##  60    NA MIN           26
    ##  61   334 MNS          758
    ##  62    NA MNS           80
    ##  63    NA QUE           35
    ##  64   160 QUE          497
    ##  65   172 WIN          506
    ##  66    NA WIN           19
    ##  67   177 HFD          534
    ##  68    NA HFD           18
    ##  69    86 CLR          113
    ##  70    NA CLR            0
    ##  71     6 SEN           18
    ##  72    63 SEN          258
    ##  73     1 HAM           47
    ##  74    23 PIR           67
    ##  75     1 PIR            1
    ##  76     4 QUA            4
    ##  77    25 DCG           64
    ##  78     0 DCG            0
    ##  79     0 MWN            1
    ##  80     0 QBD            4
    ##  81    91 MMR          271
    ##  82     9 MMR           20
    ##  83   124 NYA          239
    ##  84     1 NYA            6
    ##  85     6 SLE           11
    ##  86    42 OAK           66
    ##  87    NA OAK            3
    ##  88   108 AFM          268
    ##  89    NA AFM            2
    ##  90    23 KCS           27
    ##  91    26 CLE           47
    ##  92    17 DFL           34
    ##  93     1 DFL            0
    ##  94     3 BRK           16
    ##  95    NA WPG           11
    ##  96    NA WPG          352
    ##  97    NA ARI          190
    ##  98    NA VGK          133
    ##  99    NA VGK           16
    ## 100    73 CGS          116
    ## 101     0 TAN           18
    ## 102     0 TAN            4
    ## 103     1 TSP            4
    ## 104    10 TSP          109

``` r
nhl("/franchise-season-records?cayenneExp=franchiseId=ID", 36)
```

| id | fewestGoals | fewestGoalsAgainst | fewestGoalsAgainstSeasons | fewestGoalsSeasons | fewestLosses | fewestLossesSeasons | fewestPoints | fewestPointsSeasons | fewestTies | fewestTiesSeasons                        | fewestWins | fewestWinsSeasons | franchiseId | franchiseName         | homeLossStreak | homeLossStreakDates                                  | homePointStreak | homePointStreakDates      | homeWinStreak | homeWinStreakDates                                   | homeWinlessStreak | homeWinlessStreakDates                               | lossStreak | lossStreakDates                                                                 | mostGameGoals | mostGameGoalsDates           | mostGoals | mostGoalsAgainst | mostGoalsAgainstSeasons | mostGoalsSeasons | mostLosses | mostLossesSeasons | mostPenaltyMinutes | mostPenaltyMinutesSeasons | mostPoints | mostPointsSeasons | mostShutouts | mostShutoutsSeasons        | mostTies | mostTiesSeasons | mostWins | mostWinsSeasons | pointStreak | pointStreakDates          | roadLossStreak | roadLossStreakDates       | roadPointStreak | roadPointStreakDates      | roadWinStreak | roadWinStreakDates                                   | roadWinlessStreak | roadWinlessStreakDates    | winStreak | winStreakDates            | winlessStreak | winlessStreakDates        |
| -: | ----------: | -----------------: | :------------------------ | :----------------- | -----------: | :------------------ | -----------: | :------------------ | ---------: | :--------------------------------------- | ---------: | :---------------- | ----------: | :-------------------- | -------------: | :--------------------------------------------------- | --------------: | :------------------------ | ------------: | :--------------------------------------------------- | ----------------: | :--------------------------------------------------- | ---------: | :------------------------------------------------------------------------------ | ------------: | :--------------------------- | --------: | ---------------: | :---------------------- | :--------------- | ---------: | :---------------- | -----------------: | :------------------------ | ---------: | :---------------- | -----------: | :------------------------- | -------: | :-------------- | -------: | :-------------- | ----------: | :------------------------ | -------------: | :------------------------ | --------------: | :------------------------ | ------------: | :--------------------------------------------------- | ----------------: | :------------------------ | --------: | :------------------------ | ------------: | :------------------------ |
| 29 |         164 |                187 | 2019-20 (82)              | 2001-02 (82)       |           22 | 2019-20 (82)        |           57 | 2001-02 (82)        |          8 | 2001-02 (82), 2002-03 (82), 2003-04 (82) |         22 | 2001-02 (82)      |          36 | Columbus Blue Jackets |              6 | Oct 12 2001 - Nov 09 2001, Oct 09 2015 - Nov 10 2015 |              12 | Feb 11 2013 - Mar 31 2013 |             8 | Nov 29 2016 - Jan 03 2017, Feb 24 2018 - Mar 22 2018 |                 8 | Oct 04 2001 - Nov 09 2001, Dec 04 2003 - Dec 31 2003 |          8 | Nov 17 2000 - Dec 03 2000, Mar 03 2004 - Mar 18 2004, Oct 09 2015 - Oct 22 2015 |            10 | Nov 04 2016 - MTL 0 @ CBJ 10 |       258 |              279 | 2005-06 (82)            | 2018-19 (82)     |         47 | 2001-02 (82)      |               1505 | 2002-03 (82)              |        108 | 2016-17 (82)      |           11 | 2007-08 (82), 2008-09 (82) |        9 | 2000-01 (82)    |       50 | 2016-17 (82)    |          18 | Nov 25 2016 - Jan 03 2017 |              9 | Oct 12 2005 - Nov 20 2005 |              11 | Nov 20 2016 - Dec 31 2016 |             8 | Mar 06 2015 - Mar 28 2015, Dec 01 2016 - Dec 31 2016 |                14 | Oct 09 2003 - Dec 20 2003 |        16 | Nov 29 2016 - Jan 03 2017 |             8 | Feb 08 2020 - Feb 22 2020 |
