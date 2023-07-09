---
layout: post
title: A Pathway to Positivity
subtitle: Generate Positive Thoughts Through the Power of OpenAI API and Python
tags: [Python, OpenAI]
---
In today's dynamic and sometimes demanding world, cultivating a positive mindset is essential for our overall well-being. Fortunately, the advancements in artificial intelligence have ushered in a new era of possibilities, allowing us to harness technology in uplifting our spirits. Python, coupled with the OpenAI API, stands out as a powerful combination that empowers developers to utilize cutting-edge language models. In this blog post, our focus extends beyond generating positive and uplifting thoughts using OpenAI; I aim to showcase the versatility of Python in leveraging the API to unlock a world of possibilities.  

**Setting Up the OpenAI API Credentials**  
To begin generating positive thoughts with Python, we first need to set up the OpenAI API credentials. This involves obtaining an API key from OpenAI and securely storing it. By importing the necessary Python libraries, such as openai, and configuring the API key, we establish the connection between Python and the OpenAI API. 

```python
# Import OpenIA library and file containing the OpenAI access key
import openai
import credentials

# Set the OpenAI API key by assigning the value from credentials.openai_key to openai.api_key. 
# This step ensures that the API key is properly configured for making API requests.  
openai.api_key = credentials.openai_key
``` 

**Crafting the Conversation**  
Python allows us to structure a conversation with the OpenAI API. We start by defining a system message, such as "You are an expert in generating positive thoughts." This helps guide the model's understanding of its role. Then, we provide a user prompt that expresses the desired context or request for a positive thought. 
```python
system_prompt = "You are an expert in generating positive thoughts."  # system-level instruction or prompt
user_prompt = "I am grateful for the little things in life that bring me joy and happiness tell me a positive thought" # user interaction
```
**The generate_positive_thought Function**  
At the heart of this positive thought generation process is the generate_positive_thought function. This Python function takes two crucial parameters: system_prompt and user_prompt. 
```python
# Function to generate a positive thought using OpenAI
# The function named generate_positive_thought takes two parameters: system_message and user_prompt.
def generate_positive_thought(system_prompt, user_prompt):
# Define a list called messages that contains two dictionaries representing the system and user messages/prompts.
    messages_list = [
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": user_prompt}
    ]
    # Make a call to the OpenAI API using openai.ChatCompletion.create. The response from the API call is stored in the response variable.
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=messages_list, 
        max_tokens=100,  # Adjusting this value allows you to control the length of the generated response
        temperature=0.5  # A higher value, such as 0.8, makes the output more random and diverse. A lower value of 0.2 makes the output more focused.
    )
```
The function creates a messages_list from the system_prompt and user_prompt. This list contains two dictionaries: one for the system message and another for the user message. This structured conversation helps guide the OpenAI language model in producing relevant and uplifting responses.

**Fine-Tuning with Parameters**  
Python enables us to fine-tune the generated responses by adjusting the parameters provided to the OpenAI API. Key parameters include max_tokens and temperature. By modifying max_tokens, we control the length of the generated response. Experimenting with different values helps us find the optimal response length for our needs. Similarly, adjusting the temperature parameter allows us to influence the randomness and creativity of the generated thought. Python's flexibility empowers us to dynamically tweak these parameters and observe the resulting effects. For further information on additional parameters, I recommend referring to the [OpenAI documentation](https://platform.openai.com/docs/api-reference/completions/create).

**Invoking the Function**  
The first line of the code below invokes the generate_positive_thought function, passing in the system_prompt and user_prompt as parameters. The function returns a response with the positive thought that can be printed or used in further conversation with the api.

```python
response = generate_positive_thought(system_prompt, user_prompt)
print("Positive Thought: ", response)
```

To achieve the desired positive thought, Python facilitates experimentation and optimization. By iteratively refining the system message, user prompt, and parameter values, we can improve the generated output. Python's ease of use and ability to automate repetitive tasks make it an ideal tool for exploring various combinations.

Python, as a versatile and widely-used programming language, provides a robust foundation for interacting with the OpenAI API. This powerful combination empowers us to leverage cutting-edge language models and tap into the vast potential of artificial intelligence.

A detailed code listing, available in a Jupyter Notebook format, can be accessed in a [Github Code Repository](https://github.com/MarkCruse/positive-thought-generator-using-openai/blob/main/positive_thoughts_generator.ipynb) I have created.