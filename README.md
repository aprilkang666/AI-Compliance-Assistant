# AI-Compliance-Assistant

# 🧩 AI Compliance Assistant (n8n + Mock / OpenAI)

### Overview
The **AI Compliance Assistant** automates security policy reviews using an AI workflow built in [n8n](https://n8n.io/).  
It analyzes written policies (like SOC 2 or ISO 27001 documents) and returns a structured summary of:
- ✅ Key Controls implemented
- ⚠️ Missing Controls
- 💡 Recommendations for improvement

This project is built to showcase how **AI workflows, APIs, and automation** can be used to bridge engineering and business needs — perfect for security and pre-sales engineering demonstrations.

---

### ✨ Features
- Accepts policy text via webhook or API call  
- Analyzes and summarizes control coverage  
- Outputs clean structured JSON  
- Runs fully offline with **Mock AI responses** (no cost)  
- Can be easily switched to live **OpenAI API** for realism  
- Integrates smoothly with Slack, Email, or JSON file export  

---

### 🧰 Tech Stack
- **n8n** – workflow automation  
- **Postman** – API testing  
- **JSON / REST APIs**  
- *(Optional)* OpenAI API (`gpt-3.5-turbo`)

---

### 🧠 Workflow Diagram
```mermaid
graph TD
    A[Webhook Trigger] --> B[Mock/OpenAI Response]
    B --> C[Function Node - Extract Message Text]
    C --> D[Set Node - Format Structured Output]
    D --> E[Move Binary Data - Convert to JSON File]
    E --> F[Webhook Response / Download File]
````

---

### 🚀 Quick Start

#### 1. Import into n8n

1. Download and import `ai_compliance_assistant_workflow.json` into your n8n workspace.
2. Ensure **Webhook Trigger** and **Response** nodes are active.
3. (Optional) Replace the Mock node with your OpenAI HTTP Request node if you want live results.

#### 2. Test with Postman

1. Import the provided collection:
   `AI Compliance Assistant Test.postman_collection.json`
2. Open the request inside Postman.
3. Under **Headers**, add your OpenAI API key.

⚠️ **Important:** In the collection JSON file, locate this section and replace the line below with your real key:

```json
"header": [
  {
    "key": "Content-Type",
    "value": "application/json"
  },
  {
    "key": "Authorization",
    "value": "**YOUR TOKEN**"  ← 🔐 Replace this with your actual OpenAI API key (e.g., 'Bearer sk-xxxxxxx')
  }
],
```

💡 Your key should include the word **Bearer** before the token:

```
Bearer sk-XXXXXXXXXXXXXXXXXXXXXXXXX
```

4. Hit **Send** — you’ll see structured compliance results in seconds.

---

### 🧾 Example Input

```json
{
  "policy_text": "Access to production systems shall be restricted to authorized personnel only. MFA is required for all privileged accounts."
}
```

### 🧩 Example Output

```json
{
  "Key Controls": "Access Control, Multi-Factor Authentication (MFA)",
  "Missing Controls": "Offboarding Review, Logging and Monitoring",
  "Recommendations": "Add quarterly access audits and centralized logging for compliance visibility."
}
```

---

### 📂 Repository Structure

```
├── ai_compliance_assistant_workflow.json          # n8n workflow export
├── AI Compliance Assistant Test.postman_collection.json  # Postman test
├── input_policy_example.json                      # Example policy input
├── output_summary_example.json                    # Example AI output
├── README.md                                      # Documentation
└── demo_screenshot.png / demo_video_link           # (Optional)
```

---

### 🧑‍💻 Author

**Yi Chuan (April) Kang**
🔗 [LinkedIn](https://linkedin.com/in/april-kang)
📧 [yichuan.april.kang@gmail.com](mailto:yichuan.april.kang@gmail.com)

---

### ⚠️ Security Notes

* **Never commit your OpenAI API key** to GitHub.
* In the Postman collection, the `"YOUR TOKEN"` placeholder is intentionally left blank for safety.
* When using live API mode, store your key as an environment variable or Postman secret.

---

### 💡 Optional Improvements

* Add a framework selector (SOC 2 / ISO 27001 / HIPAA)
* Connect to Slack for team alerts
* Integrate with cloud storage for automated document scanning
* Swap Mock node for real-time OpenAI API for production demos

````

---

## 🧩 **Postman Collection Section**

In your `AI Compliance Assistant Test.postman_collection.json`, make sure the headers section looks like this (with clear instructions inside):

```json
"header": [
  {
    "key": "Content-Type",
    "value": "application/json"
  },
  {
    "key": "Authorization",
    "value": "**YOUR TOKEN**"   ← 🔐 Replace this with your actual OpenAI API key (e.g., 'Bearer sk-xxxxxxx')
  }
],
````

✅ That bold `"YOUR TOKEN"` is your placeholder — you’ll replace it with:

```
Bearer sk-XXXXXXXXXXXXXXXXXXXXXXXX
```

*(Remember to keep the word “Bearer” in front of your key.)*

---

Would you like me to generate the **README.md + Postman collection file template (.json)** as downloadable text so you can copy both files directly into your GitHub repo?
