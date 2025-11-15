# n8n AI Newsletter Automation

This n8n workflow automatically researches, drafts, and formats a complete newsletter. It uses a "chain" of AI agents to plan, research, write, and edit the content, finally saving it as a draft in Gmail.

This workflow is based on the "AI Newsletter System" template.

## ✨ Features

* **Scheduled Execution:** Runs automatically on a timer (e.g., weekly).
* **Agentic Planning:** An AI "Planning Agent" first researches a broad topic and then defines a title and three specific sub-topics for the newsletter.
* **In-Depth Research:** The workflow loops through each sub-topic and uses Tavily to perform focused research.
* **Sectional Writing:** A "Section Writer Agent" creates a detailed section for each sub-topic based on its specific research.
* **Final Editing:** An "Editor Agent" combines the sections, writes a unique introduction and conclusion, formats everything into clean HTML, and generates a subject line.
* **Automated Drafting:** The final newsletter is saved as a draft in your Gmail account, ready for review.

## ⚙️ Workflow Breakdown

1.  **Schedule Trigger:** Kicks off the workflow on a set schedule.
2.  **Initial Research:** Uses Tavily to find 3 recent articles about a main topic (e.g., "AI adoption for small businesses").
3.  **Planning Agent:** An LLM (via OpenRouter) reads the research and generates a main title and three sub-topics.
4.  **Split & Research:** The 3 topics are split. The workflow then loops through each one, using Tavily again to get in-depth research for that *specific* topic.
5.  **Section Writer Agent:** A specialized LLM (via OpenRouter) writes one standalone newsletter section for each topic.
6.  **Aggregate:** Collects the three written sections.
7.  **Editor Agent:** A final "senior" LLM (via OpenRouter) assembles the three sections, writes an intro and conclusion, formats the entire newsletter as HTML, and generates an email subject line.
8.  **Create Draft:** The final subject and HTML content are used to create a new draft in Gmail.

## 🚀 Setup Guide

1.  **Import:** Download the `AI Newsletter System.json` file and import it into your n8n canvas.
2.  **Connect Credentials:**
    * **Tavily:** Add your Tavily API key to both `Initial Research` and `Research Topics` nodes.
    * **OpenRouter:** Add your OpenRouter API key to the `OpenRouter Chat Model` and `OpenRouter Chat Model1` nodes.
    * **Gmail:** Add your Gmail (OAuth2) credentials to the `Create a draft` node.
3.  **Configure:**
    * **Schedule Trigger:** Set the schedule you want the newsletter to run on (e.g., every Friday at 9 AM).
    * **Initial Research:** Change the `Query` field to the main topic you want your newsletter to be about.
    * **Create a draft:** Set the `To` email address (e.g., your own email for review).
4.  **Activate:** Save and activate the workflow.

## 📄 License

MIT
