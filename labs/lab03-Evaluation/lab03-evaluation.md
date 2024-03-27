#### Evaluating and Deploying RAG Workflow on Prompt Flow

The purpose lab is to understand how we can evaluate RAG workflows against groundtruth data using metrics like similarity, groundedness and relevance povided on Prompt Flow.

#### Prerequisites

This is a continuation of Lab 2. So please finish the Lab steps in Lab 2.


#### Lab Steps

In this Lab, you will execute the following steps:

1) Evaluate your Chat flow.

2) Deploy the RAG flow to an online managed endpoint.

##### 1) Evaluate your Chat flow

Go to your browser and type: https://ai.azure.com

Select the project created earlier and choose the **Prompt flow** item in the **Tools** section of the **Build** tab.

###### 1.1) Prepare you chat flow for evaluation

For the RAG flow that you created earlier to be evaluated, you must include additional information to the output node of this flow, specifically the context used to generate the answer.

This information will be used by the Evaluation Flow. To do this, just follow these steps:

In the Flows section of **Prompt Flow**, open the `packt-rag-lab02` flow that you created in the previous lab. This will be the flow we use for evaluation.

<img width="769" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/3fe0fa64-a2b6-4878-821f-294ef60e9775">

Create a new output named `documents` in the Outputs node. This output will represent the documents that were retrieved in the `lookup` node and subsequently formatted in the `generate_prompt_context` node.

Assign the output of the `generate_prompt_context` node to the `documents` output, as shown in the image below.

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/3f2f39fa-e007-4461-a49f-319b0945c6b6">


Click **Save** before moving to the next section.

###### 1.2) Create your evaluation flows

Still in the **Prompt flow** item in the **Tools** section of the **Build** tab, click on the blue **Create** button.

Select the **Evaluation Flow** filter and click on **Clone** on the **QnA Groundedness Evaluation** card.

<img width="724" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/76909761-3a4e-4b94-8155-fbcf7e0b75f3">

Click on the other **Clone** button to create a copy of the flow.

A flow will be created with the following structure:

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/a9b752c8-b495-4494-8ae6-5df4df2aa453)

Update the `Connection` field to point to a gpt-4 deployment in `groundedness_score` node also update max_tokens to `1000` as shown in the next figure.  
   
![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/c4071b3f-2886-4eb2-95f3-93f8a3602600)


After updating the connection information, click on **Save** in the evaluation flow and navigate to the Flows section in **Prompt Flow** item.

Now, you will repeat the same steps described so far in this **section 1.2** to create **two** additional evaluation flows, one `QnA Relevance Evaluation` and another `QnA GPT Similarity Evaluation`. The two images below show where these flows are in the prompt flow gallery.

> You will repeat **section 1.2** steps twice since you will need to create two additional evaluation flows.

> Note that the LLM nodes, where you will set the Azure OpenAI connection for each flow, have slightly different names: **relevance_score** and **similarity_score**, respectively.

QnA Relevance Evaluation:

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/4b962293-649b-45d2-b1b3-a60c4d3d8f57)



QnA GPT Similarity Evaluation:

![image](https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/d61c245f-8b4c-46d6-ab2c-89a81825cd1d)



###### 1.3) Run the evaluation

In the Flows section of **Prompt Flow**, open the `packt-rag-lab-02` flow that you created in the previous lab. This will be the flow we use for evaluation.

Start the automatic runtime by selecting **Start** in the **Runtime** drop down. The runtime will be useful for you to work with the flow moving forward.

<img width="714" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/2c37d626-77de-4162-b83e-583a8f5fc7a0">


Now select the **Custom evaluation** option in the Evaluate menu.

<img width="600" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/39054f2a-7dee-4620-807f-900843ae1ef0">


In the `Prompt_variants` option, select the option to run only **two variants** to avoid reaching your GPT-4 model quota limit, as shown in the example image below.

<img width="721" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/cc6e40e8-4957-4716-a5f0-425c5d2ad113">


Select **Add new data**.

Upload the file data.csv inside the lab_03 folder.

After clicking on **Add**  proceed to map the input fields as shown below: 

<img width="722" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/1ac2de94-e00a-4ed8-bcc0-797e9a491965">


Select the three evaluation flows you just created.

<img width="725" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/43f6f0c1-593b-436d-9f95-5eb4a29e7da5">



Great job so far! Now, let's move on to the next step. Click on **Next** to set up the `question`, `context`, `ground_truth` and `answer` fields for each evaluation flow. You can see how to do this in the three images below. Please take a moment to ensure you've selected the correct value - it's crucial for accurate metric calculation. Keep up the good work!

**QnA GPT Similarity Evaluation**

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/ae2bf6b5-e822-40df-a6c3-9128e2e85ef8">


**QnA Groundedness Evaluation**

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/65c08ca4-31f7-4e2b-b411-5c8000715a63">



**QnA Relevance Evaluation**

<img width="800" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/6c86daa0-208a-4127-909c-ab1d96d953d0">


Click on **Submit** to start the evaluation.

<img width="710" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/74f6e001-f51d-4c25-ba6a-60f916908ac3">


The evaluation process has started. To view all evaluations (one per variant), please navigate to the **Evaluation** section under the **Build** tab.

<img width="781" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/2e2f9a08-2e6c-4ddc-9985-5de2b4bb75c2">


Upon selecting specific evaluation results, you will have the ability to view their detailed information.

You can also select **Switch to dashboard view** to access a dashboard that provides a tabular and visual comparison between the rounds of different variations, as shown in the following images.

*Table comparison*

<img width="774" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/82802870-d11f-440d-83bf-21d046832d6f">


*Chart comparison*

<img width="600" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/69f4af18-53a7-4aa5-946e-e86d3ab09ed8">


##### 2) Deploy the RAG flow to an online managed endpoint

Open the **packt-rag-lab02** flow that you created in the previous lab.

After opening the flow, click the deploy button on the top 

<img width="824" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/cf505c18-401b-4350-9bc6-90e6462face7">


Click the **Create** button.

<img width="726" alt="image" src="https://github.com/PacktPublishing/Generative-AI-for-Cloud-Solutions/assets/12818726/e267f09d-f4a5-43d6-b6ce-6d508d7da8e4">

Then go to the deployments section on the left side of your UI to find your online endpoint. Then test the endpoint. 

## Summary
In this lab, we evaluated the RAG workflow that we created in Lab02. We compared the outputs to the ground truth data using metrics like relevancy, similarity and groundednes. Then we deployed the RAG workflow on an online managed endpoint. 




