
# Importing Data

``` r
s1Raw <- read.subtitles.season("Bojack SRT/Bojack S1 SRT/") %>% subDataFrame()
```

    ## Read: 12 episodes

``` r
s2Raw <- read.subtitles.season("Bojack SRT/Bojack S2 SRT/") %>% subDataFrame()
```

    ## Read: 12 episodes

``` r
s3Raw <- read.subtitles.season("Bojack SRT/Bojack S3 SRT/") %>% subDataFrame()
```

    ## Read: 12 episodes

``` r
s4Raw <- read.subtitles.season("Bojack SRT/Bojack S4 SRT/") %>% subDataFrame()
```

    ## Read: 12 episodes

``` r
all_s_Raw <- rbind(s1Raw,s2Raw,s3Raw,s4Raw) %>%
  filter(!str_detect(.$Text, "7ed")) %>% # Removes the sync information.
  filter(!str_detect(.$Text, "[0-9]x")) %>% # Removes episode title
  rename(Line = ID) %>% # Avoids Excel error of reading CSV files as corrupted if column 1 is named "ID"
  mutate(Line = str_remove_all(Line, "\\D"))

all_s_Raw %>% write_excel_csv("ALL_SEASONS_SRT_RAW.csv") # Suitable for transcription of speakers and listeners
```

This gives us a raw CSV file of the
dialogue

<table class="table table-striped table-hover" style="margin-left: auto; margin-right: auto;">

<thead>

<tr>

<th style="text-align:left;">

Line

</th>

<th style="text-align:left;">

Timecode.in

</th>

<th style="text-align:left;">

Timecode.out

</th>

<th style="text-align:left;">

Text

</th>

<th style="text-align:left;">

season

</th>

<th style="text-align:right;">

season\_num

</th>

<th style="text-align:right;">

episode\_num

</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

1

</td>

<td style="text-align:left;">

00:00:08.335

</td>

<td style="text-align:left;">

00:00:12.882

</td>

<td style="text-align:left;">

Horsin’ Around is filmed before a live studio audience.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

2

</td>

<td style="text-align:left;">

00:00:12.965

</td>

<td style="text-align:left;">

00:00:15.134

</td>

<td style="text-align:left;">

Mondays.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

3

</td>

<td style="text-align:left;">

00:00:15.218

</td>

<td style="text-align:left;">

00:00:18.012

</td>

<td style="text-align:left;">

Well, good morning to you too.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

4

</td>

<td style="text-align:left;">

00:00:18.096

</td>

<td style="text-align:left;">

00:00:19.346

</td>

<td style="text-align:left;">

Oh, hey.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

5

</td>

<td style="text-align:left;">

00:00:19.430

</td>

<td style="text-align:left;">

00:00:21.182

</td>

<td style="text-align:left;">

Where? I’d love hay.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

6

</td>

<td style="text-align:left;">

00:00:24.393

</td>

<td style="text-align:left;">

00:00:27.438

</td>

<td style="text-align:left;">

In 1987, the situation comedy Horsin’ Around

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

7

</td>

<td style="text-align:left;">

00:00:27.521

</td>

<td style="text-align:left;">

00:00:28.898

</td>

<td style="text-align:left;">

premiered on ABC.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

8

</td>

<td style="text-align:left;">

00:00:28.981

</td>

<td style="text-align:left;">

00:00:31.109

</td>

<td style="text-align:left;">

The show, in which a young, bachelor horse

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

9

</td>

<td style="text-align:left;">

00:00:31.192

</td>

<td style="text-align:left;">

00:00:33.319

</td>

<td style="text-align:left;">

is forced to reevaluate his priorities

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

10

</td>

<td style="text-align:left;">

00:00:33.402

</td>

<td style="text-align:left;">

00:00:35.738

</td>

<td style="text-align:left;">

when he agrees to raise three human children,

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

11

</td>

<td style="text-align:left;">

00:00:35.821

</td>

<td style="text-align:left;">

00:00:37.615

</td>

<td style="text-align:left;">

was initially dismissed by critics

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

12

</td>

<td style="text-align:left;">

00:00:37.698

</td>

<td style="text-align:left;">

00:00:41.202

</td>

<td style="text-align:left;">

as broad and saccharine and not good,

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

13

</td>

<td style="text-align:left;">

00:00:41.286

</td>

<td style="text-align:left;">

00:00:43.912

</td>

<td style="text-align:left;">

but the family comedy struck a chord with America

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

14

</td>

<td style="text-align:left;">

00:00:43.995

</td>

<td style="text-align:left;">

00:00:46.164

</td>

<td style="text-align:left;">

and went on to air for nine seasons.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

15

</td>

<td style="text-align:left;">

00:00:46.248

</td>

<td style="text-align:left;">

00:00:49.209

</td>

<td style="text-align:left;">

The star of Horsin’ Around, BoJack Horseman,

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

16

</td>

<td style="text-align:left;">

00:00:49.293

</td>

<td style="text-align:left;">

00:00:50.418

</td>

<td style="text-align:left;">

is our guest tonight.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

17

</td>

<td style="text-align:left;">

00:00:50.501

</td>

<td style="text-align:left;">

00:00:51.669

</td>

<td style="text-align:left;">

Welcome, BoJack.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

18

</td>

<td style="text-align:left;">

00:00:51.753

</td>

<td style="text-align:left;">

00:00:53.213

</td>

<td style="text-align:left;">

It is good to be here, Charlie.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

19

</td>

<td style="text-align:left;">

00:00:53.297

</td>

<td style="text-align:left;">

00:00:54.577

</td>

<td style="text-align:left;">

Sorry I was late. The traffic…

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

<tr>

<td style="text-align:left;">

20

</td>

<td style="text-align:left;">

00:00:54.631

</td>

<td style="text-align:left;">

00:00:55.924

</td>

<td style="text-align:left;">

It’s really no problem.

</td>

<td style="text-align:left;">

Bojack S1 SRT

</td>

<td style="text-align:right;">

1

</td>

<td style="text-align:right;">

1

</td>

</tr>

</tbody>

</table>

At this point, the project is diverging into two paths:

The first will be a holistic analysis of the raw text, without
assignation of lines to a specific character. This can tell us general
information about the show, for example, whether the sentiment of an
episode follows a trend from one episode, or one series, to the next.

The second will be to manually transcribe the dialogue, recording the
sender and receivers of each line of dialogue. This will be a
time-consuming process as there is no simple way to manage this unless I
am able to find scripts, as opposed to SRT files, for the show. From
this, I intend to develop a Shiny App allowing a user to examine each
character’s interactions by episode and season, looking at frequency and
sentiment of interactions with other characters.
