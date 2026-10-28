# # 🍳 Recipio AI — Telegram Recipe Bot

**Your cravings. Our recipes.**

Recipio AI is an AI-powered recipe assistant built using **n8n, Telegram, and Google Gemini**. It allows users to request recipes through Telegram and receive AI-generated cooking instructions, ingredient lists, and personalized meal suggestions directly in the chat.

## ✨ Features

- 🤖 **AI-Powered Recipes:** Generates recipes based on natural-language requests using Google Gemini.
- 💬 **Telegram Integration:** Interact with the bot directly through Telegram.
- 🧠 **Conversation Memory:** Uses n8n Simple Memory to maintain conversational context.
- 🥗 **Personalized Suggestions:** Request recipes based on ingredients, dietary preferences, cuisine, budget, or cooking time.
- 📩 **Long Message Handling:** Splits lengthy AI responses into smaller messages for Telegram delivery.
- ⚠️ **Error Handling:** Sends a friendly error message if recipe generation or delivery fails.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| [n8n](https://n8n.io/) | Workflow automation |
| [Telegram Bot API](https://core.telegram.org/bots/api) | User interaction and messaging |
| [Google Gemini](https://ai.google.dev/) | AI-powered recipe generation |
| n8n Simple Memory | Conversational context management |

## ⚙️ Workflow Architecture

The automation follows this sequence:

1. **Telegram Trigger** — Receives incoming messages.
2. **AI Recipe Agent** — Processes the request and generates a recipe.
3. **Google Gemini Chat Model** — Provides the language model for the AI agent.
4. **Simple Memory** — Maintains conversational context.
5. **Split Long Reply** — Divides long responses into manageable message chunks.
6. **Send Telegram Reply** — Delivers the generated recipe to the user.
7. **Send Friendly Error** — Handles failures with a user-friendly response.

### Workflow Overview

`Telegram Trigger → AI Recipe Agent → Split Long Reply → Send Telegram Reply`

The AI Recipe Agent uses Google Gemini and Simple Memory. An error-handling path sends a friendly Telegram message when processing fails.

## 🚀 Getting Started

### Prerequisites

- An n8n instance, either self-hosted or cloud-hosted.
- A Telegram account.
- A Telegram bot token.
- A Google Gemini API key.

### 1. Create a Telegram Bot

1. Open Telegram and search for [@BotFather](https://t.me/BotFather).
2. Send `/newbot`.
3. Follow the instructions to choose a bot name and username.
4. Copy the generated bot token and store it securely.

### 2. Configure Google Gemini

1. Obtain an API key through [Google AI Studio](https://aistudio.google.com/).
2. Open n8n and create the appropriate Google Gemini credentials.
3. Connect the Google Gemini Chat Model node to the AI Recipe Agent.

### 3. Configure Telegram Credentials

1. Open your n8n workflow.
2. Configure Telegram credentials using the bot token.
3. Assign the credentials to the Telegram Trigger and Telegram Send Message nodes.

### 4. Configure the AI Agent

Add suitable system instructions to the AI Recipe Agent so that it behaves as a recipe assistant.

The agent should generate clear ingredient lists, quantities, cooking instructions, preparation times, serving sizes, and optional nutritional estimates. It should follow the user's dietary preferences and constraints wherever possible.

### 5. Configure Memory and Responses

- Connect Simple Memory to the AI Recipe Agent.
- Configure the memory session key appropriately for each Telegram chat.
- Configure the Split Long Reply node to split long responses safely.
- Map the generated response and original chat ID to the Telegram Send Message node.
- Configure the error-handling path to send a friendly message to the same chat.

### 6. Activate the Workflow

1. Save the workflow.
2. Test it using the Execute Workflow option.
3. Send a message to your Telegram bot.
4. Verify that the generated recipe reaches the correct chat.
5. Activate the workflow so it can process incoming messages automatically.

## 💬 Example Usage

Send any of the following messages to your bot:

- `Give me a quick vegetarian dinner recipe.`
- `Suggest a high-protein meal under ₹100.`
- `What can I cook with eggs, tomatoes, and onions?`
- `Give me a simple pasta recipe that takes less than 20 minutes.`
- `Suggest a budget-friendly Indian breakfast.`

The bot processes the request and replies with a suitable recipe.

## 🔐 Security

- Store API keys and bot tokens in n8n Credentials.
- Never commit API keys, tokens, or other secrets to GitHub.
- Use environment variables or a secrets manager where appropriate.
- Avoid sharing exported workflow files containing credentials or sensitive execution data.

## 📌 Future Enhancements

- 🛒 Automatic shopping lists based on recipes.
- 📊 Calorie and macronutrient estimation.
- 📅 Weekly meal planning.
- 🥦 Ingredient-based recipe recommendations.
- 🌱 Dietary profiles for vegetarian, vegan, and other preferences.
- 💰 Budget-aware meal planning.
- ⭐ Save favorite recipes for later.

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a pull request.

## 📄 License

This project can be distributed under the MIT License. Add a `LICENSE` file to the repository if you choose this license.

---

**Built with ❤️ using n8n, Google Gemini, and Telegram.**
