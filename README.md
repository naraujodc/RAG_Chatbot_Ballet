# Classical Ballet RAG Assistant

<p align="center">
<a href="https://balletchat.streamlit.app"><img alt="Classical Ballet RAG Chatbot" src="https://img.shields.io/badge/Classical%20Ballet%20RAG%20Chatbot-ffdce8"/></a> &nbsp;
</p>

![Python](https://img.shields.io/badge/-Python-ffe873?style=flat&logo=python)&nbsp;
![Streamlit](https://img.shields.io/badge/Streamlit-ececec?style=flat&logo=streamlit)&nbsp;
![crewAI](https://img.shields.io/badge/crewAI-2a7e75?style=flat&logo=crewai)&nbsp;
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai)&nbsp;
![DuckDB](https://img.shields.io/badge/DuckDB-CC6600?style=flat&logo=duckdb)&nbsp;
![Sentence Transformers](https://img.shields.io/badge/Sentence--Transformers-4A73E8?style=flat&logo=huggingface)&nbsp;
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy)&nbsp;
![Docling](https://img.shields.io/badge/Docling-00BFFF?style=flat&logo=markdown)&nbsp;

## Table of Contents
[1. Description](#description)\
[2. Domain Overview and Problem Statement](#domain-overview-and-problem-statement)\
[3. Retrieval-Augmented Generation Pipeline](#retrieval-augmented-generation-pipeline)\
[4. Document Collection Summary](#document-collection-summary)\
[5. Agent Configuration Details](#agent-configuration-details)\
[6. Installation and Setup Instructions](#installation-and-setup-instructions)

## Description
This project is an interactive chatbot powered by retrieval-augmented generation (RAG) to provide accurate, context-specific answers about classical ballet. The core of this system is an AI agent that can search a specialized vector database built from curated content covering ballet history, styles, repertoire, and important figures.

Essentially, the agent **retrieves** content related to the user's query from its curated database. It then uses that content to **augment** the original prompt and send it to an LLM (here, GPT-4o-mini) to **generate** a more informed response.

In the app's main chat area, users can:
- Type any question related to classical ballet.
- Choose from one of the *Example Questions* to instantly submit it.
- View the sources retrieved by the agent from the database.

In the app's sidebar, users can:
- Insert an OpenAI API Key. **This is necessary for the use of the app and the key is kept secret.**
- Test different numbers of **Results per Query**: This defines how many chunks of text are retrieved from the database in a single search. 
- Test different numbers of **Max Tool Calls**: This determines the number of times the agent can call the database search tool for a single user query.

<p align="center">
<img src="https://github.com/naraujodc/RAG_Chatbot_Ballet/blob/main/images/RAG_Ballet_Chatbot_Usage.png">
Screenshot of the chatbot after sending a sample question
</p>

## Domain Overview and Problem Statement
Classical ballet is a form of art that has faced the test of time and continues to marvel audiences all over the world. While repertoire created centuries ago such as *The Nutcracker* and *Swan Lake* remain as the icons of ballet, this is a dynamic art form that continues to evolve and bring out new methods and forms of artistic expression and athleticism.

I grew up dancing classical ballet and remain a passionate fan of this beautiful dance style and its adjacents, such as neoclassical ballet. My formation followed the Royal Academy of Dance (RAD) method, which &mdash; as you can learn from the chatbot &mdash; is centered around a structured curriculum and involves not only technical mastery, but also studies about human anatomy and the history of ballet. 

The history of classical ballet is complex, surprising, and fascinating. However, I noticed that obtaining information about the history of ballet, as well as its main figures and repertoire online is not a simple task. Sources are dispersed and often incomplete, making it difficult to gain a full perspective of a topic of interest through a simple search.

Thus, I decided to create this chatbot as a way to centralize reliable information about classical ballet in a database that can be searched by an AI agent to generate complete, comprehensive answers to specific questions informed by several sources.

## Retrieval-Augmented Generation Pipeline
The diagram below illustrates the process of creating the vector database from the domain-specific documents (in gray) as well as the RAG pipeline that starts when the user sends a question/query into the chat (in pink).

<p align="center">
<img src="https://github.com/naraujodc/RAG_Chatbot_Ballet/blob/main/images/RAG_Pipeline_Diagram.png">
Diagram of the database creation (gray) and RAG pipeline (pink)
</p>

*Note:* The conceptual RAG pipeline diagram was inspired by the framework presented in the Gradient Flow article, [*Best Practices in Retrieval-Augmented Generation (RAG)*](https://gradientflow.substack.com/p/best-practices-in-retrieval-augmented).

## Document Collection Summary
The Classical Ballet RAG Assistant was built upon a curated collection of materials, ensuring specialized knowledge across history, technique, and repertoire.

### Historical and Contextual Web Articles

These sources provide foundational knowledge on the origins, cultural significance, and general history of ballet.

* **Wikipedia** &mdash; [*History of ballet*](https://en.wikipedia.org/wiki/History_of_ballet)
* **Mental Floss** &mdash; [*The Art of Power: How Louis XIV Ruled France… With Ballet*](https://www.mentalfloss.com/article/93297/art-power-how-louis-xiv-ruled-france-ballet)
* **NPR** &mdash; [*Interview with historian Jennifer Homans, author of Apollo’s Angels: A History of Ballet*](https://www.npr.org/2010/12/13/132023182/the-tutu-s-tale-a-cultural-history-of-ballet-s-angels)
* **The Grand Theatre** &mdash; [*Different Types of Ballet*](https://www.blackpoolgrand.co.uk/different-types-ballet)
* **Wikipedia** &mdash; [*Ballet*](https://en.wikipedia.org/wiki/Ballet)
* **Learn to Dance** &mdash; [*Ballet terms explained*](https://www.learntodance.com/online-ballet-dance-lessons/)

### Repertoire and Narrative Guides

Sources focused on specific ballets, structure, and classification (e.g., romantic, narrative, *d'action*).

* **MasterClass** &mdash; [*10 Famous Ballets*](https://www.masterclass.com/articles/famous-ballets-guide)
* **Dance Plug** &mdash; [*10 Classical Ballets Any Kind of Dancer Should Know*](https://www.danceplug.com/article/10-classical-ballets-any-kind-of-dancer-should-know)
* **Wikipedia** &mdash; [*List of ballets by title*](https://en.wikipedia.org/wiki/List_of_ballets_by_title)
* **Wikipedia** &mdash; [*Ballet d’action*](https://en.wikipedia.org/wiki/Ballet_d%27action)
* **Wikipedia** &mdash; [*Narrative ballet*](https://en.wikipedia.org/wiki/Narrative_ballet)

### YouTube Videos, Documentaries, and Expert Interviews

Transcribed content from videos covering history, prominent figures, and stylistic explanations.

* **BBC Documentary** &mdash; [*The King Who Invented Ballet: Louis XIV and the Noble Art of Dance*](https://youtu.be/NTJIlFhg85Q?si=Q8W2CzrGZxOHF8Tq)
* **Lucasfilm** &mdash; [*Ballet: The Art of Dance \| Historical Documentary*](https://youtu.be/-b3z8Rk0zH8?si=17wU4agcEmXMwg2e)
* **Ballet Reign** &mdash; [*Ballet Styles Explained: Which One is Right for You?*](https://youtu.be/4bS9RM70Mdk?si=UxwBF0VMJJOXSVba)
* **Ballet Reign** &mdash; [*Ballet Legends: The Greatest Historical Dancers You Need To Know*](https://youtu.be/ohcq4Qj37ok?si=RayI7cN4yKzDtdKP)
* **Kathryn Morgan** &mdash; [*6 Ballet Composers You NEED To Know*](https://youtu.be/4MsTBMhaa2g?si=AurnQYgzOgPenIAF)

### Academic Papers and Books

Peer-reviewed or professionally published documents offering in-depth analysis.

* **Garafola, Lynn** &mdash; [*The Travesty Dancer in Nineteenth Century Ballet*](https://www.cambridge.org/core/journals/dance-research-journal/article/travesty-dancer-in-nineteenthcentury-ballet/E412940D55F97D6CD5355FEBFF5E60F2)
* **Schimmelpfennig, Jörg** &mdash; [*Ballet*](https://repub.eur.nl/pub/781/TOWSE%20EBOOK_pages0097-0102.pdf)

## Agent Configuration Details
To create a powerful agent built specifically for this task, I had to assign a *role*, a *goal*, and a *backstory* to it.

- **Role:** "Classical Ballet Content Assistant" &rarr; This defines the identity of my agent. I kept it simple and straightforward to indicate the domain of focus and characterize the agent as a content assistant, guiding it to focus on answering with the retrieved sources.
- **Goal:** "Answer questions about classical ballet using the database." &rarr; This sets out a clear goal to provide answers to domain-specific questions, again reinforcing the idea that the database should be used to inform those answers.
- **Backstory:** "You are an expert who has access to a database with content about classical ballet." &rarr; This context evokes expertise from the agent, which has been shown to improve the quality and accuracy of LLM responses. Once again, the agent's capability to retrieve information from the database is highlighted.

## Installation and Setup Instructions
The app has been deployed and can be accessed with the URL below. To use the app, simply visit the following link:
<p align="center">
<a href="https://balletchat.streamlit.app"><img alt="Classical Ballet RAG Chatbot" src="https://img.shields.io/badge/Classical%20Ballet%20RAG%20Chatbot-ffdce8"/></a> &nbsp;
</p>

If you want to download and run the code yourself, follow the instructions below:
1. Install Anaconda.
2. Clone this repository and cd into it.
```
git clone https://github.com/naraujodc/RAG_Chatbot_Ballet

cd RAG_Chatbot_Ballet
```
3. In a new environment, install the dependencies.
```
conda activate new_env

pip install -r requirements.txt
```
4. In the terminal, make sure you are in `RAG_Chatbot_Ballet`. If not, cd into it.
5. In the terminal, run the app on Streamlit.
```
streamlit run app.py
```
