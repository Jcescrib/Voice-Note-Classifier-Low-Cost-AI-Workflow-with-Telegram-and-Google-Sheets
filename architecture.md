# 🏗️ Architecture – Voice Note Classifier (Low-Cost AI Workflow)

This document describes the internal structure and logic of the n8n automation workflow for transcribing and classifying Telegram voice messages.

---

## 🔄 High-Level Flow

1. **Receive Voice Message**  
   Triggered by a Telegram bot when a new voice message is received.

2. **Download Audio**  
   The audio file is downloaded from Telegram using its `file_id`.

3. **Transcription (Whisper)**  
   The audio is transcribed using OpenAI Whisper (via the OpenAI API).

4. **AI Classification (Category + Concept)**  
   The transcribed text is analyzed to extract:
   - `Categoria`: keyword or tag (e.g., “ideas”, “feedback”)
   - `Concepto`: concise idea extracted from the content

5. **Validate Output Format**  
   The AI output is validated against a JSON schema to ensure it complies with the expected structure.

6. **Format for Storage**  
   Fields are mapped and prepared: transcription, category, concept, and unique file ID.

7. **Save to Google Sheets**  
   Appends a new row with the processed information.

8. **Export CSV + Save to Google Drive**  
   A CSV version of the data is generated and stored in a specified Drive folder.

9. **User Confirmation on Telegram**  
   A confirmation message is sent back to the user, summarizing that processing is complete.

10. **Error Handling**  
   If any step fails, an alert message is sent to an admin chat.

---

## 🧱 Main Technologies

| Component           | Purpose                     |
|---------------------|-----------------------------|
| **Telegram Bot**     | Input channel for audio     |
| **OpenAI Whisper**   | Speech-to-text transcription |
| **OpenAI GPT / Gemini** | Classification engine       |
| **Google Sheets API** | Structured data storage     |
| **Google Drive API**  | File-based backup           |
| **n8n**               | Workflow engine             |
| **Railway**           | Hosting and execution       |

---

## ⚙️ Node Map Summary

| Node Name                        | Description                                         |
|----------------------------------|-----------------------------------------------------|
| Telegram - On New Voice Message | Trigger when message is received                   |
| Telegram - Download Voice File  | Downloads audio                                    |
| OpenAI - Transcribe Audio       | Transcribes audio to text                          |
| AI - Classify Category & Concept| Extracts category and concept using a prompt       |
| AI - Validate Structured Output | Validates JSON response structure                  |
| Format Data for Storage         | Sets fields for storage                            |
| Google Sheets - Append Entry    | Appends structured data to a sheet                 |
| Convert JSON to CSV             | Prepares CSV export                                |
| Google Drive - Upload CSV       | Stores the CSV in a Google Drive folder            |
| Telegram - Send Confirmation    | Notifies the user via Telegram                     |
| Error Trigger + Error Message   | Captures errors and notifies admin chat            |

---

## 📊 Google Sheets Structure

The spreadsheet must contain the following columns (in this exact order):

| Column Name     | Description                                    |
|-----------------|------------------------------------------------|
| file_unique_id  | Unique ID of the voice file from Telegram      |
| Categoria       | Category label extracted from the text         |
| Concepto        | Key idea or summarized concept                 |
| Transcripción   | Full text transcription of the message         |

**Example:**

| file_unique_id | Categoria | Concepto | Transcripción |
|----------------|----------|---------|---------------|
| AgJ6ABCdEfG12... | Ideas | Optimize logistics | "Category ideas. We need to reduce times..." |

## 📌 Notes
---
- This architecture enables fast classification and data logging of ideas, thoughts, or meeting notes received via voice.
- Ensure all API credentials are set via environment variables.
- The workflow is optimized for low-cost usage by limiting token-heavy steps.
- Designed to be modular, easy to extend, and deployable on Railway or locally.
