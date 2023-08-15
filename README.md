# CodeMedic: Automatic ICD10/CPT/Snomed code generation for clinical scenarios
#### © 2023 Alexander Solod ℠

Medical coding is an incredibly complex and time intensive task. While there have been previous attempts to create fully automated coding systems, we are still very far from the creation of a fully automated coding app. The following is a 

# How it works
## Agent methodology
The following app uses LLM agents to come up with a collection of valid codes for each given clinical synopsis. The coder agent is told to play a role of a medical coder and is told to provide as many clinical codes as possible for the given scenario. Once the coder agent generates a list of code, they are passed on to the validator agent. The validator agents task is to scrutinize the code list and synopsis, making sure that all the necessary codes have been included, and removing any codes that it feels are unnecessary.


## Hallucination Checker
In order to fight against LLM hallucinations, you can choose to only include codes that have been validated in an ICD-10 database. However, as of right now the hallucination check isn't perfect, and occasionally removes valid codes from the output.


# How to use

## App Usage
- **Input**: Users can input a wide variety of clinical notes.
- **Code Extraction**: The application uses OpenAI's GPT model's zero-short learning capability to extract 
all possible relevant ICD-10 codes from the provided clinical notes.
- **Output**: It display the generated ICD-10 codes instantly upon hitting ENTER or clicking on the Submit button.

## Installation

To install this app:

Clone this repository:
```bash
git clone https://github.com/alexanderSolod/CodeMedic
```

Navigate into the cloned repository:

```bash
cd codemedic
```

Create a virtual environment and install the required packages:

```bash
python -m venv venv
source venv/bin/activate  # For Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Set up your OpenAI API key in a .env file in the root directory of the cloned repository. The file should look like this:
```bash
OPENAI_API_KEY=your-openai-api-key
```
If you do not do so, the app will request you to input your API when you try to run it.

Run the app:

```bash
gradio main.py
```

**Please note that the application should be used for reference purposes only. 
Always consult with a professional coder or practitioner when dealing with medical coding.**