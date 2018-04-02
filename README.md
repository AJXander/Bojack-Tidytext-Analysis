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

## Data Acquistion

The processing of subtitle files was inspired by [Tamas Szilyagi's Tidytext analysis of Rick & Morty](http://tamaszilagyi.com/blog/a-tidy-text-analysis-of-rick-and-morty/).

I found unofficial SRT files of the show, which provides time-stamped dialogue transcription. Using the `subtools` package developed by [Francois Keck](https://github.com/fkeck/subtools), I reformatted the files into a single CSV file containing the entire dialogue of the four series of the show.

This transcription has some issues, including spelling errors and misunderstood dialogue; credits to the users who created the subtitles; overlapping two characters' dialogue into a single observation; and no indication of who has spoken which line.

[Data Import](Data_Import.md)

## Transcription

In order to carry out analysis of the characters based on their dialogue, we need to know not only who speaks, but who listens to them. This will be further examined, with additional guidance provided by [Frank Fischer](https://github.com/lehkost) on how to represent these interactions in a standardised way.

## Simple Analytics
Break down by season, by episode, (and by time) index within the episode.

1. Clean data, filter our the non-dialogue entries.
2. Mutate Season and Episode_Num into a factor variable.
3. Semantic Analysis for all episodes.
4. Visualise. Line chart or column chart for sentiment. Aggregate, or positive and negative as separate bars.
5. Summarise and analyse.

[Term Frequency](Frequency_Analysis.md)

[Term Importance](TFIDF.md)

[Major Character Frequency](CharacterFreq.md)

## Intermediate Analytics

[Character Interaction Chord Diagram](CircularMap.md)

[Shiny Application](http://ajxander.shinyapps.io/bojackscanner)

Shiny Browser to examine:

1. Character dialogue frequency - Who speaks most?
2. Character interaction frequency - Who interacts with whom?
3. Sentiment of speech - How positive or negative is the character's speech?

This iteration of the app is still far below the original aspiration, but represents a minimum viable product, with the ability to see the chord diagram, to examine a character's top 3 interactions, and to look at the positive/negative sentiment of the character's speech.

This is far below the original goal, and there are several glaring issues.

The first and most relevant is the fact that the sentiment plots are relatively uninformative in isolation. While they reflect the use of Shiny inputs to create reactive graphs, they do __not__ provide information in the most informative way. This stands to be improved significantly. A gross plot of positive and negative language does not consider the interaction with other characters or the overall plot arc of an episode or season.

Additionally, the app is only of minor use until further transcription efforts can be completed. With only 4 episodes manually transcribed, character interactions are limited as the early episodes establish character dynamics and contexts.

## Challenging analytics - Dependent on Transcription, Learning New Packages, and Network Science

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

