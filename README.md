## SCRIBE
**S**anta Clara
**C**ollections
**R**ealtime
**I**ntelligent
**B**ook
**E**ngine

## Inspiration
We were inspired primarily by several classes we took that dealt with the history of the University and the Ohlone people. Many of these classes involved visits to Archives and Special Collections, a criminally underutilized resource that hosts digitized documents pertaining to SCU's history. Our goal with this project is to make Santa Clara's history more easily accessible and to provide an organized, interactive way to engage with the wide array of data housed in our library. There is a lot to be learned from the past; knowledge is power, after all, so why should we not try to leverage it to the best of our ability?

## What it does
A chatbot interface allows users to ask questions pertaining to documents in Archives and Special Collections or SCU's history, with responses informed by primary sources located in the archives, as well as links to the documents, artifacts, or images. _SCRIBE will always return source-based responses, and never hallucinate answers, which sets it apart from standard LLMs such as ChatGPT._

## How we built it
Retrieval Augmented Generation (**RAG**) is used to feed the LLM context about the user's prompt. RAG, generally, is the process of creating a **vector embedding** for each entry in a collection of data (in this case, embedding the text, dates, transcriptions, etc. for Archives and Special Collections). These vector embeddings are stored with each entry in a MongoDB database. When a user prompts our chatbot, we embed their prompt, and use the embedding vector to search our database to find relevant documents, which are then fed to the LLM to respond with. This way, the user can engage conversationally with an LLM, with the specific context of the digitized content in Archives and Special Collections.
The application is a **React** web app that utilizes API calls to a back-end **Flask** server to handle queries and display responses. The Flask server performs a MongoDB **vector store similarity search** to find the most relevant documents, and pings an **OpenAI API** to generate a response based on the documents.

## Challenges we ran into
A lot of **LangChain's** APIs were recently deprecated, so trying to navigate the new documentation without many concrete examples was a challenge. Also, figuring out how to pass the relevant documents into the established context for the LLM API was a bit tricky. 

## Accomplishments that we're proud of
It works extremely well! We can ask the bot specific questions and it will respond with relevant information (assuming said information is in its database to begin with). It also cites sources and provides links to the Archives and Specials Collections website for each source.

## What we learned
We learned a lot about RAG, how to embed text into vectors, React and Langchain, and how to connect all of those together to work in tandem to deliver conversational-style messages.

## What's next for SCRIBE
RAG makes it easy to add more data to the vector-embedding database. All that needs to be done is formatting and embedding the new data and adding it to the current database. Ideally, we could begin to add more Archives and Special Collections (or other SCU-related documents) as new transcriptions are added and expand the range and versatility of our model. The scope of this project is truly unbounded. SCRIBE is a tool that could serve thousands of libraries, museums, and institutions around the world. It's extremely scalable, and can be easily adapted to the document set of any institution.
