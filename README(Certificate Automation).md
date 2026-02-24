Certificate Automation (n8n Workflow)
📌 Overview

This project automates certificate generation and email delivery using n8n.

It reads data from Google Sheets, generates personalized certificates using Google Slides, emails them via Gmail, and updates the status in the sheet.

⚙️ Features:-

- Reads recipient data from Google Sheets

- Copies certificate template from Google Drive

- Replaces placeholders automatically

- Downloads final certificate

- Sends email with attachment

- Marks status as Sent in sheet

🛠️ Tech Stack:-

1) n8n

2) Google Sheets API

3) Google Drive API

4) Google Slides API

5) Gmail API

🔄 Workflow Steps:-

- Manual trigger

- Fetch rows from Google Sheets

- Copy certificate template

- Replace placeholders

- Download certificate

- Send email

- Update status to Sent

📄 Required Sheet Format:-

Your sheet must contain:

Name	Id	Course	Date	Email	Status

Status is updated automatically.

📑 Template Placeholders

- Your Google Slides template must include:

{{Name}}
{{ID}}
{{Course}}
{{Date}}

🚀 Setup:-

- Import Certificate automation.json into n8n

- Connect Google & Gmail credentials

- Replace Sheet ID, Template ID, and Folder ID

- Fill Google Sheet with data

- Click Execute Workflow

❗ Notes:-

- No retry system

- No error logging

- Suitable for small-scale automation and learning

👤 Author:-
Created by Aradhya Thapa 
