# OpenAI Chatbot for a Fictional Restaurant

This project uses OpenAI's GPT-3 model to create an interactive chatbot for a fictional restaurant. The chatbot can answer queries and perform tasks like API calls and database queries. The model used is the GPT-3.5-turbo provided by OpenAI. 

The application uses OpenAI Function Calls feature for API calls, MySQL database for restaurant data, and VectorDB for menu data.

## Architecture

![Architecture](https://github.com/andysingal/langchain-project/blob/main/LangChain-Intermediate-Project/architecture.JPG)

## Project Structure

- `app/`: Main Python application.
- `Dockerfile`: Instructions for building the Docker image.
- `requirements.txt`: Python dependencies.
- `build.py` and `run.py`: Python scripts for building and running the Docker image.
- `.env`: Environment variables loaded at runtime, including the OpenAI API key.

## Setting Up and Running the Project

1. Clone the repository.
2. Install Docker.
3. Create a `.env` file with your OpenAI API key (`OPENAI_API_KEY=your-openai-api-key`).
4. Install Python dependencies (`pip install -r requirements.txt`).
5. Build the Docker image (`python build.py`).
6. Run the application (`python run.py`).

The application runs inside a Docker container on port 5567.

## API Endpoints

1. `POST /conversation` - This endpoint takes a user query and responds based on the predefined functions.

2. `GET /reviews` - This endpoint retrieves all the reviews from the database.

3. `GET /orders` - This endpoint retrieves all the orders from the database.


The chatbot accepts HTTP POST requests at the `/conversation` endpoint. Send a JSON object with a `message` key for the chatbot message.

## Functionality

The LLM handles these primary functions:

1. `get_pizza_info(pizza_name: str)`: Fetches pizza information from the MySQL database.
2. `create_order(pizza_name: str)`: Places an order for a pizza.
3. `create_review(review_text: str)`: Stores a restaurant review in the database.
4. `ask_vector_db(question: str)`: Answers questions using VectorDB.

These functions are part of the `api_functions` dictionary which is used by the LLM to handle specific user requests.
