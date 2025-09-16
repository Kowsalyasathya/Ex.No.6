# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools


# Register no: 212222230069
# Aim: 
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required:
OpenAI API (for GPT-based models)

Hugging Face Transformers (for alternative LLMs such as BERT, GPT-2, or Falcon)

# Explanation:
In this experiment, we develop a Python program that connects with more than one AI tool. The code will:

Take a user query as input.

Send the query to two different AI tools (OpenAI GPT model and Hugging Face Transformer model).

Collect the outputs from both models.

Compare the outputs and generate actionable insights.

We follow the persona pattern of a programmer in the agricultural domain. The application focus will be forecasting agricultural commodity prices (aligned with your mini project).

# Program:
```
import openai
from transformers import pipeline

# Set API key for OpenAI
openai.api_key = "YOUR_OPENAI_API_KEY"   # replace with your valid key

# Step 1: User Query
query = "Predict the trend of tomato prices in the next month considering seasonal changes."

# Step 2: OpenAI GPT Response
def get_openai_response(query):
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",  # You can use gpt-4 if available
        messages=[{"role": "system", "content": "You are an agriculture data analyst."},
                  {"role": "user", "content": query}]
    )
    return response["choices"][0]["message"]["content"]

# Step 3: Hugging Face Transformer Response
def get_huggingface_response(query):
    generator = pipeline("text-generation", model="gpt2")  # simple LLM model
    response = generator(query, max_length=60, num_return_sequences=1)
    return response[0]["generated_text"]

# Step 4: Collect outputs
openai_output = get_openai_response(query)
huggingface_output = get_huggingface_response(query)

# Step 5: Compare and generate insights
print("=== OpenAI GPT Output ===")
print(openai_output)
print("\n=== Hugging Face GPT-2 Output ===")
print(huggingface_output)

# Simple comparison
if len(openai_output) > len(huggingface_output):
    print("\n[Insight] OpenAI provided a more detailed explanation suitable for decision-making.")
else:
    print("\n[Insight] Hugging Face output is shorter but can serve as a quick reference.")
```

# Output:
OpenAI GPT Output
Tomato prices are expected to rise in the coming month due to monsoon-related supply chain disruptions. Farmers may benefit by storing produce or connecting with local markets through digital platforms.  

Hugging Face GPT-2 Output
Predict the trend of tomato prices in the next month considering seasonal changes. The demand will increase...

[Insight] OpenAI provided a more detailed explanation suitable for decision-making.


# Conclusion:
Python code was successfully implemented to interact with multiple AI tools (OpenAI and Hugging Face). The outputs were compared, analyzed, and insights were generated.

# Result: 
The corresponding Prompt is executed successfully.
