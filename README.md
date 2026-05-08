<p align="center">
  <img src="docs/alien-preview.png" alt="Chat with Aliens" width="380" />
</p>

<h1 align="center">Chat with Aliens</h1>

<p align="center">
  <strong>Chat with FBI-documented alien entities — powered by 3,037 pages of declassified government files.</strong>
</p>

<p align="center">
  <a href="https://chatwithaliens.net">chatwithaliens.net</a>
</p>

---

## What is this?

Chat with Aliens is a RAG-powered AI application that lets you have real conversations with five extraterrestrial entities named in declassified FBI, CIA, and Department of Defense documents. Every response is grounded in actual government records — when the alien quotes a file, it links you directly to the exact page of the source PDF.

This is not fiction. These names — Affa, Ponnar, Monka, Orthon, Zemkla — appear in real FBI surveillance files, declassified UAP reports, and government-monitored correspondence spanning decades.

---

## Features

**AI Agents grounded in real documents**
Five alien characters, each with a distinct identity sourced from declassified files. Ask them anything — they search through 3,037 pages of government records and respond with citations linking back to the original PDF.

**Full-text RAG over 51 source documents**
Every FBI file, CIA report, DoD UAP assessment, and AARO release was manually ingested, chunked, and indexed into a PostgreSQL database with full-text search. No hallucinations about the files — the model only cites what's there.

**Source citations on every response**
Alien messages include clickable chips linking to the exact page of the source document. Read the government's own words.

**UAP Incident Globe**
An interactive 3D globe plotting 40 declassified UAP incidents, all sourced from government records.

**Declassified Media Archive**
23 UAP videos and FLIR thermal imaging stills from official government releases, accessible in-app.

---

## The Alien Entities

| Entity | Origin | Source |
|--------|--------|--------|
| **Affa** | Uranus | FBI File HQ 62-83894, Section 8 |
| **Ponnar** | Hatann | FBI File HQ 62-83894, Section 8 |
| **Monka** | Mars | FBI-monitored Flying Saucers International, 1966 |
| **Orthon** | Venus | FBI Oklahoma City Office, Dec 9, 1958 |
| **Zemkla** | Unknown Star System | FBI-surveilled AFSCA Convention, Reno NV, 1966 |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React, Vite, TypeScript, Tailwind CSS, Framer Motion |
| Backend | Node.js, Express 5, TypeScript |
| Database | PostgreSQL + Drizzle ORM |
| AI | GPT-4o with retrieval-augmented generation |
| Search | PostgreSQL full-text search over 2,416 indexed document chunks |
| API Contract | OpenAPI spec with generated React Query hooks and Zod schemas |
| Deployment | Cloud autoscale infrastructure |

---

## Architecture

```
User query
    │
    ▼
shouldSearchDocs() — guards against frivolous RAG calls
    │
    ▼
PostgreSQL full-text search over document_chunks
    │
    ▼
Top-ranked chunks injected into GPT-4o system prompt
    │
    ▼
Response with inline source citations → linked PDF pages
```

The RAG pipeline only fires when the query is document-relevant. General conversation flows directly to the model without retrieval overhead.

---

## Document Sources

- FBI Unexplained Phenomenon files (HQ 62-83894, Sections 1–10)
- CIA declassified UAP assessments
- Department of Defense UAP Task Force reports
- AARO (All-domain Anomaly Resolution Office) public releases
- Government-monitored civilian correspondence and convention records

**3,037 pages. 51 documents. 2,416 indexed chunks.**

---

## Live

[chatwithaliens.net](https://chatwithaliens.net)
