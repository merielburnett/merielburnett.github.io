## Words associated with male versus female dialogue in movies 

A while ago I discovered a great package for R called 'text'. The functions in this package are a significant upgrade from the tidytext methods I've been using, allowing for some very cool text analysis methods. For one thing, text has a function to visualize words in relation to a given binary or numeric variable. Individual differences variables like personality traits and demographics really lend themselves to these kind of analyses. For example, we can examine how the language people use varies in relation to a their gender or degree of neuroticism. Another way of using this technique is to look at how words vary not between individuals, but between years or historical periods. One might be curious to know what kind of words are predictive of a pre versus post-9/11 campaign speech. Yet another approach is to examine the association between words and some kind of external classification system. For example, in humor research we might correlate the words in people's jokes with an ordinal rating of how funny their joke was. There really are endless possibilities. 

So, to learn the ropes of this package, I thought I'd start simple and have a crack at examining the relation between gender and words in film dialogue. I wanted to know: how do male versus female characters speak in movies*? I grabbed a pre-compiled corpus off of kaggle (link here), cleaned it up somewhat haphazardly (i.e., liberal use of drop.na), and then computed, preprocessed, and projected the word embeddings across character gender. The results are shown in Figure 1.

**Figure 1.**

*Association Between Film Dialogue Words and Character Gender*
![gender2](https://github.com/merielburnett/merielburnett.github.io/assets/171220833/9600fb08-0226-4924-982f-70cccd2d4e3c)


We end up with some pretty interesting results. Words associated with women are uniformly positive and almost entirely romance-related. In contrast, words associated with men are mostly nouns related to male-dominated forms of work (e.g., maritime/military: morse, cannons, ports, cartel). As with any analysis, it's important to consider the limitations of the data** before making inferences about the results. Nevertheless, these word associations are approximately in line with what we might expect. No single concept ties all male speech together (maritime/military was my best guess), but it is clearly diffentiated from female speech by word emotionality and also word type. Male words are mostly valence-neutral nouns, while female words are mostly positive adjectives. This comparison paints a picture of men in film participating in the workforce, discussing things like the 'cartel', 'business', and 'airspace', and women in film in the home, revealing their feelings ('happy', 'sad', 'romantic') and announcing pregnancies and marriages. 

This pattern could be occurring for several reasons, aside from that they indicate a tendency for films to represent women in somewhat antiquated social roles. For instance, it may be that a higher proportion of female characters are found in romantic movies, in which case my finding would be more a reflection of gender differences in films genres and less a reflection of gender differences in dialogue. That particular hypothesis doesn't seem likely, as about 6% of male characters compared to 8% of female characters were in films with 'romance' listed as the primary genre. Negligible differences were also observed in other potentially mediating genres like drama (17% male, 19% female) and sci-fi (6% male, 5% female). That being said, it would be interesting to look at gender differences in film dialogue within a single genre or maybe with a larger or more recent sample of films. However, I think my poor laptop is tired of computing embeddings for now, so I'll leave all that for a later date. 


*This is just an exercise in text analysis for the purpose of fun and edification. I'm not actually drawing any empirical conclusions about gender representation in film. 

**The original film dialogue corpus had lines from 617 films. I excluded all lines from films released before 1960, bringing the total down to 512 films. I then collapsed lines of dialogue into characters, so all dialogue related to a given character in a given film was combined into a single row. Rows that did not have a gender were dropped. The result was 2434 individual characters, who each spoke an average of 756 words. There were obviously far more than 512 films released between 1960 and 2009 (the most recent film in the dataset), so this is far from a comprehensive sample. The data is instead compiled of films for which scripts and IMDB data are publically available, meaning it has what Grimmer et al. (2022) would call retrieval bias. Additionally, not having a gender identifier may have varied systematically with other factors, like film or actor popularity. All told, we can conclude that my data is skewed in some predictable and some unpredictable ways. 

Kjell, O., Giorgi, S., & Schwartz, H. A. (2021). *The text-package: An R-package for Analyzing and Visualizing Human Language Using Natural Language Processing and Deep Learning*. OSF. https://doi.org/10.31234/osf.io/293kt

Grimmer, J., Roberts, M., Stewart, B. (2022). *Text as Data: A New Framework for Machine Learning and the Social Sciences*. Princeton University Press.

Silge, J., Robinson, D. *Text Mining with R: A Tidy Approach*. Retrieved June 21, 2024, from [https://www.amazon.com.au/Text-Mining-R-Tidy-Approach/dp/1491981652](https://www.tidytextmining.com/tidytext)




