
## NU-Volunteers --> Natural Language Processing Tool built for our app's database

My team, Engage, won the annual ,renown and invite-only, Institute of Electrical and Electronic Engineers competition held this year, 2025 at Northwestern in Chicago. 

Our winning project was an application focused on recommending volunteer opportunities to students in our local Evanston area using ML tools and Natural Language Processing (NLP) algorithms to parse volunteer opportunities and match them to student profiles.


## Languages/Tools/Frameworks
- Python
- Supabase
- PostgreSQL
- KeyBERT
- TF-IDF (natural language processing)
- Pandas
- scikitlearn
- numpy
- supabase-py
  

## How it works
I built two models of NLP - KeyBERT and TF-IDF and which we incorporated in the application.

### Data fetching
- I used Python, due to its object-oriented properties, for Object Relational Mapping.
- Created a Supabase client that used SQL queries and Pandas data frames to fetch data from the PostgreSQL database

### Data preprocessing
#### TF-IDF
- Vectorized the words from the volunteer posting using TfidfVectorizer from scikit-learn to build a 'vocabulary' for the model.
- Computed the weight of the words using the TFIDF count

#### KeyBERT
- Words from the volunteer posting are encoded to tokens and mean-pooling is applied to produce a dense vector embedding.
- Using KeyBERT frameworks, candidate keywords are generated and hte document embedding and candidate keywords are compared via _cosine similarity_ to get the words that are the most representative of the text.

### Matching
- User profile is also encoded similarly into an embedding.
- The top K volunteeer opportunities that match this profile are returned.


## Example Usage
### Initialize with Supabase client
recommender = VolunteerRecommender(supabase)

### Fetch and preprocess job data
recommender.fetch_data()

### Fit embeddings on opportunities
recommender.fit()

### Build a user profile embedding
user_embedding = recommender.build_user_profile(user_id=123)

### Get personalized recommendations
recommendations = recommender.recommend_for_user(user_embedding, top_n=5)
