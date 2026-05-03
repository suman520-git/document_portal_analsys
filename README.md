# Document Portal Analsys

1.  Summarizattion of the data: A system ,it summarises the uploaded pdf file  by the user.

2.  Documents Comparision: When two files  reference and modified files upload to application ,it returns the  
    modified data  with repect to refernce file with page number and  data.

3. Chatting with Documents: Creation of vector database(FAISS) index with uploaded  documents with session id and session folder and chatting with documents
    through retrieving data from vector database.

##  Project Overview

Summarization task(Document Analsys):
1.After uploading the pdf file through front end , it saves the pdf file in the folder with file name  and path.

2.Then It  loads the file through saved path and extracts the text data from the pdf file.

3.The extracted text data is sent to the LLM with prompt to get summary of the data.

4.Built API endpoint for Summarization task with FastAPI 

Documents comparision:

1.After uploading the two  files (Reference file and  modified file) through front end , it saves the files in the folder with their file names  and paths.

2.Two files will be loaded and extracted text data from the Reference and Modified files  and combined two files text data.

3.The combined text data is sent to the LLM with prompt to get  data  which is modified from refernce data with page number and line number

4.Built API endpoint for Documents comparision task with FastAPI 

Conversational RAG(Chat with Documents):

1.Building  Faiss Vector database (Local)index  for uploaded documents type pdf ,docx and text  with specific session id and session folder.

2.Uploading files from front end to  vector index.

3.Built API endpoint to built vector index through FastAPI. 

4.Chat with documents with  stored session id from front end.

5.Built API endpoint to chat with documents through FastAPI. 



## Corrective RAG workflow
![image alt](https://github.com/suman520-git/ecomm-prod-assistant/blob/main/corrective%20Rag.png?raw=true)

## Project Structure
```
ecomm-prod-assistant                             
├─ data                                          
│  └─ product_reviews.csv                        
├─ .github                                        
│  └─ workflows                                  
│     ├─ deploy.yml                              
│     └─ infra.yml                               
├─ infra                                         
│  └─ eks-with-ecr.yaml                          
├─ k8                                            
│  ├─ deployment.yaml                            
│  └─ service.yaml                               
├─ notebook                                      
│  └─ test.ipynb                                 
├─ prod_assistant                                
│  ├─ config                                     
│  │  ├─ config.yaml                             
│  │  └─ __init__.py                             
│  ├─ etl                                        
│  │  ├─ logs                                    
│  │  │  └─ 11_09_2025_00_56_25.log              
│  │  ├─ data_ingestion.py                       
│  │  ├─ data_scrapper.py                        
│  │  └─ __init__.py                             
│  ├─ evaluation                                 
│  │  ├─ ragas_eval.py                           
│  │  └─ __init__.py                             
│  ├─ exception                                  
│  │  ├─ custom_exception.py                     
│  │  └─ __init__.py                             
│  ├─ logger                                     
│  │  ├─ custom_logger.py                        
│  │  └─ __init__.py                             
│  ├─ mcp_servers                                
│  │  ├─ client.py                               
│  │  ├─ product_search_server.py                
│  │  └─ __init__.py                             
│  ├─ prompt_library                             
│  │  ├─ prompts.py                              
│  │  └─ __init__.py                             
│  ├─ retriever                                  
│  │  ├─ retrieval.py                            
│  │  └─ __init__.py                             
│  ├─ router                                     
│  │  ├─ main.py                                 
│  │  └─ __init__.py                             
│  ├─ utils                                      
│  │  ├─ config_loader.py                        
│  │  ├─ model_loader.py                         
│  │  └─ __init__.py                             
│  ├─ workflow                                   
│  │  ├─ agentic_rag_workflow.py                 
│  │  ├─ agentic_workflow_with_mcp.py            
│  │  ├─ agentic_workflow_with_mcp_websearch.py  
│  │  ├─ normal_generation_workflow.py           
│  │  └─ __init__.py                             
│  └─ __init__.py                                
├─ static                                        
│  ├─ f6634145-b9d9-4ea1-b5e5-cb705192c6fd.png   
│  └─ style.css                                  
├─ templates                                     
│  └─ chat.html                                  
├─ test                                          
│  └─ __init__.py                                
├─ corrective Rag.png                            
├─ Dockerfile                                    
├─ get_lib_versions.py                           
├─ main.py                                       
├─ pyproject.toml                                
├─ README.md                                     
├─ requirements.txt                              
├─ scrapper_ui.py                                
└─ setup.py                                      
                     



```

## 🚀 Quick Start

### 1. Environment Setup

```bash
# Clone the repository
git clone https://github.com/suman520-git/ecomm-prod-assistant.git
cd ecomm-prod-assistant

# Create virtual environment
conda create -p venv python==3.10 -y
conda activate venv/ 

# Install dependencies
pip install -r requirements.txt
```

### 2. Configuration

```bash
# Create environment file
.env

# Edit .env with your API keys
# Required:
# - ASTRA_DB_API_ENDPOINT="xxx"
# - ASTRA_DB_APPLICATION_TOKEN="xxx"
# - ASTRA_DB_KEYSPACE="default_keyspace"
# - GOOGLE_API_KEY="xxxx"
# - OPENAI_API_KEY="xxxx"
```

### 3. API Usage

```bash
# For web scraping(Decoupled,Independent of Main RAG pipeline)
step.1 streamlit run /ecomm_prod_assistant/scrapper_ui.py


```
## Streamlit UI(For Web Scraping and Data Ingestion)
![image alt](https://github.com/suman520-git/ecomm-prod-assistant/blob/main/Streamlit_ui.png?raw=true)

```bash
#Steps to the run the application(from root folder):

# first run the MCP server
step.1 python  .\ecomm-prod-assistant\prod_assistant\mcp_servers\product_search_server.py



# start the FastAPI server for the app to start 
step.2 uvicorn prod_assistant.router.main:app --reload --port 8000
# Visit http://localhost:8000



```
## Application UI(For Retrieval and Generation)
![image alt](https://github.com/suman520-git/ecomm-prod-assistant/blob/main/Application_UI.png?raw=true)


### 4.  Dockerization
```bash
# Build Docker Image
step.1 docker build -t prod-assistant .

#Run Docker Container
step.2 docker run -d -p 8000:8000 --name product-assistant prod-assistant

```

## 🆘 Support

For issues and questions:
1. Review the configuration settings
2. Ensure all API keys are properly set
3. Verify network connectivity to external services

---

