# animated-octo-dollop
# GitHub Copilot, please generate a Pydantic model for handling incoming JSON with a "text" field
from pydantic import BaseModel

class TextInput(BaseModel):
    text: str
# GitHub Copilot, please create a FastAPI endpoint that accepts a POST request with a JSON body
# The JSON should contain a field "text", and the endpoint should return the checksum of that text.

from fastapi import FastAPI
from hashlib import sha256

app = FastAPI()

@app.post("/generate")
async def generate_checksum(data: TextInput):
    checksum = sha256(data.text.encode()).hexdigest()
    return {"checksum": checksum}
    
@app.get("/")
async def welcome():
    return {"message": "Welcome to the API, this is [Dhiraj Thakur]'s FastAPI project!"}
@app.post("/generate")
async def generate_checksum(data: TextInput):
    """
    This endpoint accepts a POST request with a JSON body containing a field "text".
    It returns the SHA256 checksum of the text provided.
    """

    # GitHub Copilot, please create test cases for the /generate endpoint using FastAPI's test client.

from fastapi.testclient import TestClient

client = TestClient(app)

def test_generate_checksum():
    response = client.post("/generate", json={"text": "Hello World"})
    assert response.status_code == 200
    assert "checksum" in response.json()

    checksum = sha256(data.text.encode()).hexdigest()
    return {"checksum": checksum}

3. Access the API at `http://127.0.0.1:8000`.

## API Endpoints

### GET `/`
Returns a welcome message.

### POST `/generate`
Accepts a JSON body with a field `text` and returns the checksum of the text.
