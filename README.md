# One-Day Tour Planning Helper

Hola! This section provides a comprehensive overview of the architecture and components used to build this application. 
---

## Project Architecture

### System Overview
The One-Day Tour Planning helper is built using a modular and scalable architecture, incorporating multiple agents for specific tasks, memory management, and a user-friendly frontend interface. Below is a detailed breakdown:

---

### Key Components
1. **Frontend:**
   - Framework: Streamlit.
   - Features:
     - A user login system for personalized access.
     - An interactive chat interface for planning discussions.
     - A display area for itineraries and real-time updates.

2. **Backend:**
   - Framework: FastAPI.
   - Microservices:
     - **User Interaction Agent:** This agent manages user inputs and guides the conversation, ensuring a smooth interaction.
     - **Itinerary Generation Agent:**  Responsible for crafting personalized itineraries based on user preferences.
     - **Optimization Agent:** Provides current weather information and adjusts plans as needed.
     - **Weather Agent:** Provides current weather information and adjusts plans as needed.
     - **Memory Agent:** Utilizes Neo4j to store and recall user preferences, enhancing personalization.


3. **Memory Management:**
   - Database: Neo4j (GraphDB).
   - Functionality:
     - Stores user preferences as triplets (Entity-Relationship-Entity).
     - Adapts dynamically to user inputs for seamless personalization.

4. **Tools and Libraries:**
   - Language Models: Transformers/Ollama/vLLM for LLM endpoints.
   - Database: Neo4j for memory graph.
   - API Framework: FastAPI for backend microservices.
   - Frontend: Streamlit for chat and display.

---

### Workflow
1. **User Interaction:**
   - Users input details such as city, budget, interests, and timings.
   - The User Interaction Agent collects this information and guides the planning process.

2. **Memory Integration:**
   - User preferences are stored in Neo4j, allowing the system to recall them during future interactions.
   - The system adapts dynamically to ensure a personalized experience.

3. **Itinerary Creation:**
   - The Itinerary Generation Agent suggests tailored plans based on the collected inputs.
   - Adjusments are made t fit within the specfied budget and time constraints.

4. **Weather and News Updates:**
   - The Weather Agent provides real-time weather forecasts relevant to the user's destination.
   - Alerts about news or events related to the location are also fetched.


5. **Dynamic Updates:**
   - Users can modify their preferences during the conversation.
   - The system instantly re-optimizes the itinerary to reflect these changes.

---

### Architecture of this project

```mermaid
graph TD
    A[Frontend: Streamlit] --> B[Backend: FastAPI]
    B --> C[User Interaction Agent]
    B --> D[Itinerary Generation Agent]
    B --> E[Optimization Agent]
    B --> F[Weather Agent]
    B --> G[Memory Agent: Neo4j]
    G --> H[GraphDB: User Preferences]
    C -->|Inputs| G
    E -->|Optimized Paths| G
    D -->|Itineraries| A
