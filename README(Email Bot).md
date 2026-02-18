This n8n workflow creates an AI-powered Gmail auto-responder.

It:

- Monitors inbox via Gmail Trigger

- Filters out sent emails

- Avoids replying to replies (no infinite loops)

- Uses LLM to generate short responses

- Sends reply automatically

🧠 Architecture Flow:-

- Gmail Trigger (polls every minute)

- IF condition:

- Ignore emails labeled SENT

IF condition:

- Ignore emails starting with Re: (prevents reply loops)

- Send email subject + body to LLM

- Generate short reply

- Send reply via Gmail node

🤖 LLM Configuration:-

- Model Used:

google/gemini-2.0-flash-exp:free

- Prompt:

Read the email and reply in short and sweet way.

- Minimalistic by design.

🔧 Requirements:-

- n8n

- Gmail OAuth2 credentials

- OpenRouter API key

- Gmail API enabled in Google Cloud

⚠️ Critical Limitations:-

- No context memory

- No sentiment detection

- No tone adjustment

- No blacklist/whitelist filtering

- No attachment handling

- Poll-based (not webhook-based)

This is automation, not intelligent email management.

💡 Production Improvements:-

- Add intent classification

- Add priority tagging

- Add CRM integration

- Add tone control (formal/casual)

- Add delay logic (don’t reply instantly)

- Add signature block

- Move to Gmail watch (push) instead of polling
