
# AI-Driven LinkedIn Lead Generation, Scoring & Outreach System

This repository contains an **end-to-end automated workflow** for LinkedIn lead generation and engagement, built using [n8n](https://n8n.io/).  


---

## Features

- AI-powered **lead generation** and **keyword search**  
- Automated **LinkedIn profile search** based on AI-generated keywords  
- Enrichment pipeline that gathers:
  - User’s LinkedIn posts → summarized by AI  
  - Company details → scraped from website  
  - Company posts → summarized by AI  
  - Company latest news → summarized by AI  
- Lead Scoring system (1–10 scale) based on user's profile
- Automated **connection requests** using Airtop nodes  
- AI-generated personalized **draft cold emails** for leads and their connections  
- Structured data storage in Google Sheets for tracking  

---

## Tech Stack

- [n8n](https://n8n.io/) – workflow automation  
- AI Agents (LLM-based) – input processing, summarization, scoring, cold email generation  
- LinkedIn Node – searching profiles, fetching posts  
- Google Sheets – structured data storage   
- Airtop – sending LinkedIn connection requests and managing user connections  


---

## Requirements

Before setting up this workflow, ensure you have the following:

- **Software**
  - [n8n](https://docs.n8n.io/) installed locally or on a server  
 
- **Accounts**
  - Active **LinkedIn account** with valid session cookie (for automation)  
  - **Google account** with access to Google Sheets  
  - **Airtop account** for connection requests and messaging  
  - **HDW account** to fetch linkdin data
  - **OpenAI API key** (or any other LLM provider) for AI agents  

- **Environment Variables**
  - `LINKEDIN_SESSION` → LinkedIn authentication cookie  
  - `GOOGLE_SHEETS_CREDENTIALS` → JSON key for service account  
  - `HDW_API_KEY` → HDW API token
  - `AIRTOP_API_KEY` → Airtop API token  
  - `OPENAI_API_KEY` → for AI message generation and summarization  

---

## Workflow Overview

The workflow runs in the following sequence:

### 1. Lead Input & Keyword Generation
- **AI Agent 1:** Takes input from the user (type of leads required).  
- **AI Agent 2:** Processes the input and generates relevant search keywords.  
- **LinkedIn Node:** Searches LinkedIn with these keywords and fetches lead profiles.  
- **Google Sheets:** Stores the fetched profiles for tracking.  

---

### 2. Data Enrichment
Each lead’s details are enriched and structured into **4 main columns**:  

1. **User’s Post Summary**  
   - Fetches recent LinkedIn posts of the user.  
   - AI Agent summarizes them into concise insights.  

2. **Company Details**  
   - Fetches the company website and scrapes key information.  
   - Saves structured company details.  

3. **Company Posts Summary**  
   - Fetches posts from the company’s official LinkedIn page.  
   - AI Agent generates summarized insights.  

4. **Company News Summary**  
   - AI Agent fetches the latest company news online.  
   - Summarizes key highlights for context.  

---

### 3. Lead Scoring
- **AI Agent:** Analyzes user’s profile .  
- Scores the lead on a **1–10 scale**.  
- Stores score in Google Sheets.  

---

### 4. Engagement Automation
1. **Connection Requests**  
   - Using **Airtop nodes**, automatically sends LinkedIn connection requests to leads.  

2. **Draft Cold Emails**  
   - Fetches the user’s connections via Airtop.  
   - AI Agent generates personalized cold email drafts based on profile and company data.  
   - Sends/email drafts for review or direct outreach.  

---

## Setup & Installation

1. Clone this repository:  
   ```bash
   git clone https://github.com/your-username/linkedin-leadgen-n8n.git
   cd linkedin-leadgen-n8n
2. Import the workflow into n8n:
    - Open n8n
    - Go to Workflows → Import from File
    - Upload the provided JSON
    
3. Configure environment variables:
    - LinkedIn session cookies / credentials
    - Airtop API credentials
    - Google Sheets API credentials
    - AI Agent API key (OpenAI / custom LLM)

Execute the workflow or set up a Schedule Trigger.
