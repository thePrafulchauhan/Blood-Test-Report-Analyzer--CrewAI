# Blood-Test-Report-Analyzer--CrewAI
Overview
The Blood Test Report Analyzer is a Python-based system designed to analyze blood test reports and provide summaries in simple, easy-to-understand language. 
The system categorizes the health focus area into one of three categories: 'nutritional', 'infection', or 'general', based on the findings in the report. 
This project utilizes advanced frameworks such as crewai, llama-parse, Create Web Search Tool, and PDFSearchTool.

Features
Automated Analysis: Utilizes machine learning and AI techniques to read and interpret blood test reports.
Health Focus Categorization: Identifies and categorizes the primary health focus area.
User-Friendly Summary: Provides a concise and easily understandable summary of the findings.
Advanced Search Capabilities: The PDFSearchTool allows for semantic searches within PDF content, using custom models and embeddings.
Technologies Used
crewai: For building and managing AI agents and workflows.
llama-parse: A framework for parsing and interpreting complex medical data, particularly useful for extracting and structuring information from detailed documents.
Create Web Search Tool: For integrating web-based search capabilities into the analysis process.
PDFSearchTool: A tool designed for semantic searches within PDF content, using custom models and embeddings.
llama-parse
llama-parse is a powerful tool designed for parsing and interpreting complex data, particularly in medical contexts. It facilitates:

Extraction of Key Information: Efficiently identifies and extracts relevant data from intricate documents such as blood test reports.
Data Structuring: Converts unstructured or semi-structured data into a structured format, making it easier to analyze and interpret.
Integration with AI Models: Works seamlessly with AI models to enhance the accuracy of data interpretation and analysis.
In the Blood Test Report Analyzer, llama-parse processes and interprets detailed information in blood test reports, enabling the system to accurately summarize and 
categorize health focus areas.

Converting Parsed PDF to JSON
To facilitate the analysis of blood test reports, parsed PDF files are converted into JSON format. This process involves:

Parsing the PDF: Using PDFSearchTool or similar tools to extract textual content and data from the PDF document.
Structuring Data: Converting the extracted content into a structured JSON format, where each key-value pair represents specific elements of the blood test
report (e.g., hemoglobin levels, white blood cell count).
Saving as JSON: The structured data is saved as a .json file for easy handling and integration.
Using JSON in an Agent
The JSON file containing the parsed data is then used by an agent within the system:

Loading the JSON: The agent reads the JSON file to access the structured data.
Analysis: The agent processes the data to extract relevant information, identify abnormalities, and categorize the health focus area.
Output: The agent generates a summary based on the analyzed data, providing insights into the health focus of the report.
This approach ensures efficient handling and analysis of detailed medical reports by converting them into a structured format that is easy to work with.

Installation
Clone the Repository:

bash
Copy code
git clone https://github.com/your-repository/blood-test-analyzer.git
Navigate to the Project Directory:

bash
Copy code
cd blood-test-analyzer
Install Dependencies: Ensure pip is installed, then run:

bash
Copy code
pip install -r requirements.txt
Usage
Access and API Key
Developer access can be obtained through Playground on GroqCloud. There you can obtain your API key, access documentation, and review terms and conditions.
If you are currently using OpenAI API, converting to Groq requires the following:

Groq API Key: Obtain your API key from the GroqCloud Playground.
Endpoint: Update your code to use the Groq API endpoint.
Model: Ensure you use the appropriate Groq model.
Define Agents, Tasks, and Setup the Crew
Define Agents
Agents represent roles that perform specific functions within the system. For the Blood Test Report Analyzer, define an agent responsible for analyzing and summarizing blood 
test reports. This agent will read the report, extract key information, and determine the primary health focus area.

Define Tasks
Tasks are specific activities assigned to the agents. For the analysis of blood test reports, create a task that directs the agent to extract key information from the report, 
identify any abnormalities, and categorize the health focus into 'nutritional', 'infection', or 'general'.

Setup the Crew
The Crew is a collection of agents and tasks that work together to accomplish the overall goal. Setting up the Crew involves organizing the agents and tasks to ensure they 
operate effectively together. The Crew manages the workflow between agents and tasks to perform the blood test report analysis.

Example Usage
To use the Crew for analyzing a blood test report:

Prepare the Input Data: Update the input data section with the blood test report data.
Execute the Analysis: Initiate the analysis process using the Crew and obtain the summary of the blood test report.
Testing Agent Functionality
To ensure that each agent is functioning correctly and completing its tasks:

Test Individual Agents: Run tests for each defined agent separately to verify their functionality. Ensure they perform their designated roles effectively and produce the expected outputs.
Validate Task Completion: Check that each task assigned to the agents is completed as expected. This includes verifying that tasks are executed correctly and that the outputs meet the required specifications.
By testing agents individually and validating task completion, you can ensure that the system operates as intended and that each component contributes effectively to the overall analysis.

Note
The main code file for executing the system is named crewai.ipynb. This Jupyter Notebook contains the core logic for defining agents, tasks, and setting up the Crew, 
and should be executed to run the analysis.

Conclusion
The Blood Test Report Analyzer provides a sophisticated and efficient solution for interpreting blood test reports and summarizing the results in an accessible format. 
By leveraging advanced technologies and frameworks, the system ensures accurate and reliable analysis of medical data. The well-defined roles of agents, structured tasks, 
and organized Crew setup contribute to a streamlined workflow, enhancing the system’s effectiveness.

The flexibility of the tool allows it to adapt to various types of blood test reports, making it a valuable asset in medical data analysis. Whether used for individual health 
assessments or integrated into larger health management systems, the Blood Test Report Analyzer offers a robust approach to understanding complex medical information.
