---
title: SlideDeck AI
emoji: 🏢
colorFrom: yellow
colorTo: green
sdk: streamlit
sdk_version: 1.32.2
app_file: app.py
pinned: false
license: mit
---

# SlideDeck AI

We spend a lot of time on creating the slides and organizing our thoughts for any presentation. 
With SlideDeck AI, co-create slide decks on any topic with Generative Artificial Intelligence.
Describe your topic and let SlideDeck AI generate a PowerPoint slide deck for you—it's as simple as that!


# Process

SlideDeck AI works in the following way:

1. Given a topic description, it uses a Large Language Model (LLM) to generate the *initial* content of the slides. 
The output is generated as structured JSON data based on a pre-defined schema.
2. Next, it uses the keywords from the JSON output to search and download a few images with a certain probability.
3. Subsequently, it uses the `python-pptx` library to generate the slides, 
based on the JSON data from the previous step. 
A user can choose from a set of pre-defined presentation templates.
4. At this stage onward, a user can provide additional instructions to *refine* the content.
For example, one can ask to add another slide or modify an existing slide.
A history of instructions is maintained.
5. Every time SlideDeck AI generates a PowerPoint presentation, a download button is provided.
Clicking on the button will download the file.


# Summary of the LLMs

Different LLMs offer different styles of content generation. Use one of the following LLMs along with relevant API keys/access tokens, as appropriate, to create the content of the slide deck:

| LLM | Provider (code) | Requires API key                                                            | Characteristics |
| :-------- | :------- |:----------------------------------------------------------------------------| :------- |
| Mistral 7B Instruct v0.2 | Hugging Face (`hf`) | Optional but encouraged; [get here](https://huggingface.co/settings/tokens) | Faster, shorter content |
| Mistral Nemo Instruct 2407 | Hugging Face (`hf`) | Optional but encouraged; [get here](https://huggingface.co/settings/tokens) | Slower, longer content |
| Gemini 1.5 Flash | Google Gemini API (`gg`) | Mandatory; [get here](https://aistudio.google.com/apikey)                   | Faster, longer content |
| Command R+ | Cohere (`co`) | Mandatory; [get here](https://dashboard.cohere.com/api-keys)                | Shorter, simpler content |

The Mistral models do not mandatorily require an access token. However, you are encouraged to get and use your own Hugging Face access token.


# Icons

SlideDeck AI uses a subset of icons from [bootstrap-icons-1.11.3](https://github.com/twbs/icons)
 (MIT license) in the slides. A few icons from [SVG Repo](https://www.svgrepo.com/)
(CC0, MIT, and Apache licenses) are also used. 


# Known Issues

- **Model unavailable**: Mistral Nemo currently appears to be unavailable. See this [issue](https://huggingface.co/mistralai/Mistral-Nemo-Instruct-2407/discussions/83).
- **Connection timeout**: Requests sent to the Hugging Face Inference endpoint might time out. If it still does not work, wait for a while and try again.

The following is not an issue but might appear as a strange behavior:
- **Cannot paste text in the input box**: If the length of the copied text is greater than the maximum
number of allowed characters in the textbox, pasting would not work.


# Local Development

SlideDeck AI uses LLMs via different providers, such as Hugging Face, Google, and Gemini.
To run this project by yourself, you need to provide the `HUGGINGFACEHUB_API_TOKEN` API key,
for example, in a `.env` file. Alternatively, you can provide the access token in the app's user interface itself (UI). For other LLM providers, the API key can only be specified in the UI.  For image search, the `PEXEL_API_KEY` should be made available as an environment variable. 
Visit the respective websites to obtain the API keys.


# Live Demo

- [SlideDeck AI](https://huggingface.co/spaces/barunsaha/slide-deck-ai) on Hugging Face Spaces
- [Demo video](https://youtu.be/QvAKzNKtk9k) of the chat interface on YouTube


# Award

SlideDeck AI has won the 3rd Place in the [Llama 2 Hackathon with Clarifai](https://lablab.ai/event/llama-2-hackathon-with-clarifai) in 2023.