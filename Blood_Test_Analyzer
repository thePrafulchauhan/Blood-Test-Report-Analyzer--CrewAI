import streamlit as st
from crew import Agent, Task, Crew  # Replace with the actual path to your implementation file

llm = None  # Replace with your language model initialization

# Define the agents
Report_Analyzer_Agent = Agent(
    role='Report Analyzer',
    goal='Analyze blood test reports and identify health focus areas',
    backstory=(
        "You are an expert in interpreting medical data, especially blood test reports."
        "Your task is to read the report, extract key parameters, and determine the primary health focus area."
        "The focus area could be related to nutritional status, infections, or general health conditions."
        "Based on your analysis, categorize the health focus into one of these areas."
    ),
    verbose=True,
    allow_delegation=False,
    llm=llm,
)

Knowledge_Base_Search_Agent = Agent(
    role='Knowledge Base Search',
    goal='Search for relevant health information based on identified health concerns',
    backstory=(
        "You specialize in finding the most relevant and credible health information online."
        "Using the focus area provided by the Report Analyzer Agent, you will search for articles, studies, and other resources."
        "Your search should prioritize up-to-date and trustworthy sources."
        "Employ NLP techniques to assess the relevance of the content to the identified health concerns."
    ),
    verbose=True,
    allow_delegation=False,
    llm=llm,
)

Health_Recommendations_Agent = Agent(
    role='Health Recommendations',
    goal='Provide personalized health recommendations based on gathered information',
    backstory=(
        "You are an expert in health and wellness, capable of providing well-rounded recommendations."
        "Using the resources and information gathered by the Knowledge Base Search Agent, compile personalized health advice."
        "Consider aspects such as dietary changes, lifestyle modifications, and when to seek medical consultation."
        "Your recommendations should be practical, actionable, and tailored to the individual's health concerns."
    ),
    verbose=True,
    allow_delegation=False,
    llm=llm,
)

# Define the tasks
report_analyzer_task = Task(
    description=(
        "Read and analyze the blood test report provided as input {response}. "
        "Extract key information such as blood test parameters (e.g., hemoglobin levels, white blood cell count), "
        "and identify any abnormalities. "
        "Determine if the focus should be on 'nutritional', 'infection', or 'general' health areas based on the report. "
        "Return a single word: 'nutritional', 'infection', or 'general' based on the findings. "
        "Do not provide any other preamble or explanation."
    ),
    expected_output=(
        "Return a single word: 'nutritional', 'infection', or 'general' based on the blood test report analysis. "
        "Do not provide any other preamble or explanation."
    ),
    agent=Report_Analyzer_Agent,
    #tools=[],  # Assuming no external tools needed for this example
)

knowledge_base_search_task = Task(
    description=(
        "Using the focus area identified by the Report Analyzer Agent, {focus_area}, "
        "conduct a search for relevant articles, studies, and information on the internet. "
        "Focus on finding the latest and most credible sources related to the identified health area. "
        "Use natural language processing (NLP) techniques to ensure the relevance of the content found. "
        "Return a list of URLs or titles of the most relevant resources found. "
        "Do not provide any other preamble or explanation."
    ),
    expected_output=(
        "Return a list of URLs or titles of the most relevant articles, studies, or information "
        "related to the identified health area {focus_area}. "
        "Do not provide any other preamble or explanation."
    ),
    agent=Knowledge_Base_Search_Agent,
    #tools=[],  # Assuming no external tools needed for this example
)

health_recommendations_task = Task(
    description=(
        "Compile the information gathered by the Knowledge Base Search Agent, including URLs or titles of articles, studies, and other resources {resources}. "
        "Based on the identified health concerns, provide personalized health recommendations. "
        "Consider dietary changes, lifestyle modifications, and potential medical consultations. "
        "The recommendations should be practical and actionable. "
        "Return the recommendations in a concise format. "
        "Do not provide any other preamble or explanation."
    ),
    expected_output=(
        "Return a list of personalized health recommendations based on the compiled resources {resources}. "
        "The recommendations should include dietary changes, lifestyle modifications, and suggestions for medical consultations if necessary. "
        "Do not provide any other preamble or explanation."
    ),
    agent=Health_Recommendations_Agent,
    # tools=[recommendation_tool],
)

# Create the crew
rag_crew = Crew(
    agents=[Report_Analyzer_Agent, Knowledge_Base_Search_Agent, Health_Recommendations_Agent],
    tasks=[report_analyzer_task, knowledge_base_search_task, health_recommendations_task],
    verbose=True,
)

# Streamlit app
st.title("Health Report Analysis and Recommendations")

# User inputs
report_input = st.text_area("Enter the blood test report:")
focus_area_input = st.selectbox("Select the focus area:", ["nutritional", "infection", "general"])

if st.button("Analyze Report"):
    inputs = {
        "response": report_input,
        "focus_area": focus_area_input,
        "resources": [
            "https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5581799/",
            "https://www.mayoclinic.org/tests-procedures/thyroid-function-tests/about/pac-20385075",
            "https://www.endocrine.org/thyroid-conditions",
            "https://www.diabetes.org/diabetes/glucose-monitoring",
            "https://www.webmd.com/diabetes/guide/understanding-diabetes-diagnosis-treatment"
        ]
    }

    result = rag_crew.kickoff(inputs=inputs)

    st.write("### Analysis Result:")
    st.write(result)
