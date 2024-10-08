## Some fun with textProjection plots

A while ago I discovered a great package for R called 'text'. One of the main advantages of this package is that it tunnels into python to obtain advanced contextualized word embedding models like BERT from the huggingface library. These contextualized embedding models are distinguished from static embeddings like GloVe or text2vec by their use a mechanism called "self-attention" to understand word meanings based on detailed information about the context in which they appear. 
Static embeddings develop a global vocabulary of all terms within the corpus, obtaining one vector representation for each word. Contextualized embeddings are sensitive to the fact that identical words can have different meanings, and that these meanings are tied to their usage within a sentence. The resulting embeddings matrix will distinguish between the word "bow" used in this context "he was shot with a bow", this context "the bow of the ship", and this context "he bowed to the emporer". 


Another cool thing about this package is its functions to compute the relationships between words and the document (e.g., textCentrality), words and other words (e.g., cosine) and words and a binary or continuous meta-data variable (e.g., textProjection). The data in my lab tends to have a lot of accompanying meta-data, so I wanted to test the textProjection function. Individual differences variables like personality traits and demographics like age and gender really lend themselves to textProjection. For example, we can examine how the language people use varies in relation to a their gender or degree of neuroticism. Another way of using this technique is to look at how words vary not between individuals, but between years or historical periods. One might be curious to know what kind of words are predictive of a pre versus post-9/11 campaign speech. Yet another approach is to examine the association between words and some kind of external classification system. For example, in humor research we might correlate the words in people's jokes with an ordinal rating of how funny their joke was. There's many possibilities. 


I thought I'd start simple and have a crack at one binary textProjection plot, and one continuous textProjection plot. For the binary text projection, I grabbed an existing online dataset that contains film dialogue and meta-data on the gender of the character speaking, cleaned it up somewhat haphazardly (i.e., liberal use of drop.na), and then computed, preprocessed, and projected the word embeddings across character gender. The results are shown in Figure 1.

**Figure 1.**

*Association Between Film Dialogue Words and Character Gender*
![344058234-9600fb08-0226-4924-982f-70cccd2d4e3c](https://github.com/user-attachments/assets/19d2ff63-1fcd-4c30-a666-12617ecb66aa)

We end up with some pretty interesting results. Words associated with women are uniformly positive and almost entirely romance and family related. In contrast, words associated with men are mostly nouns related to male-dominated forms of work. I would characterize these male words as a combination of military, maritime, and logistics terminology. There's also "grape", which I have no theory on. As with any analysis, it's important to consider the limitations of the data** before making inferences about the results. Nevertheless, these word associations are approximately in line with what we might expect. No single concept ties all male speech together (maritime/military was my best guess), but it is clearly diffentiated from female speech by word emotionality and also word type. Male words are mostly valence-neutral nouns, while female words are mostly positive adjectives. This comparison paints a picture of men in film participating in the workforce, discussing things like the 'cartel', 'business', and 'airspace', and women in film in the home, revealing their feelings ('happy', 'sad', 'romantic') and announcing pregnancies and marriages. 


Now let's look at a different dataset, and project words across a continuous variable. I took some data that my lab had in storage: people's open-ended responses to what are called 'joke stems' tasks. These joke stems are basically ways of prompting participants to make jokes. My corpus is people's responses to a specific joke stems task in which participants imagine that a friend invited them over for dinner, cooked a really disgusting meal, and then asked them how the food was. Responses were things like "it was so bad, a dog wouldn't eat it". I had about 1600 responses, with each response (i.e., joke) averaging in length about 13 words. As before, I computed and preprocessed the embeddings. I then projected them across age - how old the person who made the joke was. The results are shown in Figure 2.

**Figure 2.**
*Association Between Joke Words and Age*
![zoomerplotAgeEmbeddings](https://github.com/user-attachments/assets/6f515e21-64d8-489f-9055-caf79d11b033)


I was tickled by this plot, particularly the text associated with the "young" side of the age range. I interpreted this plot from a generational perspective - these are jokes that young people are making, not necessary because they're young, but because they reflect the humor trends of their time. Of course, there is a *lot* of researcher degrees of freedom here, but I tend to agree that "um", "wow", and "uhh" are indeed representative of Gen-Z humor. Another thing we notice is that older participants seem to be drawing upon a "dog" theme in their jokes about the gross food. Again, this could be a generational effect, it could be a direct result of age and maturity, or it could be because older participants just wanted to get the joke prompt task over and done with and didn't care about actually making an original joke. "A dog wouldn't eat it" and its variations are probably the first thing that occurs to many people, and if you just want to submit your survey to Prolific and get paid, perhaps you tend to go with this instinct. Again, these results are open to a great deal of interpetation, I'm just speculating.


Well, that was fun and educational. I don't think anyone will read this, but I hope someone got a kick out of my plots. As an R user who is slowly learning Python, I think there is a great deal of value in a package like text which allows people who aren't familiar with Python to accces some of its functionality. I really look forward to reading the publications that come of this package.

-Meriel


*This is just an exercise in text analysis for the purpose of fun and learning a new package. I'm not actually drawing any empirical conclusions. 

**The original film dialogue corpus had lines from 617 films. I excluded all lines from films released before 1960, bringing the total down to 512 films. I then collapsed lines of dialogue into characters, so all dialogue related to a given character in a given film was combined into a single row. Rows that did not have a gender were dropped. The result was 2434 individual characters, who each spoke an average of 756 words. There were obviously far more than 512 films released between 1960 and 2009 (the most recent film in the dataset), so this is far from a comprehensive sample. The data is instead compiled of films for which scripts and IMDB data are publically available, so it suffers from pretty significant retrieval bias (Grimmer et al., 2022). Additionally, the absence of a gender identifier may have varied systematically with other factors, so dropping all cases without gender may have introduced some additional bias. All told, we can conclude that my data is skewed in some predictable and some unpredictable ways. 
This pattern could be occurring for several reasons, aside from that they indicate a tendency for films to represent women in somewhat antiquated social roles. For instance, it may be that a higher proportion of female characters are found in romantic movies, in which case my finding would be more a reflection of gender differences in films genres and less a reflection of gender differences in dialogue. That particular hypothesis doesn't seem likely, as about 6% of male characters compared to 8% of female characters were in films with 'romance' listed as the primary genre. Negligible differences were also observed in other potentially mediating genres like drama (17% male, 19% female) and sci-fi (6% male, 5% female). That being said, it would be interesting to look at gender differences in film dialogue within a single genre or maybe with a larger or more recent sample of films. However, I think my poor laptop is tired of computing embeddings for now, so I'll leave all that for a later date. 

Kjell, O., Giorgi, S., & Schwartz, H. A. (2021). *The text-package: An R-package for Analyzing and Visualizing Human Language Using Natural Language Processing and Deep Learning*. OSF. https://doi.org/10.31234/osf.io/293kt

Grimmer, J., Roberts, M., Stewart, B. (2022). *Text as Data: A New Framework for Machine Learning and the Social Sciences*. Princeton University Press.





