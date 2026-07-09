
**3-Min Loom Script**
“Hi, this is my Session 10 LLM Servers homework.

For this assignment, the original instructions used Fireworks AI with `gpt-oss-20b`. The setup document gives two choices: a serverless endpoint or a dedicated on-demand deployment. I chose the serverless route because the dedicated endpoint was optional, and I wanted to avoid provisioning GPUs or accidentally leaving paid infrastructure running.

I used Together.ai as my hosted serverless provider. In my notebook, I loaded my API configuration from `.env`, including the Together API key, base URL, chat model `openai/gpt-oss-20b`, and the only available embedding model in Together's API `intfloat/multilingual-e5-large-instruct`.

First, I tested a single request with LangChain’s `ChatOpenAI`, pointed at Together’s OpenAI-compatible API. The model responded successfully, but the first call took about 9.6 seconds. That showed the endpoint worked, but also that serverless latency can be noticeable.

Next, I ran concurrent requests to test throughput and latency. In one run, multiple requests completed in about 12 seconds total, with individual requests ranging from around 3 seconds to around 12 seconds. This showed that concurrency worked, but response times varied. That variability is an important tradeoff of serverless inference: it is easy to use, but shared capacity can cause queueing or uneven latency.

The main concept I learned is the difference between serverless and dedicated endpoints. Serverless is convenient because I only need an API key and model name. I do not manage GPUs, containers, scaling, or shutdown. Dedicated endpoints reserve compute, so they can be more predictable for production traffic, but they cost more and require more operational care.

I also learned why token throughput matters. Throughput is how quickly a model processes input tokens and generates output tokens. For a user-facing RAG app, low throughput means users wait longer, especially when the prompt includes retrieved context. Higher throughput supports better latency and more simultaneous users.

My next step is to connect this provider configuration to the RAG application, using the hosted chat model for generation and the embedding model for retrieval.”

That should land around 2.5 to 3 minutes if spoken calmly.