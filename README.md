# 📝 Note Scraping

A Python tool for scraping articles from [note.com](https://note.com/yabukin_coffee/n/n09b9f19e05a6) and storing the extracted information in a Notion database. This tool helps content creators track and analyze their published articles.

## ✨ Features

- 🔍 Automatically scrapes article data from note.com:
  - 📄 Title
  - 📅 Publication date
  - ❤️ Like count
  - 🏷️ Hashtags used in articles
- 📊 Stores data in a structured Notion database for easy access and analysis
- 📋 Uses Google Sheets as a source list for URLs to process in batch

## 🔧 Requirements

- 🐍 Python 3.6+
- 📧 Google account (for using Google Sheets API)
- 🧠 Notion account with API access
- 📦 Required Python packages:
  - `gspread`
  - `google-auth`
  - `notion-client`
  - `beautifulsoup4`
  - `requests`
  - `python-dotenv`

## 🚀 Setup

### 1️⃣ **Create a Google Sheet**:
   - 📝 Add URLs of note.com articles you want to track in a column
   - 🔑 Note the Sheet ID from the URL `https://docs.google.com/spreadsheets/d/{SPREADSHEET_ID}/edit`

### 2️⃣ **Set up Notion Integration**:
   - 🔌 Create a new integration at [Notion Integrations](https://www.notion.so/my-integrations)
   - 🗃️ Create a database with the following properties:
     - `Title` (title type)
     - `Like` (number type)
     - `View` (number type)
     - `URL` (url type)
     - `Charnum` (number type)
     - `Category` (multi-select type)
     - `Publish` (date type)
   - 🔗 Connect your database with the integration
   - 📋 Copy your database ID from the URL

### 3️⃣ **Environment Setup**:
   - 📄 Create a `.env` file with the following variables:
     ```
     SPREADSHEET_ID="your_google_spreadsheet_id"
     SHEET_NAME="Sheet1"
     COLUMN_TO_READ=2
     START_ROW=2
     NOTION_API_KEY="your_notion_integration_key"
     DATABASE_ID="your_notion_database_id"
     ```

## 🏃‍♂️ Usage

### 🌐 Option 1: Run using Google Colab
1. 📓 Open the provided Jupyter notebook in Google Colab
2. 💾 Mount your Google Drive
3. 📂 Set the working directory where your `.env` file is located
4. ▶️ Run all cells sequentially

### 💻 Option 2: Run locally
1. ⚙️ Install required packages:
   ```bash
   pip install gspread google-auth notion-client beautifulsoup4 requests python-dotenv
   ```

2. 📜 Extract the Python code from the notebook into a script
3. 🚀 Run the script:
   ```bash
   python note_scraper.py
   ```

## ⚙️ How It Works

1. 📊 The tool reads URLs from your Google Sheet
2. 🔍 For each URL, it scrapes note.com to extract article data
3. ✏️ The data is formatted and added to your Notion database
4. 📝 Progress and any errors are logged during execution

## ⚠️ Limitations

- 🌐 Works specifically with note.com's current HTML structure
- 📊 Some values like View count and Character count are not implemented
- ⏱️ Rate limits may apply when scraping many articles

## 🔧 Troubleshooting

If you encounter errors:
- 🔍 Verify your environment variables are set correctly
- ✅ Ensure your Notion database property names match exactly (case-sensitive)
- 🔗 Check that your note.com URLs are valid and accessible

---

> 💡 **Tip**: For best results, run the script during non-peak hours to avoid rate limiting by note.com or Notion API.