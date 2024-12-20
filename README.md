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
