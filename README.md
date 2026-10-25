# SUMMARIX — AI-Powered Economic News Analysis

**A five-person team project turning economic news and YouTube discussions into accessible, visual insights.**

**Project period:** September–October 2025  
**My role:** News crawling, news summarisation, YouTube opinion mining, and API/data integration  
**Type:** Software development bootcamp team capstone

[Watch the project demo](https://www.youtube.com/watch?v=Bk_dYeuUDCE) · [Browse the source code](./fast_api) · [Spring Boot application](./news)

> **Portfolio note:** This repository contains a **sanitised source-code snapshot** of our five-person bootcamp project, published with the team’s permission. Credentials, local research datasets and large trained-model artifacts have been removed. Some features require external services, credentials and models, so this snapshot is **not verified as runnable end-to-end**.

## Project overview

SUMMARIX is an AI-assisted economic news analysis web application created during a software development bootcamp in South Korea. The team combined external news and video data, unstructured-data storage, natural-language processing, API services, and interactive dashboards to make economic trends easier to understand.

### Team-developed features

- Economic news dashboard with headlines, keyword rankings, trends, sentiment indicators, and topic clusters
- Daily article summaries and news briefings
- YouTube comment analysis, including sentiment and keyword visualisations
- News search, content recommendations, and an AI-powered chatbot

These were **team features**, not features I built entirely on my own.

## My contributions

### 1. Python web crawling and data storage

- Developed Python web-crawling scripts using **requests** and **BeautifulSoup** to collect and parse Korean economic news articles.
- Processed unstructured article content and stored records in **MongoDB** for subsequent analysis.
- Worked on data preparation to support news categorisation, summarisation, keywords, and sentiment analysis.

### 2. FastAPI ↔ Spring Boot ↔ frontend integration

- Built a **FastAPI** endpoint that retrieved MongoDB-backed news data and returned keyword-trend information as **JSON**.
- Implemented a proof-of-concept **Spring Boot** controller using **WebClient** to fetch data from FastAPI.
- Connected the response to a webpage using JavaScript **fetch()** and **Chart.js** to visualise keyword trends.

**Code examples in this repository:** [News crawler](./fast_api/collect/news_clawler.py), [FastAPI analysis endpoints](./fast_api/analysis/opinion_mining.py), [Spring Boot API integration](./news/src/main/java/com/bgroup/news/analysis/service/AnalysisGateway.java), and [JavaScript frontend](./news/src/main/resources/static/js).

### 3. News summaries and opinion mining

- Contributed to news summarisation workflows and API-connected news presentation.
- Worked on YouTube opinion-mining functionality, including Korean text tokenisation and stopword filtering.
- Investigated data flow and frontend display issues while integrating features with the rest of the team.

The original team documentation lists my primary responsibilities as news crawling, news summarisation and YouTube opinion mining.

## System architecture

The application's main web layer used **Spring Boot (Java)**, while Python-based analysis and data functionality were exposed through **FastAPI**. **MongoDB Atlas** was used for storage.

```mermaid
flowchart TD
    A["Economic news websites and external APIs"] --> B["Python collection: requests + BeautifulSoup"]
    B --> C[("MongoDB Atlas: articles and analysis data")]
    C --> D["FastAPI: data and analysis endpoints"]
    D --> E["Spring Boot: WebClient and REST controllers"]
    E --> F["Frontend: HTML, CSS, JavaScript, Thymeleaf"]
    F --> G["Charts, summaries, search and dashboards"]
```

*This diagram illustrates a representative data flow. Other application features used additional services and integrations.*

### Example: keyword-trend visualisation

1. News data was collected and stored in MongoDB.
2. A FastAPI endpoint retrieved relevant documents and returned processed keyword data as JSON.
3. Spring Boot used WebClient to request that API response.
4. The frontend retrieved the response using JavaScript and visualised the data with Chart.js.

This particular end-to-end integration was a **prototype**, not a claim of production deployment.

## Technology stack

| Area | Technologies in the team project |
| --- | --- |
| Frontend | HTML, CSS, JavaScript, Thymeleaf, Chart.js |
| Web backend | Java 17, Spring Boot, Gradle, Spring WebClient |
| Python API and processing | Python, FastAPI, pandas, requests |
| Collection | BeautifulSoup, external news APIs, YouTube Data API |
| Database | MongoDB Atlas |
| AI and NLP | Korean text processing, sentiment analysis, summarisation, topic clustering, LLM-based features |
| Version control | Git, GitHub |

**My primary hands-on work:** Python, BeautifulSoup, MongoDB, FastAPI, REST/JSON integration, a Spring Boot WebClient proof of concept, and JavaScript/Chart.js data rendering.

## What I learned

- Building data pipelines for unstructured web content
- Retrieving database records through REST API endpoints
- Connecting independently developed backend services to a browser UI
- Debugging problems across collection, data storage, APIs, and rendering
- Collaborating on a multi-module web application with a five-person team

## Demo and source code

- **Demo video:** https://www.youtube.com/watch?v=Bk_dYeuUDCE
- **Python APIs and collection:** [fast_api/](./fast_api)
- **Spring Boot backend and web UI:** [news/](./news)
- **Public-source safety notes:** [SECURITY_NOTES.md](./SECURITY_NOTES.md)

### Configuration notes

Python services expect environment variables for database and external API access. See [.env.example](./.env.example). Some modules call `load_dotenv()`; other modules require variables exported in the shell or provided by the process manager. Spring Boot also reads `MONGO_URI` from its environment. Use **newly issued credentials** only; do not reuse credentials from the original project.

**Running the full application:** Each Python service may require a different virtual environment and start command. The Java app is under `news/`. The repository does not include private data, downloaded models, external cloud services or an automated end-to-end test; please treat this as a code portfolio rather than a plug-and-play deployment.

## Credits and scope

**SUMMARIX was developed by five team members.** This README distinguishes my individual contributions from features implemented by teammates. The source code has been republished with team consent and without application credentials or the original Git commit history.

---

**Seongjin Jang** · [LinkedIn](https://www.linkedin.com/in/seongjin-jang-87815b359)

> **Security:** Keys exposed in the original team repository must be rotated or revoked. Publishing this clean snapshot does not remove secrets from the original repository history.
