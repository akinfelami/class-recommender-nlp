# course-recommender

#### An NLP based model that recommends courses from Cornell University, Ithaca NY.

The model predicts other courses a user might like based on a course title or keywords. it is trained on a word2Vec model using course descriptions scraped from [here](https://classes.cornell.edu/).

#### Features

- improved using  a slim version of google's pretrained word2vec model 
- recommend courses based on course title
- recommend courses based on keywords

#### Things to Note

- dataset is available in `catalog.pkl`, while `model.pkl` is the trained model. `vectors.pkl` is the sentence vectors determined by taking the average of the vectors of words in a sentence but weighted using their tf idf vectors
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
