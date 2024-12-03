Explanation of the Code: BuddyGPT - Voice-Based Chat Application
This code implements a voice-based chatbot named BuddyGPT, combining OpenAI's GPT model, audio transcription, and text-to-speech synthesis. It allows users to interact with the chatbot through voice input, which is processed, transcribed, and responded to, both in text and audio formats.

Key Components
Libraries Used:
base64: Encoding binary audio and image data for HTML embedding.
random: Randomly selecting GIFs for visual feedback.
tempfile: Handling temporary files for storing audio.
numpy: Managing numerical operations for audio data.
requests: Fetching GIFs from external URLs.
streamlit: Building the user interface for the chatbot.
whisper: Transcribing audio to text using OpenAI's Whisper model.
langchain: Creating a conversational agent using OpenAI’s GPT model.
elevenlabs: Generating speech from text.
Functions
1. fetch_gif(url: str)
Purpose: Fetches a GIF from a URL and encodes it as a Base64 string for embedding in the chatbot interface.
Inputs: URL of the GIF.
Outputs: Base64 string or an error message if the fetch fails.
2. talking_buddy()
Purpose: Returns an HTML string for displaying a random talking buddy GIF.
Functionality:
Selects a random GIF from a predefined list.
Uses the fetch_gif() function to encode it.
Embeds the encoded GIF into HTML.
3. transcribe(audio: np.ndarray)
Purpose: Transcribes recorded audio using OpenAI's Whisper model.
Process:
Saves the audio to a temporary .mp3 file.
Loads the Whisper model and transcribes the audio.
Logs and displays the transcribed text.
Inputs: Audio data as a NumPy array.
Outputs: Transcribed text.
4. ask_openai(transcribed_text: str, openai_key: str)
Purpose: Sends the transcribed text to OpenAI's GPT model via LangChain to generate a response.
Process:
Constructs a conversational prompt template.
Sends the prompt to OpenAI's GPT model using LangChain.
Logs and displays the chatbot's response.
Updates the talking buddy GIF during the response.
Inputs: Transcribed text and OpenAI API key.
Outputs: Generated response text.
5. tts_with_elevenlabs(answer: str, eleven_labs_key: str)
Purpose: Converts the chatbot's text response to speech using Eleven Labs’ Text-to-Speech API.
Process:
Generates audio from the chatbot’s response.
Embeds the audio in the chatbot interface using Base64 encoding.
Inputs: Chatbot response text and Eleven Labs API key.
Outputs: Plays the generated audio in the Streamlit interface.
6. main()
Purpose: Main function orchestrating the chatbot's functionality.
Process:
Displays the chatbot interface with title and description.
Collects OpenAI and Eleven Labs API keys via the sidebar.
Records user audio using audiorecorder.
Transcribes the audio, generates a response, and plays the response as audio.
Inputs: User's voice input and API keys.
Outputs: Transcription, chatbot response, and audio playback.
Workflow
User Interface:

Built with Streamlit for a simple and interactive experience.
Sidebar collects the necessary API keys.
Audio Recording:

Uses audiorecorder to capture user input.
Transcription:

Transcribes the recorded audio to text using OpenAI’s Whisper model.
Chatbot Response:

Sends the transcribed text to OpenAI’s GPT model via LangChain.
Generates a coherent and human-like response.
Text-to-Speech:

Converts the response to audio using Eleven Labs’ API.
Plays the audio along with a GIF for visual feedback.
Technical Highlights
Whisper Model:

Transcribes user audio to text accurately.
LangChain:

Simplifies the interaction with OpenAI's GPT model.
Eleven Labs:

Generates high-quality, natural-sounding text-to-speech audio.
Streamlit:

Provides a user-friendly web interface for the chatbot.
GIF Integration:

Enhances the user experience with animated visual feedback.
Example Usage
User provides API keys for OpenAI and Eleven Labs.
Records their query by clicking the audio recorder button.
Chatbot transcribes the audio, generates a response, and plays it back.
Error Handling
Handles errors during:
GIF fetching.
Audio transcription.
GPT response generation.
Text-to-speech synthesis.
Logs all errors using loguru for debugging.
