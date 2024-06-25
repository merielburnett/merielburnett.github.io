## How film dialogue varies depending on character gender

A little while ago I discovered an incredible package for R called 'text'. The functions in this package are a significant upgrade from the tidytext methods I was using previous, allowing for some very cool text analysis methods. For one thing, text has a function to generate plots that show words in relation to a given binary or numeric variable. Individual differences variables like personality traits and demographics really lend themselves to these kind of analyses. For example, we can examine how the language people use varies in relation to a their gender or degree of neuroticism. Another way of using this technique is to look at how words vary not just between individuals, but across time. One might be curious to know what kind of words are characteristic of a pre versus post-9/11 campaign speech. Yet another approach is to examine the association between words and some kind of external classification system. For example, in humor research we might correlate the words in people's jokes with an ordinal rating of how funny their joke was. There really are endless possibilities. 

So, to learn the ropes of this package, I thought I'd start simple and have a crack at examining the relation between gender and words in film dialogue. I wanted to know: how do male versus female characters speak in movies? I grabbed a pre-compiled corpus off of kaggle (link here), cleaned it up somewhat haphazardly (i.e., liberal use of drop.na), and then computed, preprocessed, and projected the word embeddings across character gender. The results are shown in Figure 1.

Figure 1. 
Association Between Film Dialogue Words and Character Gender
![gender](https://github.com/merielburnett/merielburnett.github.io/assets/171220833/5405834d-d8f5-4247-9467-463175a664f1)
Note: As you can see, I didn't remove stop-words like 'the' and 'to'. Gender was coded as Male = 0, Female = 1. Although text automatically plots the focal variable into quartiles (numbers on the x-axis represent standard deviations from the mean), it maintained the binary structure of gender making these quartiles meaningless. 

We end up with some pretty interesting results. Words related to shipping and logistics (e.g., 'bulk', 'exports', 'shipment', 'galley') are associated with male characters, while simple and non-specific terms (e.g., 'yes', 'me', 'you', 'maybe', 'please') are associated with female characters. As with any analysis, it's important to consider the limitations of the data** before boldly interpretating the results. Nevertheless, these results are 







**The film dialogue corpus I downloaded had lines from 617 films. I excluded all lines from films released before 1960, bringing the total down to 512 films. I then collapsed lines of dialogue into characters, so all dialogue related to a given character in a given film was combined into a single row. Rows that did not have a gender were dropped. The result was 2434 individual characters, who each spoke an average of 756 words. There were far more than 512 films released between 1960 and 2009 (the most recent film in the dataset), so this is far from a comprehensive sample. The characters who got dropped for having '?' in place of a gender identifier may have varied systematically with other factors, like film genre or popularity. The resulting dataset is biased in some predictable and unpredictable ways. 





