# 🍳 Recipio AI — Telegram Recipe Bot

**Your cravings. Our recipes.**

Recipio AI is an AI-powered recipe assistant built with **n8n, Telegram, and Google Gemini**. Send a recipe request to the Telegram bot and receive an AI-generated recipe in the same chat.

## Features

- AI-generated recipes from natural-language prompts
- Telegram messaging interface
- Conversational context through n8n Simple Memory
- Ingredient, cuisine, budget, dietary, and cooking-time preferences
- Splits long replies into smaller Telegram messages
- Friendly error handling

## Workflow

```text
Telegram Trigger
      |
      v
AI Recipe Agent <--- Google Gemini Chat Model
      ^            <--- Simple Memory
      |
      +---- success ---> Split Long Reply ---> Send Telegram Reply
      |
      +---- error ---------------------------> Send Friendly Error
```

## Tech stack

- [n8n](https://n8n.io/) — workflow automation
- [Telegram Bot API](https://core.telegram.org/bots/api) — messaging
- [Google Gemini](https://ai.google.dev/) — language model

## Repository contents

- `workflow/recipio-ai-workflow.json` — importable n8n workflow template
- `prompts/recipe-agent-system-prompt.txt` — system prompt used by the AI agent
- `.gitignore` — excludes common secrets and local files

## Setup

### 1. Create a Telegram bot

1. Open Telegram and message [@BotFather](https://t.me/BotFather).
2. Send `/newbot` and follow the instructions.
3. Copy the bot token and keep it private.

### 2. Get a Gemini API key

1. Visit [Google AI Studio](https://aistudio.google.com/).
2. Create an API key.
3. Keep the key private. Do not add it to this repository.

### 3. Import the workflow into n8n

1. Download `workflow/recipio-ai-workflow.json`.
2. In n8n, create/open a workflow and choose **Import from File**.
3. Select the JSON file.
4. Open the Telegram Trigger and Telegram messaging nodes and select your Telegram credentials.
5. Open the Google Gemini Chat Model node and select your Gemini credentials.
6. Save the workflow.

> Credential references are intentionally not included in the exported JSON. Configure credentials inside your own n8n instance after importing.

### 4. Test and activate

1. Test the workflow using the Execute Workflow button.
2. Send a message to your bot, such as `Give me a quick vegetarian dinner under ₹100`.
3. Check that the bot replies in the same Telegram chat.
4. If it works as expected, activate the workflow.

## Example requests

- `Give me a quick vegetarian dinner recipe.`
- `Suggest a high-protein meal under ₹100.`
- `What can I cook with eggs, tomatoes, and onions?`
- `Give me a pasta recipe that takes less than 20 minutes.`
- `Suggest a budget-friendly Indian breakfast.`

## Security

- Never commit Telegram bot tokens or Gemini API keys.
- Store credentials in n8n Credentials or a suitable secrets manager.
- Before committing workflow exports, inspect them for credentials, personal data, and execution data.
- If a token is accidentally published, revoke or rotate it immediately.

## Limitations

- Ingredient prices and nutrition values are estimates unless verified with a reliable data source.
- Recipe quality depends on the selected Gemini model and its availability.
- The workflow is a starter template; n8n node versions and parameter schemas can vary by installation. If your n8n version flags a node parameter, open that node and reselect the equivalent option in the editor.

## Future improvements

- Weekly meal planning
- Shopping-list generation
- Recipe favorites
- Nutrition and macro estimates
- User dietary profiles
- Ingredient-based recommendations

## License

This project is provided as a starter template. Add a `LICENSE` file if you decide to publish it under a specific open-source license.
