# course-recommender

#### An NLP based model that recommends courses from Cornell University, Ithaca NY.

The model is trained on a word2Vec model using course descriptions scraped from [here](https://classes.cornell.edu/).

#### Features

- improved using google's pretrained model that includes word vectors for a vocabulary
  of 3 million words and phrases that they trained on roughly 100 billion words from a Google News dataset.
- recommend courses based on course title
- recommend courses based on keywords

#### Things to Note

- dataset is available in `catalog.pkl`, while `model.txt` is the trained model, I have added `model.txt` to gitignore because it is too large (about 7GB)
- to load dataset:

  ```
  import pickle
  with open('/path/to/catalog.pkl', 'rb') as f:
    df= pickle.load(f)
  ```

- There are a couple of courses with the same name but from different departments. I did not drop duplicates so as not to introduce any bias for departments.

- change the number of courses recommended
  - in `recommend_from_keyword(keyword)` function, change the value `10` to any number < `4619` e.g `top_recommendations = np.argsort(avg_scores)[::-1][:50]`
  - in `recommend_from_title(title)` change index range from the line ` sim_scores = sim_scores[1:11]`
- make sure title in `recommend_from_keyword(title)` a valid title in dataset but keyword from `recommend_from_keyword(keyword)` can be any english word or phrase
- Interactive UI coming soon

I had fun making this. I'm open to questions/feedback or contributions
