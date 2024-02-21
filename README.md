# utl-using-r-rvest-to-scrape-the-web-for-brazil-world-cup-performance
Using r rvest to scrape the web for brazil world cup performance
    %let pgm=utl-using-r-rvest-to-scrape-the-web-for-brazil-world-cup-performance;

    Using r rvest to scrape the web for brazil world cup performance

    github
    http://tinyurl.com/bdzzm8tr
    https://github.com/rogerjdeangelis/utl-using-r-rvest-to-scrape-the-web-for-brazil-world-cup-performance

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  This is the only input                                                                                                */
    /*                                                                                                                        */
    /*  http://tinyurl.com/vyfukpk5                                                                                           */
    /*  https://en.wikipedia.org/wiki/Brazil_at_the_FIFA_World_Cup                                                            */
    /*                                                                                                                        */
    /*------------------------------------------------------------------------------------------------------------------------*/
    /*                              |                                     |                                                   */
    /*       INPUT                  |             PROCESS                 |             OUTPUT                                */
    /*                              |                                     |                                                   */
    /*  http://tinyurl.com/vyfukpk5 |  file<-read_html(                   |                                                   */
    /*                              |     "http://tinyurl.com/vyfukpk5")  |  YEAR ROUND         POSITION PLD  W  D  L  GF  GA */
    /*                              |  tables<-html_nodes(file, "table")  |                                                   */
    /*                              |  want<-as.data.frame(               |  1930 Group stage     6th     2   1  0  1  5   2  */
    /*                              |     html_table(tables[1],fill=TRUE))|  1934 Round of 16     14th    1   0  0  1  1   3  */
    /*                              |                                     |  1938 Third place     3rd     5   3  1  1  14  11 */
    /*                              |                                     |  1950 Runners-up      2nd     6   4  1  1  22  6  */
    /*                              |                                     |  1954 Quarter-finals  5th     3   1  1  1  8   5  */
    /*                              |                                     |  1958 Champions       1st     6   5  1  0  16  4  */
    /*                              |                                     |  1962 Champions       1st     6   5  1  0  14  5  */
    /*                              |                                     |  1966 Group stage     11th    3   1  0  2  4   6  */
    /*                              |                                     |  1970 Champions       1st     6   6  0  0  19  7  */
    /*                              |                                     |  1974 Fourth place    4th     7   3  2  2  6   4  */
    /*                              |                                     |  1978 Third Place     3rd     7   4  3  0  10  3  */
    /*                              |                                     |  1982 Second group    5th     5   4  0  1  15  6  */
    /*                              |                                     |  1986 Quarter-finals  5th     5   4  1  0  10  1  */
    /*                              |                                     |  1990 Round of 16     9th     4   3  0  1  4   2  */
    /*                              |                                     |  1994 Champions       1st     7   5  2  0  11  3  */
    /*                              |                                     |  1998 Runners-up      2nd     7   4  1  2  14  10 */
    /*                              |                                     |  2002 Champions       1st     7   7  0  0  18  4  */
    /*                              |                                     |  2006 Quarter-finals  5th     5   4  0  1  10  2  */
    /*                              |                                     |  2010 Quarter-finals  6th     5   3  1  1  9   4  */
    /*                              |                                     |  2014 Fourth place    4th     7   3  2  2  11  14 */
    /*                              |                                     |  2018 Quarter-finals  6th     5   3  1  1  8   3  */
    /*                              |                                     |  2022 Quarter-finals  7th     5   3  1  1  8   3  */
    /*                              |                                     |                                                   */
    /**************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* This is the only input                                                                                                 */
    /*                                                                                                                        */
    /* http://tinyurl.com/vyfukpk5                                                                                            */
    /* https://en.wikipedia.org/wiki/Brazil_at_the_FIFA_World_Cup                                                             */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    %utl_rbegin;
    parmcards4;
    library(rvest)
    library(SASxport)
    file<-read_html("http://tinyurl.com/vyfukpk5")
    tables<-html_nodes(file, "table")
    want<-as.data.frame(html_table(tables[1],fill=TRUE))
    want
    write.xport(want,file="d:/xpt/want.xpt")
    ;;;;
    %utl_rend;

    libname xpt xport "d:/xpt/want.xpt";
    proc contents data=xpt._all_;
    run;quit;

    proc print data=xpt.want(where=(year<"2023")) width=min;
    run;quit;

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*                                                                                                                        */
    /* Obs    YEAR    ROUND                 POSITION    PLD    W    D_    L    GF    GA                                       */
    /*                                                                                                                        */
    /*   1    1930    Group stage             6th        2     1    0     1    5     2                                        */
    /*   2    1934    Round of 16             14th       1     0    0     1    1     3                                        */
    /*   3    1938    Third place             3rd        5     3    1     1    14    11                                       */
    /*   4    1950    Runners-up              2nd        6     4    1     1    22    6                                        */
    /*   5    1954    Quarter-finals          5th        3     1    1     1    8     5                                        */
    /*   6    1958    Champions               1st        6     5    1     0    16    4                                        */
    /*   7    1962    Champions               1st        6     5    1     0    14    5                                        */
    /*   8    1966    Group stage             11th       3     1    0     2    4     6                                        */
    /*   9    1970    Champions               1st        6     6    0     0    19    7                                        */
    /*  10    1974    Fourth place            4th        7     3    2     2    6     4                                        */
    /*  11    1978    Third Place             3rd        7     4    3     0    10    3                                        */
    /*  12    1982    Second group stage      5th        5     4    0     1    15    6                                        */
    /*  13    1986    Quarter-finals          5th        5     4    1     0    10    1                                        */
    /*  14    1990    Round of 16             9th        4     3    0     1    4     2                                        */
    /*  15    1994    Champions               1st        7     5    2     0    11    3                                        */
    /*  16    1998    Runners-up              2nd        7     4    1     2    14    10                                       */
    /*  17    2002    Champions               1st        7     7    0     0    18    4                                        */
    /*  18    2006    Quarter-finals          5th        5     4    0     1    10    2                                        */
    /*  19    2010    Quarter-finals          6th        5     3    1     1    9     4                                        */
    /*  20    2014    Fourth place            4th        7     3    2     2    11    14                                       */
    /*  21    2018    Quarter-finals          6th        5     3    1     1    8     3                                        */
    /*  22    2022    Quarter-finals          7th        5     3    1     1    8     3                                        */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
