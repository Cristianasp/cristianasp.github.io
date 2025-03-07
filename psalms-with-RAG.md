[BACK TO INDEX](https://cristianasp.github.io)

---

# A Psalm Counselor using RAG

📅 March,  2025

Okay, so on November 2024, I took the **"5 day Generative AI Intensive Course"** from Kaggle and it was really nice to update my knowledge about what happened in 20 months since Chat-GPT4, when I wrote [this article](ml-ai-english.md).

And here is the link to the course, if you are interested:

https://www.kaggle.com/discussions/general/545082

One of the topics that I most liked was RAG (Retrieveal Augmented Generation), so now I will briefly explain it and how I made a Psalm Counselor using RAG.

## RAG

On a nutshell, RAG - Retrieval Augmented Search - was created to enable the use of general purpose LLMs to answer questions related to more specific domains or novel external data.

Chat-GPT explains us the motivation and mains activities of RAG: 

### **Motivation for RAG**

LLMs, like GPT, have a fundamental limitation:

- They rely on **static pretraining data**, which can be outdated or incomplete.
- They struggle with **domain-specific knowledge** and factual accuracy.

RAG **addresses this by allowing the model to fetch relevant documents dynamically**, rather than relying solely on what it "remembers."

### **3 Main Activities in RAG**

1. **Indexing (Preprocessing the Knowledge Base)**
    - Data sources (e.g., documents, databases, APIs) are processed into a searchable format, typically using **vector embeddings** stored in a **vector database** (e.g., FAISS, Pinecone, ChromaDB).
    - Each document is transformed into numerical vectors using an **embedding model** (e.g., OpenAI embeddings, BERT, or SentenceTransformers).
2. **Retrieval (Fetching Relevant Documents)**
    - When a user query arrives, it is also converted into a vector.
    - The system **performs a similarity search** in the vector database to find the most relevant documents.
    - These retrieved documents are then passed to the LLM as additional context.
3. **Generation (Producing the Final Response)**
    - The LLM processes the query along with the retrieved documents.
    - It generates a response that **incorporates the fetched information**, improving accuracy and reducing hallucinations.

### Use Cases of RAG

- **Customer Support Chatbots**: Answer queries using up-to-date documentation.
- **Legal & Compliance Assistants**: Retrieve legal precedents or policies.
- **Medical & Healthcare AI**: Access medical research papers for precise diagnoses.
- **Enterprise Search & Knowledge Management**: Help employees quickly find relevant internal documents.
- **Coding Assistants**: Fetch documentation or relevant code snippets dynamically.

## My Proof of Concept

I wanted to build an agent that answers questions using Psalms as inspiration.

## The data

The first step was to prepare the data. I got the Psalms from King James Bible from [this dataset](https://www.kaggle.com/datasets/kk99807/the-king-james-bible). Since the KJ Bible is in ancient modern english, I updated all the verses to modern english, with the help of Gemini and ChatGPT, you can check how I did it in [this notebook](https://www.kaggle.com/code/crisparada/psalms-translating-from-ancient-to-modern-english).

## Indexing the data into a vector database

With the dataset ready, next step was to "upload" it to a vector database. 

This is the step of transforming text data to vector embeddings, that basically are a numeric representation of the text.

For embedding, I used Google's Gemini GenAI.Embedding API with the 'text-embedding-004' model. Here is link of the documentation:
https://ai.google.dev/gemini-api/docs/models/gemini.

Regarding vector databases, I have used Chroma from Google in the GenAI course, but at the present date it's in early version and there is no cloud implementation that my app could connect to. Good news is that I already use mongoDB and I was able to launch a vector database in the free tier. 

It was very easy to embbed and ingest data into the vector database:

``` python
for text, psalm, tag in zip (documents, psalms,tags):
   embedding = embedd(text)
   collection.insert_one({ "psalm_number": psalm, "text": text, "embedding": embedding, "tag" : tag })
```

After that, I had to create the vector index. I did it manually directly in Atlas website. Basically, this is the necessary configuration:

```
"fields": [
  {
  "type": "vector",
  "path": "embedding",
  "similarity": "euclidean",
  "numDimensions": 768
  }
],
name="vector_index",
type="vectorSearch",
  ```
     

Here is the link to [MongoDB RAG with vector search documentation](https://www.mongodb.com/pt-br/docs/atlas/atlas-vector-search/rag), and by the way, there is a cool diagram about RAG:

![](https://www.mongodb.com/pt-br/docs/atlas/images/rag-flowchart.svg)

## The flow for retrieval and generation

The Psalm Counselor answers user's question if there is a psalm related to the question. If the user's question is not related to any psalm, it replies with a general answer, known as a "fallback answer".

The goal is to restrain answers to the specific domain, in this case, to psalms.

The strategy is: after querying the user's question (the embedded version, of course) to the vector database, if the query returns a low match score, the Psalm Counselor would fallback to a general answer. Deciding what is the minimum score is key to a successful counselor. I set it to 0.48

This strategy is good for not consuming Gemini's API with inappropriate or irrelevant questions.

Next step is prompting the Gemini LLM using the related psalm.

Prompting is 20% inspiration and 80% expiration. Had to try several strategies and test them to find a good instruction to Gemini. Special attention to prompt injection, people can be so creative!

Backend was ready and working. The tech stuff:
- fastapi
- motor
- mongoDB
- gemini

## Going Multilingual 

If you used any LLM, you might have noticed that they deal with languages very smoothly. They are multilingual, by design. So is the embedding model. 

I noticed that I could ask questions in different languages and the Psalm Counselor was able to give me a reasonable answer.

I made a little improvement and used a language detector to identify the language of the question. After that, I would instruct the LLM to translate his answer to the same language.  All this in the same prompt, so no extra resources used. 

To accomplish this, I used Google's mediapipe library.

https://ai.google.dev/edge/mediapipe/solutions/text/language_detector/python

## And.. a lean site.

Then came the time to make an interface so everybody could try it! And this is always the harder part for me... because ux design always takes a lot of time!

I made a one page light and lean site, using my favorite stack: 
- fastapi
- jinja templates (this is sufficient, no need of flask or django)
- middleware tunning for "not found" pages
- htmx for requests / responses using ajax
- simple cool light and clean css and html
- few javascript
- google recaptcha to prevent abuse

## Production

Pack-it-all in a docker and deploy on Heroku's eco dyno.

I usually use Alpine Linux images, but for this specific case, due to jaxlib compatibility, I had to change to a glibc-based distribution like Debian or Ubuntu image.


## 😎 The final result? I liked it!

Wanna try ? 

Here: https://www.superatrix.com

Please remember that the app is sleeping, so it make take some time to start...

## 🔎 My Conclusion:  LLMs are power without control. Agents are beautiful and the future of AI applications.

---

[BACK TO INDEX](https://cristianasp.github.io)

---