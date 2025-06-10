# Voice Note Classifier – Low-Cost AI Workflow with Telegram and Google Sheets

This repository contains a real-world automation built with [n8n](https://n8n.io), deployed on [Railway](https://railway.app), and designed to classify Telegram voice notes using OpenAI.

![image](https://github.com/user-attachments/assets/7e5845d1-78c2-46aa-99d7-0e2a23ddb56a)


## 🚀 Features

- Converts Telegram voice messages to text (via Whisper)
- Classifies content using GPT
- Saves transcription + label to Google Sheets
- Optionally stores audio files in Google Drive
- Low-cost and serverless deployment

## 🛠️ Stack

- n8n (Workflow Automation)
- OpenAI Whisper + GPT API
- Telegram Bot API
- Google Sheets API
- Railway for deployment

## 📁 Project structure

- `n8n_workflow/`: exported JSON from n8n
- `docs/`: usage and deployment guides
- `env.sample`: example .env file

## 🧪 Status

✅ Fully tested on live setup  
📦 Preparing full documentation  

## 📝 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.
