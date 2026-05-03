# Document Portal Analsys

1.  Summarizattion of the data: A system ,it summarises the uploaded pdf file  by the user.

2.  Documents Comparision: When two files  reference and modified files upload to application ,it returns the  
    modified data  with repect to refernce file with page number and  data.

3. Chatting with Documents: Creation of vector database(FAISS) index with uploaded  documents with session id and session folder and chatting with documents
    through retrieving data from vector database.

##  Project Overview

### Summarization task(Document Analsys):

1.After uploading the pdf file through front end , it saves the pdf file in the folder with file name  and path.

2.Then It  loads the file through saved path and extracts the text data from the pdf file.

3.The extracted text data is sent to the LLM with prompt to get summary of the data.

4.Built API endpoint for Summarization task with FastAPI 

### Documents comparision:

1.After uploading the two  files (Reference file and  modified file) through front end , it saves the files in the folder with their file names  and paths.

2.Two files will be loaded and extracted text data from the Reference and Modified files  and combined two files text data.

3.The combined text data is sent to the LLM with prompt to get  data  which is modified from refernce data with page number and line number

4.Built API endpoint for Documents comparision task with FastAPI 

### Conversational RAG(Chat with Documents):

1.Building  Faiss Vector database (Local)index  for uploaded documents type pdf ,docx and text  with specific session id and session folder.

2.Uploading files from front end to  vector index.

3.Built API endpoint to built vector index through FastAPI. 

4.Chat with documents with  stored session id from front end.

5.Built API endpoint to chat with documents through FastAPI. 



