## Guide: Medical Drug Researcher Dify Plugin
This guide provides instructions on how to set up and effectively use the Medical Drug Researcher Dify Plugin within your Dify applications (Chatflows, Workflows, or Agents).

1. What is the Medical Drug Researcher Plugin?
The Medical Drug Researcher Dify Plugin is a tool designed to instantly retrieve information about drug usage and common side effects. It integrates directly with the DrugBank API, allowing your Dify applications to query a vast database of drug information using natural language commands or structured inputs.

Key Features:

Search for drug information by name.

Retrieve details on typical usage.

Access common side effects.

Seamless integration into Dify workflows and conversational AI.

2. Setup and Configuration
Before using the plugin, you need to configure your DrugBank API credentials within Dify.

2.1. Obtain DrugBank API Credentials
DrugBank Account: You will need an account with DrugBank (DrugBank typically offers different tiers of access, including a comprehensive API for researchers and developers).

API Key: Obtain your API Key from your DrugBank developer dashboard or through their provided API access method.

API Endpoint: Identify the base URL for the DrugBank API that you intend to use. This is typically provided in their API documentation (e.g., https://api.drugbank.com/v1).

2.2. Configure Credentials in Dify
Navigate to your Dify application's "Plugins" or "Tools" section.

Locate the "Medical Drug Researcher" plugin.

Go to its "Credentials" or "Settings" area.

Enter your drugbank_api_key in the designated "DrugBank API Key" field.

Enter your drugbank_api_endpoint (the base URL) in the "DrugBank API Base URL" field.

Save the configurations.

3. Using the Medical Drug Researcher Tool
Once configured, you can invoke the drug_researcher tool in your Dify applications.

3.1. Tool Parameters
The drug_researcher tool accepts the following parameter:

drug_name (string, required):

Description: The full or common name of the medical drug you wish to research.

Example: "Ibuprofen", "Amoxicillin", "Paracetamol"

3.2. Invoking the Tool
In a Chatflow/Agent:
Your Dify Agent, when prompted by a user, can identify the intent to search for drug information and call the tool.

User Input Example: "What is Ibuprofen used for and what are its side effects?"

Agent Action: The LLM would recognize "Ibuprofen" as the drug_name and trigger the drug_researcher tool.

In a Workflow:
You can add a "Tool" node in your workflow, select "Medical Drug Researcher," and map an input variable (e.g., from a "Text Input" node) to the drug_name parameter.

4. Understanding the Output
Upon successful execution, the drug_researcher tool returns a structured JSON object containing the drug's information. This JSON can then be processed by subsequent LLM steps or displayed directly to the user.

Example Output (JSON):
```
{
  "drug_details": {
    "drug_name": "Ibuprofen",
    "usage": "Used for pain relief, fever reduction, and anti-inflammatory purposes.",
    "side_effects": [
      "Stomach upset, heartburn, nausea, vomiting, headaches, dizziness, drowsiness.",
      "Serious side effects include stomach bleeding, kidney problems, and allergic reactions."
    ]
  }
}
```
The Dify interface will typically display this information in a readable format, often as a card or directly in the chat.

5. Use Cases
Personal Health Assistant: Provide quick information to users asking about common medications.

Educational Tool: Assist students or healthcare professionals with rapid access to drug facts.

Information Retrieval: Automate the extraction of drug data for reports or databases.

Content Generation: Aid in creating summaries or articles about pharmaceutical products.

6. Important Disclaimer: NOT MEDICAL ADVICE
THIS PLUGIN IS FOR INFORMATIONAL PURPOSES ONLY AND DOES NOT CONSTITUTE MEDICAL ADVICE. IT IS NOT INTENDED TO BE A SUBSTITUTE FOR PROFESSIONAL MEDICAL ADVICE, DIAGNOSIS, OR TREATMENT. ALWAYS SEEK THE ADVICE OF YOUR PHYSICIAN OR OTHER QUALIFIED HEALTH PROVIDER WITH ANY QUESTIONS YOU MAY HAVE REGARDING A MEDICAL CONDITION OR DRUG USE. NEVER DISREGARD PROFESSIONAL MEDICAL ADVICE OR DELAY IN SEEKING IT BECAUSE OF INFORMATION OBTAINED THROUGH THIS PLUGIN.

7. Troubleshooting
"DrugBank API key is not configured" / "DrugBank API endpoint is not configured":

Solution: Go to the plugin's credentials in Dify and ensure both the API key and the base URL are correctly entered and saved.

"Error from DrugBank API: 4xx/5xx":

Solution: This indicates an issue with the API call itself.

Check your DrugBank API key for correctness and ensure it has the necessary permissions.

Verify the drugbank_api_endpoint URL is exact and accessible.

Consult DrugBank's API documentation for specific error codes and rate limits.

The DrugBank service might be temporarily unavailable.

"No detailed information found...":

Solution: The drug name might be misspelled, or the specific drug may not be present in the DrugBank database, or your API access level doesn't cover it. Try alternative spellings or common names.

"Error parsing DrugBank API response...":

Solution: This suggests the DrugBank API's response format might have changed, or it returned an unexpected structure. You may need to review the plugin's Python code to adapt to the new response format based on DrugBank's latest documentation.

Network Error:

Solution: Check your internet connection and ensure Dify's environment has outgoing network access to the DrugBank API endpoint.