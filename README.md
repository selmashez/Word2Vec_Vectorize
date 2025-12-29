Word2Vec Fun with Fake News 
Hey there This is a simple project where I played around with the Word2Vec model to see how it turns news articles into vectors. I used the WELFake dataset for this.

I wanted to see if I could visualize how words like "President" or "Market" are related to each other in the world of news. So, I vectorized the words using Word2Vec and then "squashed" them into a 2D map using PCA so we can actually see them on a plot.

A note on Preprocessing
I used simple_preprocess from Gensim because, honestly, I didn't want to get stuck in the rabbit hole of heavy cleaning (like removing stop-words or stemming). My main goal here was just to see Word2Vec in action in the simplest way possible.

🛠 My Settings
Library: Gensim (Word2Vec)

Vector Size: 50 (trying to keep it lightweight)

Window: 5 (after some testing, this gave better results)

Epochs: 20

Challenges (The "Annoying" Part)
The Warning Wall
While training the model, I kept getting these super long and annoying "Exception ignored" messages in my notebook. They weren't errors, but they were making my notebook look like a mess.

I tried import warnings; warnings.filterwarnings('ignore') -> Didn't work.

I tried changing the logging levels -> Still didn't work.

The Fix: I ended up using the %%capture magic command at the top of the cell. Why? Because those messages were coming from the low-level C++ code (Cython) that Word2Vec uses. Standard Python warning filters can't catch those, but %%capture just tells the notebook to "shut up" and hide everything that comes out of that cell. It worked like a charm!

Semantic Alignment
At first, the vectors for similar words were a bit all over the place. I increased the window size, and the results improved. It turns out that giving the model a bit more "room" to look at surrounding words makes it much smarter.

 What's next?
This was just the warm-up! In my next projects/repos, I’m planning to use these vectors to build a Classifier that can actually tell if a news story is Real or Fake. This was just me getting to know the vectors.
