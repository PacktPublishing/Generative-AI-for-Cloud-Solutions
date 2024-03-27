#### Building a RAG workflow on Azure Prompt Flow

Learn how to build rag-based prompt flow orchestrations for your Gen AI App.

#### Prerequisites

An Azure subscription where you can create an AI Hub Resource and a AI Search service.

Apply for an Azure Open AI subscription - [Request Access to Azure OpenAI Service (microsoft.com)](https://customervoice.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR7en2Ais5pxKtso_Pz4b1_xUNTZBNzRKNlVQSFhZMU9aV09EVzYxWFdORCQlQCN0PWcu)

#### Setup

Create an AI Project and AI Hub Resouces
Let's start by creating a project in AzureAI Studio.
Go to your browser and type: https://ai.azure.com
After logging in with your Azure account, you will see the following screen:


<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/726aeab4-0f7b-4373-b209-ea2b79498307">


In the Build tab, select New AI project to create a project.
Choose an unique name for your project.

<img width="900" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/3ee512c0-6a74-4721-ab79-2faad798fecf">

Select the Create a new resource link and choose a name for your AI hub where your project resources will be created.

<img width="900" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/70401647-732d-4b6f-ad82-58143b246f78">

Note: Choose the region where the GPT-4 models and text-embeddings-ada-002 are available.
Still on this screen, select the Create a new Azure AI Search option; this service will be used in the following lessons.

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/7e1a1453-6172-44a4-869e-43cd6c644e38">

Finally, select Create a project for the creation of resources to be used in your project.

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/c214dbc1-abf8-4406-a5bf-7221c9fd7abe">
<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/7f804228-a5ce-4fd2-97bd-ab802ea6f903">


   
#### Deploy an Azure OpenAI model

After creating your AI Project, the first step is to create a deployment of an OpenAI model so you can start experimenting with the prompts you will use in your application.
To do this, access your newly created project in the Build tab of the AI Studio, select the Deployments option, and click on Create (Real-time endpoint).

<img width="620" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/1ea8711f-38bb-41f9-94e8-39cdc07c620c">

From the list of models, select gpt-4

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/988e4399-900e-4743-8f33-c4332506863d)


On the next screen, define the name of the deployment, in this case, you can use the same name as the model and in the version field select the latest available version, in the example below we chose version 1106-Preview (gpt4).

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/0c87cabc-4724-4c7b-8686-b0fda106d0c9">



Click on Advanced Options and select at least 40K Tokens per Minute Rate Limit* to ensure the flows run smoothly/
Now, just click on Deploy and your model deployment is created. You can now test it in the Playground.

#### Lab Steps

During this lab, we will cover the following steps to create a conversational RAG flow.



##### Create a conversational RAG flow

Now you will create a conversational flow using the RAG pattern, start by creating a new flow in the **Prompt Flow** item in the **Tools** section within the **Build** tab. If you see a list of projects, select your project first and then go to Tools Section on the left.

Select the **Multi-Round Q&A** on Your Data template after clicking the **Create** button.

<img width="900" alt="imae 1" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/8f7471a8-e311-4e10-9a91-ddd016dba748">


Click on the **Clone** button. A flow with the following structure will be created.

<img width="571" alt="image 2" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/6383d387-8192-4406-9893-b7577e035229">



Start the automatic runtime by selecting **Start** in the **Runtime** drop down. The runtime will be useful for you to work with the flow moving forward.


<img width="817" alt="image03" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/8c1e7ebd-b828-4b35-8444-a2a3c3935466">



Click the **Save** button to save your flow.

###### 1) Flow overview

The first node, `modify_query_with_history`, produces a search query using the user's question and their previous interactions. Next, in the `lookup` node, the flow uses the vector index to conduct a search within a vector store, which is where the RAG pattern retrieval step takes place. Following the search process, the `generate_prompt_context` node consolidates the results into a string. This string then serves as input for the `Prompt_variants` node, which formulates various prompts. Finally, these prompts are used to generate the user's answer in the `chat_with_context` node.

###### 2) Search index

Before you can start running your flow, a crucial step is to establish the search index for the Retrieval stage. This search index will be provided by the Azure AI Search service.

The AI Search service was originally created in the **Setup** section of this lab. If you have not yet created the Search service, you will need to set one up as explained below. With the search service created, you can now proceed to create the index.

In our case, we will create a **Vector index**. To do this, you just need to go back to the project in the **AI Studio**, select the **Indexes** option, and then click on the **New index** button.  
   
![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/342ab7d3-fc77-43dc-b1ab-4f77f4336858)

   
At the `Source data` stage, select the `Upload files/folders` option and upload the PDF `files/surface-pro-4-user-guide-EN.pdf` to the data folder of this lab, as shown in the next screen.

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/fe177a1e-8fc1-446a-a6b6-d46f7de26876)

   
In `Index storage`, select the Search Service you created earlier.  

> If someone has created the AI Search service for you, you can also use it to create the index. Simply select it in the **Select Azure AI Search service** option.

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/ac73488e-44c1-4d5e-a7e9-548ba7b80277">

   
Under `Search settings`, select **Add vector search to this ...** as indicated in the following image.  
   
![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/8e3e8f82-01cc-4069-bdec-146862c8dc0f)

In `Index settings`, keep the default options as indicated below.  
   
<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/704d1845-88c1-42b2-8ce6-101255b41b29">

   
> Note: If you want to select a virtual machine configuration, click on the **Select from recommended options**. If you don't select, the default configuration will use serverless processing.

Great, now just click on the **Create** button at the `Review and finish` stage.  
   
The indexing job will be created and submitted for execution, so please wait a while for it to complete.

It may take about 10 minutes from the time it enters the execution queue until it starts.  
   
Wait until the index status is `Completed` as in the next image, before proceeding with the next steps.  
   
<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/88098744-7eeb-40af-b109-495544cd2995">


Done! You have created the index, as can be seen in the **Indexes** item of the **Components** section.

<img width="1127" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/25769b37-0c9a-4fc2-b4e7-dccd9bf5dac2">


Now return to the RAG flow created in **Prompt flow** to configure the `lookup` node.

After selecting the `lookup` node, click on `mlindex_content`.


A **Generate** window will appear. In this window, select the `Registered Index` option from the `index_type` field. Then, choose version 1 of the index you just created. After making these selections, click on **Save**.

Now, let's go back to the `lookup` node. Select the `Hybrid (vector + keyword)` option from the query_type field, as shown in the subsequent image.

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/46a19098-42ec-486b-88bd-7130ec200a40">

###### 2.3) Updating connection information

Now you will need to update the Connections of the nodes that link with LLM models.  

Starting with the Connection in the `modify_query_with_history` node with the gpt-4 deployment, as indicated below:

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/57301370-0090-47f7-98ab-1dd397103f7c)

And the Connection for the `chat_with_context node` with the gpt-4 deployment, as indicated below:

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/03f1b610-f7f7-4461-a039-f33cc320efa5)

###### 2.4) Testing your RAG flow

Everything is now set up for you to initiate your chat flow. Simply click on the blue **Chat** button located at the top right corner of your page to begin interacting with the flow.

<img width="500" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/450bcf24-4aba-42e7-bdbd-5810c5546acb">


### Summary

In this lab you created a simple RAG Q&A workflow with Azure Prompt Flow, GPT-4 and Azure AI Search that extracted information from a pdf document which contained large amounts of unstructured data.
