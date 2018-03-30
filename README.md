# Bojack Horseman Text Analysis and Character Relationship Networks

As part of my studies, I am completing an analysis of a large body of unstructured text data, using the TidyText package for R, and semantic analysis.

As raw data for this study, I have acquired SRT files for every episode of the comedy, _Bojack Horseman_.
These SRT files contain all of the dialogue in the show, timestamped, however characters are not identified.

Initially, I will run simple analytics on the entirety of the SRT files.

Subsequently, I will watch each episode, annotating the CSV files manually with the speaker and listeners to each line.
I am determining how best to do this, including numbering conversations, and identifying cutaway scenes such as flashbacks, or humorous asides.

I then intend to develop a Shiny app to interactively examine the episodes. It is unrealistic to specifically produce each episode's summary analysis, and each character's. Using Shiny, it will be possible to create this and examine each character in detail.

My ultimate goal is to develop a network map, indicating the fluctuating relationships of characters over time.


## Introduction

The initial inspiration was the [Tidy Text Mining](https://www.tidytextmining.com/tidytext.html) package and the associated course on [Datacamp](https://www.datacamp.com/courses/sentiment-analysis-in-r-the-tidy-way). In addition to this, an intense course with [Eduardo Ariño de la Rubia](https://github.com/earino) on Unstructured Text Analysis, at CEU in Budapest, gave further direction.

## [Data Acquistion](../../Data_Import.html)

The processing of subtitle files was inspired by [Tamas Szilyagi's Tidytext analysis of Rick & Morty](http://tamaszilagyi.com/blog/a-tidy-text-analysis-of-rick-and-morty/).

I found unofficial SRT files of the show, which provides time-stamped dialogue transcription. Using the `subtools` package developed by [Francois Keck](https://github.com/fkeck/subtools), I reformatted the files into a single CSV file containing the entire dialogue of the four series of the show.

This transcription has some issues, including spelling errors and misunderstood dialogue; credits to the users who created the subtitles; overlapping two characters' dialogue into a single observation; and no indication of who has spoken which line.

## Transcription

In order to carry out analysis of the characters based on their dialogue, we need to know not only who speaks, but who listens to them. This will be further examined, with additional guidance provided by [Frank Fischer](https://github.com/lehkost) on how to represent these interactions in a standardised way.

## Simple Analytics
Break down by season, by episode, (and by time) index within the episode.

1. Clean data, filter our the non-dialogue entries.

2. Mutate Season and Episode_Num into a factor variable.

3. Semantic Analysis for all episodes.

4. Visualise. Line chart or column chart for sentiment. Aggregate, or positive and negative as separate bars.

5. Summarise and analyse.

* Term Frequency - By season
* Term Relevance - By season
* Frequency of characters names being mentioned?

## Intermediate Analytics

### Dependent on Transcription

Frequency of character speech
Frequency of characters speaking to one another


### Dependent on Code

Shiny Browser to examine:

1. Character dialogue frequency - Who speaks most?
2. Character interaction frequency - Who interacts with whom?
3. Sentiment of speech - How positive or negative is the character's speech?
4. Sentiment per episode, or per season - Plot of the sentiment of an episode or a season.
5. Word frequency - Per character, or per episode, or per season.

## Challenging analytics - Requires transcription and learning new packages.

* Show character relationship networks between the primary characters
* Edge width by frequency of interaction (Single episode? Cumulative Total? Weighted, so more recent matters more than less recent?
* Weight so a one-episode-wonder is less important than a recurring character?)
* Edge color by sentiment of the relationship? (Same weighting issues)


---

## Reference Notes

* http://tidytextmining.com
* https://cran.r-project.org/web/packages/network/vignettes/networkVignette.pdf
* https://briatte.github.io/ggnet/
* http://tamaszilagyi.com/blog/a-tidy-text-analysis-of-rick-and-morty/

