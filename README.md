# 🎙️ AI Blog to Podcast Agent

An AI-powered **Blog-to-Podcast Agent** that automatically converts a blog article into an engaging **2-person podcast conversation** using Google Gemini.

The project takes a blog URL, extracts the article content, sends the content to Gemini, and generates a natural podcast-style script with a **Host** and **Guest**.

## 🚀 How It Works

```text
Blog URL
   ↓
Web Scraping
   ↓
Article Text Extraction
   ↓
Google Gemini AI
   ↓
Podcast Script Generation
   ↓
Host + Guest Conversation
```

## ✨ Features

* 🔗 Accepts a blog/article URL
* 🌐 Extracts webpage content using `Requests` and `BeautifulSoup`
* 🧹 Removes unnecessary webpage elements such as scripts, styles, navigation, and footer content
* 🤖 Uses **Google Gemini** to generate the podcast script
* 🎙️ Creates a natural **Host & Guest** conversation
* 📚 Explains technical concepts in simple language
* ⏱️ Generates a script designed for approximately **3 minutes**
* 🚫 Instructs the AI not to invent information that isn't present in the source article
* ☁️ Designed to run easily in **Google Colab**

## 🛠️ Technologies Used

* **Python**
* **Google Gemini API**
* **Google Colab**
* **Requests**
* **BeautifulSoup4**
* **Google GenAI SDK**
* **gTTS**

## 📦 Installation

Install the required Python packages:

```python
!pip install -q google-genai requests beautifulsoup4 gtts
```

## 🔑 API Key Setup

The project uses a Gemini API key stored securely in Google Colab Secrets.

Create a secret named:

```text
GEMINI_API_KEY
```

Then load it using:

```python
from google.colab import userdata

GEMINI_API_KEY = userdata.get("GEMINI_API_KEY")
```

## ▶️ Usage

### 1. Enter a Blog URL

Provide the URL of the article you want to convert:

```python
blog_url = "https://example.com/article"
```

### 2. Extract the Article

The project uses `BeautifulSoup` to extract readable text from the webpage while removing unnecessary elements.

```python
soup = BeautifulSoup(response.text, "html.parser")

for element in soup(["script", "style", "nav", "footer"]):
    element.decompose()

article_text = soup.get_text(separator=" ", strip=True)
```

### 3. Generate the Podcast Script

The extracted article is sent to Gemini with instructions to create a two-person podcast featuring:

* **Host**
* **Guest**
* Natural conversation
* Simple explanations
* Important points from the article
* Approximately 3 minutes of content

### 4. Get the Result

The generated podcast conversation is stored in:

```python
podcast_script
```

and printed as the final output.

## 📁 Project Structure

```text
AI-Blog-to-Podcast-Agent/
│
├── AI_Blog_to_Podcast_Agent.ipynb
└── README.md
```

## 🎯 Example Workflow

```text
Blog Article
     ↓
Article Content Extraction
     ↓
Google Gemini
     ↓
Podcast Script
     ↓
Host: Welcome to today's episode...
Guest: Today we're going to discuss...
```

The result is a conversational podcast script rather than a simple article summary.
