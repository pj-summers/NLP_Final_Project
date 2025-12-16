# Guitar Teacher RAG Assistant: Created by PJ Summers
Retrieval Augmented Generation (RAG) agent that uses gpt-4o-mini from OpenAI along with a corpus of task-specific documents to provide the user with reliable and trustworthy answers to questions about learning guitar.

## Domain Overview and Problem Statement
While generative AI chatbots such as ChatGPT can give overarching information on methods of learning guitar, they pull from such a wide database that results can be muddled. This is a problem that I ran into when first tryign to learn.
With this RAG agent I made sure to load it with sources that I found most helpful in my journey so that it has a more narrow vision and knowledge of guitar basics and can therefore be more helpful to a prospective beginner.

## Architecture Overview
** 1: Chunking and Vectorization **
My selected documents were chunked and tokenized using HuggingFace and DocLing before being turned into embeddings and loaded into a DuckDB vector database.

** 2: User Query **
Using the DuckDB vector database on my StreamLit app, the user is able to ask my RAG agent a question which is then embedded and tested for similarity to each chunk in my vector space.

** 3: Information Retrieval **
Based on the user's chosen k value, the top k most similar chunks to their question are used as context for a new augmented query to the OpenAI model.

** 4: Final Answer **
The model will respond with an answer backed by both OpenAI and the information gathered in the previous step to provide a clear and concise answer that cites its sources and gives rationalization for its choices with similarity scores.

## Document Collection Summary
Transcripts from Marty Music's 8 part beginner acoustic lessons series on YouTube - Marty was the most helpful teacher for me on YouTube so I wanted to include a lot of his methods
Text files pulled from Play Guitar Academy's website's 6 part series on how to learn guitar scales - This is a route that I did not take when learning but was told by many was a good way to begin so I wanted to include a little bit of a different approach to see how it paired with the rest
HTML file from a discussion board about the best methods to learn guitar - Discussion boards like Reddit and Quora were super helpful for me because it gives you a wide array of opinions to filter through 
5 PDFS discussing the history of teaching, new state of the art methods, and comparisons between different methods over time - These are long and heavily researched documents that aim to find out the single best way to learn guitar so I thought they would be super helpful for this agent

## Agent Configuration Details 
Role: Beginning guitar teacher
Goal: Answer questions about how to learn to play guitar using the database
Backstory: You are an experienced teacher who has access to a database with content about the best ways to begin learning to play guitar

I chose these three definitions for my agent because I wanted to be precise and simple. I did not want to overexplain my agent its role and force it to fit into whatever box that may have created.
Instead I gave it very concise instructions about exactly who it was and what it should expect to do for me. In the backstory I made sure to put experienced teacher rather than guitar expert due to the fact that I feel as though an expert cna sometimes overlook the basics, but an experienced teacher would specialize in them.

## Usage Instructions 
To use this agent you simply need to have an OpenAI API key, which can be found here https://platform.openai.com/api-keys
Once you have your API key, go to the following link to run my StreamLit app! 

## StreamLit Link
https://pj-summers-nlp-final.streamlit.app/
