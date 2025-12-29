# pydanticai_RAG

🚀 PydanticAI-RAG Assistant (Snapp Internal Knowledge Q&A)This project implements an advanced RAG (Retrieval-Augmented Generation) system designed to provide fast, accurate, and fact-based answers from an internal knowledge base (Snapp data). It leverages the Gemini 2.5 Flash model (as the intelligent core) and integrates Supabase/Cloudflare for vector storage and embedding generation.The core innovation lies in the chained tool execution and the optimized statistical data retrieval to ensure high precision even for ambiguous or numerical queries.

✨ Key FeaturesChained Tool Execution: The system uses a two-step process:
Query Rewriting (Tool 1): Gemini refines the user's potentially vague input into 1-3 highly specific Farsi search queries.
Vector Retrieval (Tool 2): Executes the search on the Supabase vector store.Optimized Statistical Retrieval (The Fix): The Agent is instructed to explicitly include Farsi keywords like تعداد (Count) or آمار (Statistics) in its rewritten queries for numerical questions. This strategy, combined with a lowered similarity threshold ($0.4$), ensures retrieval of concise statistical data points that might otherwise be filtered out.Conversational Memory: Maintains short-term memory (history context) to support follow-up questions and conversational flow within a session.
Farsi Constraint: All final outputs and responses from the LLM are strictly enforced to be in Farsi (فارسی).High Stability: Utilizes Pydantic for validation of settings and tool outputs, alongside robust error handling and JSON parsing fallbacks.

🛠️ PrerequisitesTo run this project, you need the following API keys and services configured:Gemini API Key: Access key for Google's Gemini models.Supabase: URL and Service Key for the PostgreSQL database with the pg_vector extension (the vector store).Cloudflare AI Gateway: API Token and Account ID to utilize their Embedding models (e.g., @cf/baai/bge-m3) for query vectorization.
