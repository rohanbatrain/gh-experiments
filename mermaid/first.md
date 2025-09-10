# Multilayer Translation + Deployment Architecture

## Diagram 1 – Content Authoring → Translation
```mermaid
graph TD
    subgraph L1[Content Authoring Layer]
        A1[English Markdown Files] --> A2[Front Matter Metadata]
    end

    subgraph L2[Translation Layer - MarkLang]
        B1[Parser] --> B2[LLM Translation (Ollama + LLaMA 3.2 3B)]
        B2 --> B3[Dictionary Consistency Module]
    end

    A2 --> B1
```

---

## Diagram 2 – Translation → Static Site Generation
```mermaid
graph TD
    subgraph L2[Translation Layer - MarkLang]
        B3[Dictionary Consistency Module]
    end

    subgraph L3[Static Site Generation - Hugo]
        C1[Language Directories] --> C2[Multilingual Site Build]
    end

    B3 --> C1
```

---

## Diagram 3 – CI/CD Automation
```mermaid
graph TD
    subgraph L3[Static Site Generation - Hugo]
        C2[Multilingual Site Build]
    end

    subgraph L4[Automation Layer - GitHub Actions]
        D1[Commit Trigger] --> D2[Pipeline Execution]
        D2 --> D3[Auto Translation + Site Build]
    end

    C2 --> D1
```

---

## Diagram 4 – Deployment
```mermaid
graph TD
    subgraph L4[Automation Layer - GitHub Actions]
        D3[Auto Translation + Site Build]
    end

    subgraph L5[Deployment Layer]
        E1[GitHub Pages / Vercel / Netlify]
    end

    D3 --> E1
```
