# animated-octo-dollop
# GitHub Copilot, please generate a Pydantic model for handling incoming JSON with a "text" field
from pydantic import BaseModel

class TextInput(BaseModel):
    text: str
