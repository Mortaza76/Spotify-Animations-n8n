<img width="1440" height="900" alt="Screenshot 2025-09-30 at 4 37 39 PM" src="https://github.com/user-attachments/assets/72a618bd-4861-43c0-a1a2-75397cdf20aa" />

<img width="645" height="1317" alt="Screenshot 2025-09-30 at 4 42 44 PM" src="https://github.com/user-attachments/assets/a5be8c57-8b78-46a9-8515-00c753ca5ee9" />


# LLM → Spotify Autoplay

An intelligent n8n workflow that integrates **LLMs, Google Gemini, and Spotify** to automate song search and playback based on user prompts. This project demonstrates how AI can be used to understand natural language commands and interact with Spotify in real-time.

---

## **Project Overview**

This workflow enables a user to send natural language messages (e.g., “Play the song *Bandana*”) and have the system:

1. Understand the user’s intent using a **Large Language Model (LLM)**.
2. Extract the song and artist information automatically.
3. Search Spotify for the requested track.
4. Add the track to the Spotify playback queue.
5. Provide feedback to the user confirming the addition.

It showcases a **full end-to-end AI automation pipeline** combining conversational AI, memory buffers, and third-party API automation.

---

## **Workflow Architecture**

The workflow consists of the following major components:

| Node Name                        | Purpose                                                                                     |
|---------------------------------|---------------------------------------------------------------------------------------------|
| **When chat message received**    | Trigger node for incoming user messages (LangChain Chat Trigger).                             |
| **AI Agent**                      | Processes user messages and extracts the song name using LLM.                                |
| **Google Gemini Chat Model**      | Large Language Model used to interpret user prompts.                                         |
| **Search tracks by keyword**      | Spotify node to search for the track extracted by the AI Agent.                              |
| **AI Agent1**                     | Prepares the track URI for queuing in Spotify.                                               |
| **Add a song to a queue**         | Adds the track to the user’s Spotify playback queue.                                         |
| **AI Agent2**                     | Sends a confirmation message to the user (song added to queue).                              |
| **Simple Memory / Simple Memory1** | Stores recent conversation history to maintain context for multi-turn conversations.         |

---

## **How It Works**

1. **User Interaction**: The workflow listens for chat messages via the LangChain Chat Trigger node.
2. **Natural Language Processing**: The message is sent to an AI Agent powered by Google Gemini to extract the song name and artist.
3. **Spotify Integration**: The extracted track is searched on Spotify and the first matching track is added to the queue.
4. **Feedback Loop**: Another AI Agent sends a personalized message confirming that the song has been added, enhancing user experience.
5. **Memory Buffers**: Contextual memory ensures multi-turn conversations can maintain state.

---

## **Setup Instructions**

### **Prerequisites**
- [n8n Community Edition](https://n8n.io/) installed locally or hosted.
- A Spotify account with OAuth credentials.
- Google PaLM / Gemini API account for LLM processing.

### **Steps**
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/llm-spotify-autoplay.git
    cd llm-spotify-autoplay
    ```
2. Install dependencies (if running locally with n8n in a project folder):
    ```bash
    npm install
    ```
3. Open n8n:
    ```bash
    export N8N_HOST=127.0.0.1
    export N8N_PORT=5678
    export N8N_PROTOCOL=http
    npx n8n
    ```
4. Import the workflow JSON (`workflow.json`) via **Workflow → Import** in the n8n UI.
5. Configure credentials for **Spotify OAuth2** and **Google Gemini**.
6. Activate the workflow and start interacting with your AI-powered Spotify assistant.


## **Usage Example**

- **Input Message**:
- add the song Bandana to the queue please. Thanks.

- **Workflow Action**:  
1. AI Agent extracts: `{ "song": "Bandana", "artist": "" }`
2. Spotify node searches for the track.
3. Track is added to the queue.
4. AI Agent2 responds:  
   ```
   "Bandana has been added to your queue! Enjoy your music 🎵"
   ```


## **Technologies Used**

- **n8n** – Workflow automation platform.
- **LangChain nodes** – For conversational AI and memory management.
- **Google Gemini / PaLM** – LLM for natural language understanding.
- **Spotify API** – To search tracks and add songs to the playback queue.


## **Features**

- Conversational AI understanding multiple song requests.
- Automatic extraction of song and artist information.
- Spotify queue management via automation.
- Contextual memory for multi-turn conversations.
- Modular design for easy extension (e.g., adding playlists or albums).


## **Future Improvements**

- Support for adding entire albums or playlists automatically.
- Integrate WhatsApp or Telegram notifications for song confirmations.
- Add sentiment-based playlist suggestions using AI.


## **Contributing**

1. Fork the repository.
2. Make improvements or add new features.
3. Submit a pull request.



## **License**

This project is licensed under the MIT License.



