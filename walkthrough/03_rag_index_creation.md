# 03 — RAG Index Creation

This section creates a RAG index in Azure AI Search from documents stored in Azure Blob Storage.

The index is created using the Azure AI Search import wizard, the previously created Blob Storage container, and the embedding model deployment from Azure AI Foundry.

## Step 3.1 — Upload documents to the Blob directory

* Go to Azure Portal -> Storage Account created.
* Go to Data storage -> Containers.
* Open the container created previously.
* Open the directory created previously, or create a new directory.
* Click Upload.
* Select the documents that Azure AI Search should use for RAG.
* Wait until the uploaded files appear inside the directory.
* This makes the source documents available for Azure AI Search indexing.

![Uploaded documents in Blob directory](assets/03_01_blob_documents_uploaded.png)

## Step 3.2 — Start the Azure AI Search import wizard

* Go to Azure Portal.
* Open the AI Search service previously created.
* In the overview page, click on "Import data".
* Click on "Azure Blob Storage".
* Click on "RAG".

![Azure AI Search RAG import option](assets/03_02_import_data_rag_option.png)

## Step 3.3 — Connect the Blob Storage data source

* Select the subscription.
* Select the Storage Account created previously.
* Select the Blob container created previously.
* In Blob folder, enter the name of the directory where the uploaded documents are stored.
* For Parsing mode, choose "Markdown (Preview)" because the source documents are Markdown files.
* Leave deletion tracking unchecked.
* Check "Authenticate using managed identity".
* Choose "System-assigned" Managed identity type.
* Click Next.

![Connect Blob Storage data source](assets/03_03_connect_blob_storage_data_source.png)

## Step 3.4 — Configure text vectorization

* Change Kind from "Azure OpenAI" to "Microsoft Foundry".
* Select the subscription.
* Select the Foundry project previously created from the dropdown.
* Select the embedding model deployment previously created from the dropdown.
* For authentication type, choose System assigned identity.
* Check the acknowledgement for additional cost.
* Click Next.

![Configure text vectorization](assets/03_04_configure_text_vectorization.png)

## Step 3.5 — Configure advanced settings and create the RAG index

* On the Advanced settings page, keep "Enable semantic ranker" checked.
* Leave the index fields as default.
* Keep Schedule set to "Once".
* Click Next.
* On the Review and create page, review the settings.
* In Object name prefix, keep the default value or replace it with a short readable prefix for this demo.
* Click Create.
* Wait for Azure AI Search to create the data source, index, skillset, and indexer.
* Confirm that all four objects show successful creation.

![RAG index objects created](assets/03_05_rag_index_created.png)

## Step 3.6 — Verify the RAG index

* Go back to the Azure AI Search service.
* In the left menu, go to Search management -> Indexes.
* Open the index created in Step 3.5.
* Confirm that the document count is greater than 0.
* Confirm that vector index quota usage is greater than 0.
* This verifies that the documents were indexed, chunked, and vectorized.

![RAG index document count and vector usage](assets/03_06_index_document_count_vector_usage.png)
