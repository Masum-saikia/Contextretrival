1. RAG is a method that retrieves relevant information from a knowledge base and appends it to the user's prompt, significantly enhancing the model's response. Problem arises because Traditional RAG remove context during encoding.
2. One of the solution to this problem is if the knowledge base is smaller we can just include the entire knowledge base in the prompt that you give the model, with no need for RAG or similar methods. We can use prompt caching to it.
3. Prompt caching works in the following ways, firstly,The system checks if the prompt prefix is already cached from a recent query, then if foun, it uses the cached version, reducing processing time and costs, otherwise it processes the full prompt and caches the prefix for future use.
4. This is useful for prompts with many example, large amounts of context or background information , repetative taks with consistent instructions, Long multi-turn conversations
5. Pipeline of basic RAG model:Convert the documents into small chunks .
Convert the small chunks in to TF-IDF encodings and semantic embeddings and store them into vector db.
Take input query and convert it into TF-IDF encodings and semantic embeddings and using embeddings search it in vector db to find top k chunks
We create a prompt template with the help of query and top k chunks
6. We feed it to the generative llm to generate the answer
7. RAG system that uses both embeddings (BM25) to retrieve information. TF-IDF measures word importance and forms the basis for BM25.
8. Contextual Retrieval:
9. PREPROCESSING: here we take each chunk feed that into a template prompt which helps in locating the chunk in the document and add contextual document to that specific chunk
Rest of the process is same hai standard RAG model 
We can further boost the performance of the model with reranking feature:
Where the top k chunks, are passed witht the user’s query throught the model , and the model re ranks the top k chunks based on there relevance score and importance to the prompt

Performance improvement : Reranked Contextual Embedding and Contextual BM25 reduced the top-20-chunk retrieval failure rate by 67%
