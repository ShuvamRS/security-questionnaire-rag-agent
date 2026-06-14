# Security Questionnaire RAG Agent

This project shows how a security questionnaire response workflow can be built with Azure AI Foundry agents, Azure AI Search, and synthetic evidence documents.

The walkthrough follows the newer Microsoft Foundry / Azure portal experience as of June 2026.

The idea is to use two agents:

1. A RAG answer agent searches indexed evidence documents and drafts an answer.
2. A validation agent reviews that answer and checks whether it appears supported by the available evidence.

Instead of answering security questionnaire questions from memory, the workflow retrieves from indexed policy/evidence documents first and then produces a grounded response.

The walkthrough uses fictional company data for **AcmeCloud Analytics**. All evidence documents and questionnaire rows in this repository are synthetic.

## What this project does

The project builds a RAG workflow for security questionnaire answering:

1. Create an Azure AI Foundry project.
2. Deploy a chat model and embedding model.
3. Upload synthetic evidence documents to Azure Blob Storage.
4. Build a RAG index using Azure AI Search.
5. Connect to the Foundry project from a local Python notebook.
6. Create a temporary RAG agent that answers questions from the indexed documents.
7. Create a second temporary validation agent that reviews whether an answer is supported by the indexed evidence.

## How to follow the project

Start with the walkthrough files in order.

Sections **01–05** are documented as general Foundry/Azure setup steps that can be reused for similar Azure AI Foundry + Azure AI Search RAG projects.

Sections **06–07** are specific to this security questionnaire demo.

Complete **Sections 01–04** before running the notebooks. Section 04 covers the local environment, dependencies, `.env` file, and Jupyter setup.

After that, run the notebooks in order:

```text
walkthrough/05_foundry_connection_test.ipynb
walkthrough/06_rag_agent_demo.ipynb
walkthrough/07_multi_agent_validation_demo.ipynb
```

| Section | File                                                                                 | Purpose                                                                     |
| ------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------- |
| 01      | [Foundry project and models](walkthrough/01_foundry_project_and_models.md)           | Create the Foundry project and deploy the chat/embedding models             |
| 02      | [Storage, Search, and permissions](walkthrough/02_storage_search_and_permissions.md) | Create Blob Storage, Azure AI Search, and managed identity permissions      |
| 03      | [RAG index creation](walkthrough/03_rag_index_creation.md)                           | Upload synthetic Markdown evidence and create the Azure AI Search RAG index |
| 04      | [Local environment setup](walkthrough/04_local_environment_setup.md)                 | Set up the Python environment and `.env` file                               |
| 05      | [Foundry connection test](walkthrough/05_foundry_connection_test.ipynb)              | Confirm the local notebook can connect to the Foundry project               |
| 06      | [RAG agent demo](walkthrough/06_rag_agent_demo.ipynb)                                | Create a temporary RAG agent and answer a question from evidence            |
| 07      | [Multi-agent validation demo](walkthrough/07_multi_agent_validation_demo.ipynb)      | Use one agent to answer and another to review support from evidence         |

## Synthetic data

The repository includes synthetic test data under `synthetic_data/`.

The documents are fictional policies for AcmeCloud Analytics and cover areas such as:

* access control
* encryption
* incident response
* data retention
* vendor management
* business continuity

The sample CSV contains security questionnaire questions that can be used to test the RAG agent.

## Running this in your own Azure environment

To run it yourself:

1. Follow Sections **01–03** to create the Azure resources and RAG index.
2. Follow Section **04** to set up the local Python environment and `.env` file.
3. Run Notebooks **05–07** in order.

## Notes from the build

One useful nuance came up during portal verification.

The Azure AI Search index showed successful ingestion, a successful indexer run, a nonzero document count, and vector index usage. However, Search Explorer did not display visible results for simple manual queries during portal testing.

Because the source files were Markdown documents, this may have been related to how the Markdown content was ingested, chunked, or exposed through Search Explorer queries. The later agent notebooks were still able to retrieve answers through the Azure AI Search tool, so this was treated as a Search Explorer / Markdown ingestion verification nuance rather than a failed RAG index.

## Cleanup

Azure resources can continue to create cost after testing.

If you created a dedicated resource group for this project, the simplest cleanup is to delete that resource group after you are done.

Only delete the resource group if it contains resources for this project only. Deleting it will remove the Foundry resource, Azure AI Search service, Storage Account, uploaded documents, indexes, and related resources created during the walkthrough.

