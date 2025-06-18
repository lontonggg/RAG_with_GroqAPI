<h1 align="center"> Retrieval-Augmented Generation with Gradio and Groq API Key</h1>
<p align="center"> Natural Language Processing Project</p>

<div align="center">

<img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">

</div>

### Name : Reyhan Zada Virgiwibowo
### Tech Stack : Python, Gradio, LangChain, HuggingFace Embedding, FAISS vector store

---

### 1. Analysis about how the project works
The project lets users upload a PDF file and then ask questions about its content using a simple web interface. When a PDF is uploaded, the text is split into smaller parts, converted into vector representations using HuggingFace embeddings, and stored in a FAISS vector database. When a user asks a question, the system finds the most relevant parts of the PDF and sends them, along with the question, to a language model (via the Groq API) to generate an answer. This way, users can quickly get answers from their documents without reading the whole file.

### 2. Analysis about how different every model works on Retrieval-Augmented Generation

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile", # Change the model in the code
        temperature=0.2
    )
```
- Model used : ```[llama-3.3-70b-versatile, deepseek-r1-distill-llama-70b, gemma2-9b-it]```

2.1 Analysis on ```llama-3.3-70b-versatile``` :  
This model is very strong at understanding and answering questions from documents, giving detailed and accurate responses. It is good at following instructions and can handle a wide range of topics, making it reliable for most question-answering tasks. When used in this project, it usually gives clear and relevant answers based on the content of the PDF.

2.2 Analysis on ```deepseek-r1-distill-llama-70b``` :  
This model is designed to be faster and more efficient, so it responds quickly and uses less computing power. While its answers are still good, sometimes they are a bit shorter or less detailed compared to the larger models. It works well for simple questions and when you need faster results, but for complex questions, the answers might not be as deep.

2.3 Analysis on ```gemma2-9b-it``` :  
This model is smaller than the others, so it is faster and uses less memory, but its answers can be less accurate or more general. It is best for basic questions or when you want quick responses, but it might miss some details from the document. For simple tasks, it works fine, but for more complicated questions, the bigger models usually perform better.

### 3. Analysis about how temperature works

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",
        temperature=0.2 # Change the temperature value here and analzye
    )
```

3.1 Analysis on higher temperature  
When the temperature is set higher, the model's answers become more creative and varied, but sometimes they can be less accurate or go off-topic. This setting is useful if you want more diverse or unexpected responses, but it may make the answers less reliable for factual questions.

3.2 Analysis on lower temperature  
When the temperature is set lower, the model's answers become more focused, predictable, and consistent. The responses are usually more accurate and stick closely to the information in the document, making this setting better for getting clear and reliable answers.

### 4. How to run the project

- Clone this repository with : 

```git
git clone https://github.com/arifian853/RAG_with_GroqAPI.git
```

- Copy the ```.env.example``` file and rename it to ```.env```

```
GROQ_API_KEY=your-groq-api-key
```

- Fill the ```GROQ_API_KEY``` with your Groq API Key, find it here : https://console.groq.com/keys

You can run the project using **pip** or **conda** as below:

**Option 1: Using pip (recommended for most users)**

1. Make sure you have Python 3.10 or newer installed.
2. (Optional but recommended) Create a virtual environment:
   ```bash
   python -m venv env
   ```
   Then activate it:
   - On Windows:
     ```bash
     .\env\Scripts\activate
     ```
   - On Mac/Linux:
     ```bash
     source env/bin/activate
     ```
3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the app:
   ```bash
   python app.py
   ```

**Option 2: Using conda**

1. Make sure you have [conda](https://docs.conda.io/en/latest/miniconda.html) installed.
2. Create and activate a new environment:
   ```bash
   conda create -n ragpdf python=3.12
   conda activate ragpdf
   ```
3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the app:
   ```bash
   python app.py
   ```

After running, open the local URL shown in your terminal to access the Gradio web interface.
