## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

## PROBLEM STATEMENT:
To create an LCEL chain that accepts two inputs and generates meaningful responses using a language model.

## DESIGN STEPS:

### STEP 1:
Import the required libraries and load the API key.

### STEP 2:
Create a prompt with two parameters and initialize the model and output parser.

### STEP 3:
Connect the components using the LCEL pipe operator (`|`) and execute the chain.

## PROGRAM:

```python
import os
import openai

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file
openai.api_key = os.environ['OPENAI_API_KEY']

from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser

# Create prompt
prompt = ChatPromptTemplate.from_template(
    "Suggest a {type} activity for someone interested in {interest}."
)

# Initialize model and parser
model = ChatOpenAI(model="gpt-4o-mini", temperature=0.7)
output_parser = StrOutputParser()

# Create LCEL chain
chain = prompt | model | output_parser

# Execute chain
response = chain.invoke({
    "type": "weekend",
    "interest": "artificial intelligence"
})

print("Generated Response:")
print(response)
```

## OUTPUT:

<img width="690" height="286" alt="image" src="https://github.com/user-attachments/assets/8917e4a0-c6cc-4bd0-b8de-15ce42c05fc8" />


### Real-World Applications:

1. AI Chatbots – Generate responses to user queries.
2. Educational Assistants – Suggest learning activities.
3. Content Generation – Create content based on user inputs.
4. Recommendation Systems – Suggest activities based on user interests.

## RESULT:

Thus, the LCEL expression was successfully implemented using two prompt parameters and three key components. The chain generated meaningful responses and demonstrated its applications in real-world scenarios.
