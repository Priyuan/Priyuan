# GPT-3 Sentiment Analysis

This project implements a simple interactive chat interface using OpenAI's GPT-3 model and performs sentiment analysis on the responses using Hugging Face's `transformers` library.

## Prerequisites

Before running the code, make sure you have the following installed:

- Python 3.6 or later
- pip (Python package installer)

### Required Libraries

Install the necessary libraries by running:

```bash
pip install transformers torch openai
python your_script_name.py
import openai
from transformers import pipeline

# Set up OpenAI API key
openai.api_key = 'YOUR_OPENAI_API_KEY'

# Initialize the sentiment analysis pipeline
sentiment_pipeline = pipeline("sentiment-analysis")

def get_gpt3_response(prompt):
    """Function to get a response from GPT-3."""
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",  # You can use gpt-4 if available
        messages=[
            {"role": "user", "content": prompt}
        ]
    )
    return response['choices'][0]['message']['content']

def analyze_sentiment(text):
    """Function to analyze sentiment of the text."""
    sentiment = sentiment_pipeline(text)[0]
    return sentiment

def main():
    while True:
        user_input = input("You: ")
        if user_input.lower() in ['exit', 'quit']:
            print("Exiting the chat.")
            break
        
        # Get response from GPT-3
        gpt3_response = get_gpt3_response(user_input)
        print(f"GPT-3: {gpt3_response}")

        # Analyze sentiment
        sentiment = analyze_sentiment(gpt3_response)
        print(f"Sentiment: {sentiment['label']} (Score: {sentiment['score']:.2f})")

if __name__ == "__main__":
    main()
Here's a sample `README.md` file for your sentiment analysis project using GPT-3 and Hugging Face's `transformers` library.

```markdown
# GPT-3 Sentiment Analysis

This project implements a simple interactive chat interface using OpenAI's GPT-3 model and performs sentiment analysis on the responses using Hugging Face's `transformers` library.

## Prerequisites

Before running the code, make sure you have the following installed:

- Python 3.6 or later
- pip (Python package installer)

### Required Libraries

Install the necessary libraries by running:

```bash
pip install transformers torch openai
```

## Getting Started

1. **Clone the repository** (if applicable) or create a new Python file and copy the code provided below.

2. **Obtain an OpenAI API Key**:
   - Sign up at [OpenAI](https://openai.com) and create an API key.

3. **Set Up Your API Key**:
   - Replace `YOUR_OPENAI_API_KEY` in the code with your actual OpenAI API key.

4. **Run the Script**:
   - Execute the script in your terminal or command prompt:

   ```bash
   python your_script_name.py
   ```

## Code Overview

```python
import openai
from transformers import pipeline

# Set up OpenAI API key
openai.api_key = 'YOUR_OPENAI_API_KEY'

# Initialize the sentiment analysis pipeline
sentiment_pipeline = pipeline("sentiment-analysis")

def get_gpt3_response(prompt):
    """Function to get a response from GPT-3."""
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",  # You can use gpt-4 if available
        messages=[
            {"role": "user", "content": prompt}
        ]
    )
    return response['choices'][0]['message']['content']

def analyze_sentiment(text):
    """Function to analyze sentiment of the text."""
    sentiment = sentiment_pipeline(text)[0]
    return sentiment

def main():
    while True:
        user_input = input("You: ")
        if user_input.lower() in ['exit', 'quit']:
            print("Exiting the chat.")
            break
        
        # Get response from GPT-3
        gpt3_response = get_gpt3_response(user_input)
        print(f"GPT-3: {gpt3_response}")

        # Analyze sentiment
        sentiment = analyze_sentiment(gpt3_response)
        print(f"Sentiment: {sentiment['label']} (Score: {sentiment['score']:.2f})")

if __name__ == "__main__":
    main()
```

### Key Functions

- `get_gpt3_response(prompt)`: Sends the user prompt to GPT-3 and retrieves its response.
- `analyze_sentiment(text)`: Uses the Hugging Face pipeline to analyze the sentiment of the given text.
- The main loop allows users to interact with GPT-3, receiving responses and sentiment analysis until they decide to exit.

## Usage

- Type your messages when prompted.
- To exit the chat, type `exit` or `quit`.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Acknowledgments

- [OpenAI](https://openai.com) for the GPT-3 API.
- [Hugging Face](https://huggingface.co) for the Transformers library.
