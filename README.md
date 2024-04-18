# Generative AI for Cloud Solutions

<a href="https://www.packtpub.com/product/generative-ai-for-cloud-solutions/9781835084786?_gl=1*j7eztt*_gcl_au*NzkyOTIxOTY1LjE3MTI3MjM0MTE.*_ga*MTI3MTI1MDc3LjE3MDQ4NzY0MzU.*_ga_Q4R8G7SJDK*MTcxMjcyMzQxMC4zMC4xLjE3MTI3MjM0NjUuNS4wLjA."><img src="https://content.packt.com/_/image/original/B21443/cover_image_large.jpg" alt="no-image" height="256px" align="right"></a>

This is the code repository for [Generative AI for Cloud Solutions](https://www.packtpub.com/product/generative-ai-for-cloud-solutions/9781835084786?_gl=1*j7eztt*_gcl_au*NzkyOTIxOTY1LjE3MTI3MjM0MTE.*_ga*MTI3MTI1MDc3LjE3MDQ4NzY0MzU.*_ga_Q4R8G7SJDK*MTcxMjcyMzQxMC4zMC4xLjE3MTI3MjM0NjUuNS4wLjA.), published by Packt.

**Architect modern AI LLMs in secure, scalable, and ethical cloud environments**

## What is this book about?
Discover the potential of ChatGPT, harness cloud platforms for security and scalability, maximize the efficiency of your AI apps, and explore industry use cases to gain practical insights with the help of Generative AI for Cloud Solutions

This book covers the following exciting features:
* Get started with the essentials of generative AI, LLMs, and ChatGPT, and understand how they function together
* Understand how we started applying NLP to concepts like transformers
* Grasp the process of fine-tuning and developing apps based on RAG
* Explore effective prompt engineering strategies
* Acquire insights into the app development frameworks and lifecycles of LLMs, including important aspects of LLMOps, autonomous agents, and Assistants APIs
* Discover how to scale and secure GenAI systems, while understanding the principles of responsible AI

If you feel this book is for you, get your [copy](https://www.amazon.com/Generative-Cloud-Solutions-Architect-environments/dp/1835084788/ref=sr_1_1?dib=eyJ2IjoiMSJ9.-A1xdFAOgA1tbXpO39-8hwcgGfuj-g38E_hnPXrEQ_Ybq_Oon3y4B1rKHQfJLLqxEmDNeX9i9z3xwuo5DieNIsuWy057ycD6LST30rIuXbS3Q6SQgpEOzXmCnDfVG4SaV0N9C3dHRR49Mx4ORFGrAJ5dYeazXqvEup1CKSEHxf8b1PIO8b-g2CxIZcJI2L4l_RmamwJfp2ZOZD65jJ1ItrNtwAZ7oQPHKvKFVFWfBX8.gvYl9cpIOktECqpzgy6pvkMwDkTJkDmApbORbZzgozo&dib_tag=se&keywords=Generative+AI+for+Cloud+Solutions&qid=1713418664&sr=8-1) today!
<a href="https://www.packtpub.com/?utm_source=github&utm_medium=banner&utm_campaign=GitHubBanner"><img src="https://raw.githubusercontent.com/PacktPublishing/GitHub/master/GitHub.png" 
alt="https://www.packtpub.com/" border="5" /></a>
## Instructions and Navigations
All of the labs are organized into folders. For example, lab02-RAG.

The code will look like the following:
```
from langchain.text_splitter import (
    RecursiveCharacterTextSplitter,
    Language,
)
```

**Following is what you need for this book:**
This artificial intelligence book is for aspiring cloud architects, data analysts, cloud developers, data scientists, AI researchers, technical business leaders, and technology evangelists looking to understanding the interplay between GenAI and cloud computing. Some chapters provide a broad overview of GenAI, which are suitable for readers with basic to no prior AI experience, aspiring to harness AI's potential. Other chapters delve into technical concepts that require intermediate data and AI skills. A basic understanding of a cloud ecosystem is required to get the most out of this book.

With the following software and hardware list you can run all labs present on the GitHub Repository (Lab 1-5).
## Software and Hardware List
| Labs | Software required | OS required |
| -------- | ------------------------------------ | ----------------------------------- |
| 1-5 | Access to GitHub repository | Any modern device with internet access. |
| 1-5 | Microsoft Azure cloud subscription |    |

**Please Note:** To help go into depth on some of the more intricate concepts of this book, we have created additional hands-on labs. These labs are an optional addition, access to Github and, subsequelntly the Azure cloud is not required for this book. If you'd like to use some of the main ideas you have learned from the book, you can practice with these labs.

## Related products
* Unlocking the Secrets of Prompt Engineering [[Packt]](https://www.packtpub.com/product/unlocking-the-secrets-of-prompt-engineering/9781835083833) [[Amazon]](https://www.amazon.com/Unlocking-Secrets-Prompt-Engineering-generation/dp/1835083838/ref=sr_1_1?crid=1D2045NQZZO5R&dib=eyJ2IjoiMSJ9.C-nZZXjKeQLJI6RijMQoqe_PK3WhtdgqeOwv2tLgcoz0rMkHVsbWXq9Yz2tl9vRMR7K8oW0y0iXnalShX1HvtencRk45QT7JQLEUvnvC4i2Q3cJ47aMfiL0abHExiUiBEcXBPaLTixmwC9Qea0hRh6y5FKgvtJ7yz67--cING1AiVxh98wAPJ6MWcBKxw6VzJBRHQkHjlYI-loCuhfpba3hXC0Q4XVb0pCxyduEzrzs.whyv4jVRzFJzv0Jae1xJrRlEKybm_hcA2OrCQj9p3ak&dib_tag=se&keywords=Unlocking+the+Secrets+of+Prompt+Engineering&qid=1712726417&sprefix=generative+ai+for+cloud+solutions%2Caps%2C325&sr=8-1)

* Building AI Applications with ChatGPT APIs [[Packt]](https://www.packtpub.com/product/building-ai-applications-with-chatgpt-apis/9781805127567) [[Amazon]](https://www.amazon.com/Building-Applications-ChatGPT-APIs-DALL/dp/180512756X/ref=sr_1_1?crid=3JY42OYWE8MQC&dib=eyJ2IjoiMSJ9.SJP3cZoIwjaUNq1v-QkolGx4cAi742ZCeZfeacGJD6yx2DrhBxIgvlhbWkJNY4ijffStzMIC4DkBtdBszW00LyKmoMQ4VUU1yYFc8fb4A2PlGJO8y8lALeG6oeLHKsHqz-6XWgk5pVTY4XtszGNY8bjPb0To9FBiCJXtD1GwuPGPf5SjZplaB6UYF5OhwbhMm7WZY2IkY3cOOme4HQLiNsnor-tVzRZBP7yYTreF8Xg.EwigXI2gvNqGzwh1dcAl9gJ_7wUcVPu8qenoKAGS7LQ&dib_tag=se&keywords=Building+AI+Applications+with+ChatGPT+APIs&qid=1712726497&sprefix=building+ai+applications+with+chatgpt+apis%2Caps%2C319&sr=8-1)

## Get to Know the Authors
**Paul Singh**
 is currently a Principal Cloud Solution Architect (CSA), working at Microsoft for over 10 years. Having been selected as the very first ten CSA&rsquo;s the role was first created, Paul helped shape the role ever since, including being on the national hiring committee(s) as well as helping create the very first Azure Architecture Exam. Paul has earned many honors and awards along the way, while also gaining over 30 different technical certifications, and helping some of the largest Cloud customers with complex scenarios and solutions.

**Anurag Karuparti**
 is a seasoned Senior Cloud Solution Architect specializing in AI at Microsoft's Azure practice. Anurag holds a Master's degree in Information Management(Data Science) from Syracuse University, and has a background in Computer Engineering. With over 10 years of experience in the industry, Anurag has become a trusted expert in the fields of Cloud, data, and advanced analytics. Anurag holds multiple Azure Certifications and is certified across major cloud platforms. Throughout his career, he has successfully designed and implemented cutting-edge solutions, leveraging the power of artificial intelligence to drive innovation and transform businesses. Prior to joining Microsoft, Anurag gained valuable experience working as a manager in the Emerging Technologies practices of renowned consulting firms such as EY and PwC.
