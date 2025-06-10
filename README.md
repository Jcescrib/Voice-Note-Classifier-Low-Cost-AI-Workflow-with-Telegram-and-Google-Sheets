# 🗣️ Voice Note Classifier (Low-Cost AI Workflow)

![n8n](https://img.shields.io/badge/n8n-workflow-orange)
![Telegram](https://img.shields.io/badge/Telegram-Bot-blue)
![OpenAI](https://img.shields.io/badge/OpenAI-Whisper-success)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Connected-green)

This repository contains a real-world automation built with [n8n](https://n8n.io), deployed on [Railway](https://railway.app), and designed to classify Telegram voice notes using OpenAI.

---

## 🧠 Description

AI workflow built with [n8n](https://n8n.io) to process voice messages sent via Telegram:

- ✅ Transcribes audio using OpenAI Whisper
- 🧠 Classifies messages using GPT / Gemini
- 📊 Logs results in Google Sheets
- ☁️ Uploads structured data as CSV to Google Drive
- 🤖 Sends Telegram confirmation
- 🚨 Sends alerts on error via Telegram

![image](https://github.com/user-attachments/assets/7e5845d1-78c2-46aa-99d7-0e2a23ddb56a)

---

## 🏗️ Architecture

1. Telegram Bot receives a voice message
2. Audio is downloaded and transcribed using Whisper
3. AI classifies the message into:
   - `Categoria`
   - `Concepto`
4. Result is saved to:
   - ✅ Google Sheets (structured storage)
   - ✅ Google Drive (CSV backup)
5. User receives confirmation on Telegram
6. Errors are reported to an admin chat via Telegram

---

## 🚀 Features

- Converts Telegram voice messages to text (via Whisper)
- Classifies structured content with GPT / Gemini
- Saves transcription and labels to Google Sheets
- Stores CSV backup on Google Drive
- Real-time Telegram confirmation
- Error handling via Telegram alerts
- Optimized for low-cost API usage

---

## 🛠️ Stack

- `n8n` – Workflow Automation Engine
- `OpenAI Whisper` – Audio-to-text transcription
- `GPT/Gemini` – Intelligent classification
- `Telegram Bot API` – Message input/output
- `Google Sheets API` – Data logging
- `Google Drive API` – File storage
- `Railway` – Serverless deployment

---

## 🧾 Project Structure

```text
workflow/                    # n8n JSON export
docs/                        # Architecture and deployment notes
deploy/                      # Railway setup and tips
assets/                      # Screenshots and diagrams
.env.sample                  # Sample environment file
README.md                    # You're reading it
LICENSE                      # Project license
