
# Character Name Frequency

There are 5 main characters in Bojack Horseman: \* Bojack - The titular
horse from Horsin’ Around, and the protagonist of the series. An aimless
fading star, hitting a midlife crisis. \* Diane Nguyen - His ghostwriter
and friend, a woman struggling to reconcile her principles and her
lifestyle. \* Todd - His layabout roommate; kind, compassionate, and
often the instigator of B-plots \* Princess Carolyn - His sometime
girlfriend, agent, and a dedicated career woman seeking to excel in her
professional and private lives. \* Mister Peanutbutter - His frenemy; an
ever-enthusiastic and cheerful character, keen to see the best in
everything. Refuses to believe Bojack is anything but his best
friend.

``` r
tidy_bojack %>% filter(word %in% c("bojack", "peanutbutter", "carolyn", "diane", "todd")) %>% mutate(word = as.factor(word)) %>%
  count(word) %>% ggplot(aes(x = reorder(word,n), y = n)) + geom_bar(stat = "identity", fill = "steelblue") + coord_flip() + xlab("Character") + ylab("Frequency") + ggtitle("Character Naming Frequency", "Who is mentioned or addressed the most?")
```

![](CharacterFreq_files/figure-gfm/Character%20Name%20Frequency%20Plot-1.png)<!-- -->

This chart counts direct references to characters in all dialogue
throughout the entirety of the four series of Bojack Horseman. Bojack’s
prominence is unsurprising given his titular role, however the
proportion of references to other characters bears some discussion.

If we consider the roles of the characters:

Diane is a sometime love-interest, friend, and frequent advisor to
Bojack. She features prominently in the first season as his ghostwriter,
and later works alongside Princess Carolyn during the filming and
marketing of Secretariat. In Season 4, she branches out separately from
Bojack, as do most characters, and establishes her story independently.

Todd is a frequent source of B-Plots, commenting himself on his **zany
adventures**. He alternates between Bojack’s foil, comic relief, and
periodically a morality pet due to his naivete and trusting natures.

Mister Peanutbutter is a rival in Bojack’s eyes; Diane’s boyfriend; and
a frequent collaborator with Todd. His reduced frequency may not be due
to appearing less often, but rather not being referred to by name.

Finally, Princess Carolyn is a character often referred to by name. But
she also features less-heavily in a number of the storylines.

This plot does not tell us, however, how the frequency is distributed
over the entirety of the series. Let us consider that
below:

``` r
tidy_bojack %>% filter(word %in% c("bojack", "peanutbutter", "carolyn", "diane", "todd")) %>% mutate(word = as.factor(word)) %>%
  count(season, word) %>% ggplot(aes(x = reorder(word,n), y = n, fill = season)) + geom_bar(stat = "identity") + coord_flip() + xlab("Character") + ylab("Frequency") + ggtitle("Character Naming Frequency - By Season", "Who is mentioned or addressed the most?")
```

![](CharacterFreq_files/figure-gfm/Character%20Name%20Frequency%20Plot%20Divded%20By%20Season-1.png)<!-- -->

This plot shows how the show has evolved from a single focus to an
ensemble cast.

Bojack, Diane, and Todd, have all declined in frequency over the course
of the series, while Mister Peanutbutter and Princess Carolyn have risen
in prominence. This does not necessarily indicate that the characters
occur less frequently. To determine that I will have to complete my
transcription project.

This tells us that Bojack, Diane, and Todd, are all referred to by name
less frequently. If they are established characters, the viewer will not
need to hear their name so often, having become familiar with them.
Instead of being the object of interaction, they can become the subject,
and drive interactions with **others**.

In contrast, Mister Peanutbutter and Princess Carolyn were more
frequently seen as side characters in the early seasons. Their more
frequent mention might indicate more involvement with other characters,
and more focus in a plotline, rather than being supporting elements.

-----

This analysis is not truly revealing from a statistical perspective. It
shows how many times a name is mentioned and nothing more. Tallying this
by episode, as well as by season, could be an interesting future
development, examining whether some characters receive less attention as
others receive more.

I am also curious to look at the dialogue of the characters, to see if
their frequency of being referred to parallels their frequency of
interacting with other major and minor characters.