## Corrective RAG workflow
![image alt](https://github.com/suman520-git/ecomm-prod-assistant/blob/main/corrective%20Rag.png?raw=true)

## Project Structure
```
document_portal_analsys                                    
├─ api                                                     
│  ├─ __pycache__                                          
│  │  └─ main.cpython-311.pyc                              
│  └─ main.py                                              
├─ archive                                                 
│  └─ src                                                  
│     ├─ document_analyzer                                 
│     │  ├─ __pycache__                                    
│     │  │  ├─ data_analysis.cpython-311.pyc               
│     │  │  ├─ data_ingestion.cpython-311.pyc              
│     │  │  └─ __init__.cpython-311.pyc                    
│     │  ├─ data_analysis.py                               
│     │  ├─ data_ingestion.py                              
│     │  └─ __init__.py                                    
│     ├─ document_compare                                  
│     │  ├─ __pycache__                                    
│     │  │  ├─ data_ingestion.cpython-311.pyc              
│     │  │  ├─ document_comparator.cpython-311.pyc         
│     │  │  └─ __init__.cpython-311.pyc                    
│     │  ├─ data_ingestion.py                              
│     │  ├─ document_comparator.py                         
│     │  └─ __init__.py                                    
│     ├─ multi_document_chat                               
│     │  ├─ __pycache__                                    
│     │  │  ├─ data_ingestion.cpython-311.pyc              
│     │  │  ├─ retrieval.cpython-311.pyc                   
│     │  │  └─ __init__.cpython-311.pyc                    
│     │  ├─ data_ingestion.py                              
│     │  ├─ retrieval.py                                   
│     │  └─ __init__.py                                    
│     ├─ single_document_chat                              
│     │  ├─ __pycache__                                    
│     │  │  ├─ data_ingestion.cpython-311.pyc              
│     │  │  ├─ retrieval.cpython-311.pyc                   
│     │  │  └─ __init__.cpython-311.pyc                    
│     │  ├─ data_ingestion.py                              
│     │  ├─ retrieval.py                                   
│     │  └─ __init__.py                                    
│     ├─ __pycache__                                       
│     │  └─ __init__.cpython-311.pyc                       
│     └─ __init__.py                                       
├─ config                                                  
│  └─ config.yaml                                          
├─ data                                                    
│  ├─ document_analysis                                    
│  │  ├─ session_20260502_163648_1bb11f69                  
│  │  │  └─ NIPS-2017-attention-is-all-you-need-Paper.pdf  
│  │  ├─ session_20260502_212952_e7155ed4                  
│  │  │  └─ Long_Report_V2.pdf                             
│  │  ├─ session_20260502_213637_eee37d60                  
│  │  │  └─ sample.pdf                                     
│  │  └─ sample.pdf                                        
│  ├─ document_compare                                     
│  │  ├─ session_20260502_212033_2161fb0f                  
│  │  │  ├─ Long_Report_V1.pdf                             
│  │  │  └─ Long_Report_V2.pdf                             
│  │  ├─ session_20260502_213708_70bf1cfe                  
│  │  │  ├─ Long_Report_V1.pdf                             
│  │  │  └─ Long_Report_V2.pdf                             
│  │  ├─ Long_Report_V1.pdf                                
│  │  └─ Long_Report_V2.pdf                                
│  ├─ madhu                                                
│  │  ├─ 3a6dbe27.pdf                                      
│  │  ├─ 40007ef8.pdf                                      
│  │  ├─ 62c8c9bd.pdf                                      
│  │  └─ 7ade7972.pdf                                      
│  ├─ multi_doc_chat                                       
│  │  ├─ market_analysis_report.docx                       
│  │  ├─ NIPS-2017-attention-is-all-you-need-Paper.pdf     
│  │  ├─ sample.pdf                                        
│  │  └─ state_of_the_union.txt                            
│  ├─ single_document_chat                                 
│  │  └─ NIPS-2017-attention-is-all-you-need-Paper.pdf     
│  └─ 06c96159.txt                                         
├─ document_portal_analsys.egg-info                        
│  ├─ dependency_links.txt                                 
│  ├─ PKG-INFO                                             
│  ├─ SOURCES.txt                                          
│  └─ top_level.txt                                        
├─ exception                                               
│  ├─ __pycache__                                          
│  │  ├─ custom_exception.cpython-311.pyc                  
│  │  └─ __init__.cpython-311.pyc                          
│  ├─ custom_exception.py                                  
│  ├─ custom_exception_archive.py                          
│  └─ __init__.py                                          
├─ faiss_index                                             
│  ├─ madhu                                                
│  │  ├─ index.faiss                                       
│  │  ├─ index.pkl                                         
│  │  └─ ingested_meta.json                                
│  ├─ index.faiss                                          
│  ├─ index.pkl                                            
│  └─ ingested_meta.json                                   
├─ infrastructure                                          
│  └─ document-portal-cf.yaml                              
├─ logger                                                  
│  ├─ __pycache__                                          
│  │  ├─ custom_logger.cpython-311.pyc                     
│  │  └─ __init__.cpython-311.pyc                          
│  ├─ custom_logger.py                                     
│  └─ __init__.py                                          
├─ logs                                                    
│  ├─ 03_15_2026_22_10_15.log                              
│                             
│                             
│                              
│                              
│                             
├─ model                                                   
│  ├─ __pycache__                                          
│  │  └─ models.cpython-311.pyc                            
│  └─ models.py                                            
├─ notebook                                                
│  ├─ data                                                 
│  │  └─ sample.pdf                                        
│  ├─ logs                                                 
│  │  ├─ 03_07_2026_14_06_03.log                           
│  │                           
│  ├─ exception_experiment.ipynb                           
│  ├─ experiments.ipynb                                    
│  ├─ Exp_topics.ipynb                                     
│  └─ logging_experiment.ipynb                             
├─ prompt                                                  
│  ├─ __pycache__                                          
│  │  ├─ prompt_library.cpython-311.pyc                    
│  │  └─ __init__.cpython-311.pyc                          
│  ├─ prompt_library.py                                    
│  └─ __init__.py                                          
├─ src                                                     
│  ├─ document_analyzer                                    
│  │  ├─ __pycache__                                       
│  │  │  ├─ data_analysis.cpython-311.pyc                  
│  │  │  └─ __init__.cpython-311.pyc                       
│  │  ├─ data_analysis.py                                  
│  │  └─ __init__.py                                       
│  ├─ document_chat                                        
│  │  ├─ __pycache__                                       
│  │  │  ├─ retrieval.cpython-311.pyc                      
│  │  │  └─ __init__.cpython-311.pyc                       
│  │  ├─ retrieval.py                                      
│  │  └─ __init__.py                                       
│  ├─ document_compare                                     
│  │  ├─ __pycache__                                       
│  │  │  ├─ document_comparator.cpython-311.pyc            
│  │  │  └─ __init__.cpython-311.pyc                       
│  │  ├─ document_comparator.py                            
│  │  └─ __init__.py                                       
│  ├─ document_ingestion                                   
│  │  ├─ __pycache__                                       
│  │  │  ├─ data_ingestion.cpython-311.pyc                 
│  │  │  └─ __init__.cpython-311.pyc                       
│  │  ├─ data_ingestion.py                                 
│  │  └─ __init__.py                                       
│  ├─ __pycache__                                          
│  │  └─ __init__.cpython-311.pyc                          
│  └─ __init__.py                                          
├─ static                                                  
│  └─ style.css                                            
├─ templates                                               
│  └─ index.html                                           
├─ tests                                                   
│  ├─ __pycache__                                          
│  │  ├─ test_unit_cases.cpython-311-pytest-8.4.1.pyc      
│  │  └─ __init__.cpython-311.pyc                          
│  ├─ test_unit_cases.py                                   
│  └─ __init__.py                                          
├─ utils                                                   
│  ├─ __pycache__                                          
│  │  ├─ config_loader.cpython-311.pyc                     
│  │  ├─ document_ops.cpython-311.pyc                      
│  │  ├─ file_io.cpython-311.pyc                           
│  │  ├─ model_loader.cpython-311.pyc                      
│  │  └─ __init__.cpython-311.pyc                          
│  ├─ config_loader.py                                     
│  ├─ document_ops.py                                      
│  ├─ file_io.py                                           
│  ├─ model_loader.py                                      
│  └─ __init__.py                                          
├─ app.py                                                  
├─ Dockerfile                                              
├─ documents_comparator_test.py                            
├─ document_analyzer_test.py                               
├─ document_chat_test.py                                   
├─ main_archive.py                                         
├─ multidoc_chat_test.py                                   
├─ README.md                                               
├─ requirements.txt                                        
├─ setup.py                                                
└─ versions.py                                             
                                   
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

