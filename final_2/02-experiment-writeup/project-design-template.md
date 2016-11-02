# Project Design Writeup and Approval Template

Follow this as a guide to completing the project design writeup. The questions for each section are merely there to suggest what the baseline should cover; be sure to use detail as it will make the project much easier to approach as the class moves on.

### Project Problem and Hypothesis
* What's the project about? What problem are you solving?
* Where does this seem to reside as a machine learning problem? Are you predicting some continuous number, or predicting a binary value?
* What kind of impact do you think it could have?
* What do you think will have the most impact in predicting the value you are interested in solving for?

This project is about tagging news/blog articles with appropriate content tags. Article tags can be used to make recommendations of new articles to users who read articles with the same tag. Currently the articles are tagged manually by an editor. I would like to train a classifier to predict what content tags a given article should have. This would be useful if it could eliminate the task of manually tagging articles. It might also include tags the editor may have missed, which could lead to better recommendations for users. 

I believe the name of the author, the author's profession/title, length of the article, the words used in the article, and the order of the words (n-grams) might be useful features for accurately predicting tags.

### Datasets
* Description of data set available, at the field level (see table)
* If from an API, include a sample return (this is usually included in API documentation!) (if doing this in markdown, use the javacription code tag)

I will be scraping article data (including text, author info, published date, and tags) from the OPEN Forum website (https://www.americanexpress.com/us/small-business/openforum/explore/). I'm still in the process of setting up the scraping with BeautifulSoup so I haven't decided on precise fields yet.'

### Domain knowledge
* What experience do you already have around this area?
* Does it relate or help inform the project in any way?
* What other research efforts exist?
    * Use a quick Google search to see what approaches others have made, or talk with your colleagues if it is work related about previous attempts at similar problems.
    * This could even just be something like "the marketing team put together a forecast in excel that doesn't do well."
    * Include a benchmark, how other models have performed, even if you are unsure what the metric means.

This article discusses using nearest neighbors to recommend post tags. It analyzes how similar posts are through a method called tf–idf. I will most likely use this text analysis approach.
(https://medium.com/data-lab/how-we-used-data-to-suggest-tags-for-your-story-a120076d0bb6#.n08nlgol1)

Scikit learn has a tutorial on text processing so I might use some of those techniques for representing my text as a feature. 
(http://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html).

### Project Concerns
* What questions do you have about your project? What are you not sure you quite yet understand? (The more honest you are about this, the easier your instructors can help).
* What are the assumptions and caveats to the problem?
    * What data do you not have access to but wish you had?
    * What is already implied about the observations in your data set? For example, if your primary data set is twitter data, it may not be representative of the whole sample (say, predicting who would win an election)
* What are the risks to the project?
    * What's the cost of your model being wrong? (What's the benefit of your model being right?)
    * Is any of the data incorrect? Could it be incorrect?
    
I plan on training a classifier on the features and Y values (tags) of my training dataset.
A concern is there are a LOT of possibilities for the article tags, and articles can have more than one tag. So determining the accuracy might be difficult if the classifier is able to predict some of the tags correctly but not all. 

The risk is adding tags that definitely do not belong on an article. Then we end of recommending articles that users might have no interest in. Another risk is not adding tags that definitely should be added. Then we lose out on recommending an article to someone who might enjoy it. We want to minimize both these risks. But we'll still have someone reviewing the tags so it's not incredibly important - maybe the tags could be presented as suggested tags while the editor is reviewing the articles. 

### Outcomes
* What do you expect the output to look like?
* What does your target audience expect the output to look like?
* What gain do you expect from your most important feature on its own?
* How complicated does your model have to be?
* How successful does your project have to be in order to be considered a "success"?
* What will you do if the project is a bust (this happens! but it shouldn't here)?

I expect the outcome for a single article input to be an array of tag names, perhaps with a percentage of how strongly the tag is associated with the article. 

My target audience (the people that own the website) would expect to provide an article and get back accurate content tags that apply to that article. I feel the text of the article to be the most important feature in determining the correct tags.

If the project is a complete bust, I will move on to plan B. If the reason is due to my dataset - then I might be able to use the news article dataset mentioned in the scikit learn tutorial. 
