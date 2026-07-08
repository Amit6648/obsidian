# RAG & Obsidian Architecture Planning

This note serves as your expandable planning space for integrating RAG (Retrieval-Augmented Generation) with your Obsidian second brain, based on the Excalidraw design. Click on any section below to expand it and write your notes.

---

> [!INFO]- 📄 Reference
> ### Reference Material & Static Sources
> Notes on what documents, files, and external sources are indexed as read-only references.
> 
> **Key Planning Items:**
> - [ ] What types of references are supported? (PDFs, Web articles, Markdown notes)
> - [ ] Where are static references stored in the vault?
> - [ ] How are they categorized and tagged?
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- 🤖 Rag
> ### Retrieval-Augmented Generation (RAG) Setup
> Notes on the core RAG mechanism, LLM provider, prompt templates, and vector store configurations.
> 
> **Key Planning Items:**
> - [ ] Vector database selection (e.g., local SQLite, Chroma, or cloud-based)
> - [ ] Embedding model configuration (e.g., Gemini Embeddings, OpenAI, or local HuggingFace)
> - [ ] Retrieval strategy (semantic search similarity thresholds, top-k chunks count)
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- 🧱 block documents
> ### Document Chunking & Block-Level Retrieval
> Strategies for breaking down long notes into smaller, granular blocks/paragraphs for better RAG context retrieval.
> 
> **Key Planning Items:**
> - [ ] Chunking algorithm (e.g., paragraph-based, sentence-based, or fixed-size sliding window)
> - [ ] Handling metadata (inheriting page title, headers, and tags down to block level)
> - [ ] Block references structure in Obsidian (retaining `^block-id` linkages)
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- 🔒 immutable documents
> ### Static & Archival Documents
> How to index logs, completed journal entries, and archived notes that never change.
> 
> **Key Planning Items:**
> - [ ] Identifying which folders are read-only/immutable (e.g., `Journal/`, `Daily tasks/`)
> - [ ] Pre-indexing pipelines for faster search of archival files
> - [ ] Compression or freezing of older vector embeddings
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- 💬 chat bot
> ### Chat Bot Interface & Conversational Flow
> Notes on the chat interface, context window management, conversational history, and system prompts.
> 
> **Key Planning Items:**
> - [ ] Interface layout (sidebar chat panel, floating window, or inline chat)
> - [ ] Memory strategy (summarizing history, sliding window history, or full history)
> - [ ] System prompts and agent personas
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- 🕸️ Whole graphs
> ### Knowledge Graphs & Structural Connections
> Utilizing graph networks, tags, and semantic hubs to retrieve context beyond simple text similarity (Graph RAG).
> 
> **Key Planning Items:**
> - [ ] Mapping notes as a network of nodes (folders, tags, back-links)
> - [ ] Graph-based retrieval algorithms (fetching neighbor nodes of retrieved chunks)
> - [ ] Entity extraction and relationship indexing
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- 🧠 second brain graphs
> ### Obsidian Vault Graph Integration
> Leveraging Obsidian's native link graph and connections for query context.
> 
> **Key Planning Items:**
> - [ ] Utilizing bidirectional links (`[[Note Name]]`) to pass parent/child context
> - [ ] Filtering the vault graph for RAG searches (excluding templates, drafts, or junk)
> - [ ] Visualizing RAG search results on Obsidian's graph view
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*

> [!INFO]- ✏️ Editability
> ### Dynamic Notes & Index Updates
> Managing frequently updated notes, indexing cache invalidation, and keeping the vector store in sync when notes are edited.
> 
> **Key Planning Items:**
> - [ ] Real-time indexing via file save events (Obsidian file-change listener)
> - [ ] Cache invalidation strategy (updating or replacing embeddings for modified blocks only)
> - [ ] Handling note deletions and renames
> - [ ] **Notes & Ideas:**
>   - *Add your thoughts here...*
