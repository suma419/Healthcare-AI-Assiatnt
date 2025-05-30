#HealthCare Chatbot
HealthMate is an AI-powered health assistant that helps users manage their health inquiries, schedule appointments, and view past interactions. This project uses Django, Neo4j, and other technologies to build an LLM-agnostic chatbot with the flexibility to integrate with various models.

Table of Contents
Project Overview
Key Features
Setting Up the Project Locally
Running the Application
How to Use
Assumptions
Additional Notes
Project Overview
HealthMate is designed to assist users with the following:

Answering health-related queries.
Escalate change requests to Doctor.
Maintaining conversation histories for easy reference.
Using an LLM-agnostic design to swap different language models (e.g., OpenAI’s GPT-4 or Mistral models) with ease.
Assistant logic graph: Graph
Current Knowledge Graph from conversations: Knowledge Graph
Key Features
Conversational Health Assistance: The chatbot can respond to user queries about health and appointments.
Change Requests Alerting: Users can raise requests for appointment or Treatment changes to their doctor.
Conversation History: Users can view their past interactions, filtered by date, in a side panel, with an added search functionality.
LLM-Agnostic Design: The project supports multiple LLMs through a unified interface. Currently only OpenAI models are fully supported. Mistral's and Google's are in development.
RAG Integrated Retrieval Augmented Generation(RAG), allowing chatbot to provide responses from a knowledge base.
Knowledge Graph Integration: Connects to a Neo4j database for context-aware responses.
Setting Up the Project Locally
Follow these instructions to set up the project on your local machine.

Prerequisites
Python 3.10+: Ensure you have Python installed.
Django 5.x: Install the Django framework.
Neo4j: You need a running instance of Neo4j or can use their cloud database AuraDB.
PostgreSQL: For database management.
Step 1: Clone the Repository
git clone https://github.com/nisargptl/healthmate.git
cd healthmate/healthmate
Step 2: Set Up a Virtual Environment
python -m venv env
source env/bin/activate   # On Windows use `env\Scripts\activate`
Step 3: Install Required Dependencies
Install the required Python packages:

pip install -r requirements.txt
Step 4: Set Up Environment Variables
Create a .env file in the root directory and add the following environment variables:

# .env file
API_KEY=<your_llm_api_key>
LLM_MODEL=openai # (mistralai or googleai under development.) 
MODEL_NAME=<model_name> # (gpt-4)
PINECONE_API_KEY=<your_pinecone_api_key>
NEO4J_URI=<your_neo4j_uri>
NEO4J_USER=<your_neo4j_username>
NEO4J_PASSWORD=<your_neo4j_password>
DB_NAME=healthmate_db
DB_USER=<db_user>
DB_PASSWORD=<your_db_password>
Step 5: Set Up the Database
Create Database:

psql -U postgres
CREATE DATABASE heatlthmate_db;
CREATE USER yourusername WITH PASSWORD 'yourpassword';
GRANT ALL PRIVILEGES ON DATABASE healthmate_db TO yourusername;
ALTER USER yourusername WITH SUPERUSER;
\q
Apply the database migrations:

python manage.py makemigrations
python manage.py migrate
Step 6: Start the Django Development Server
python manage.py runserver
Step 7: Access the Application
Open your browser and navigate to http://127.0.0.1:8000 to access the HealthMate chatbot.

Running the Application
To run the application, follow these steps:

Activate the Virtual Environment:

source env/bin/activate   # On Windows use `env\Scripts\activate`
Start the Django Server:

python manage.py runserver
Access the Web Application: Open your browser and go to http://127.0.0.1:8000.
