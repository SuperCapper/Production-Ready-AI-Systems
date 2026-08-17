# Initial strategic decisions

Source: https://www.ibm.com/docs/en/watsonx/saas?topic=solution-initial-strategic-decisions

Before you start planning your generative AI or machine learning solution, you must make some key strategic decisions. Your strategy must account for your organization's requirements and priorities, the skills and preferences of your development team, your data requirements, and the solution requirements.

To set the strategy for implementing your AI solution, make the following decisions:

- [What is your use case](#what-is-your-use-case)
- [Whether to implement gen AI or machine learning](#whether-to-implement-gen-ai-or-machine-learning)
- [Who to involve](#who-to-involve)
- [How to manage risk and compliance](#how-to-manage-risk-and-compliance)
- [How much to automate versus code](#how-much-to-automate-versus-code)
- [How to choose foundation models for gen AI](#how-to-choose-foundation-models-for-gen-ai)
- [How to prepare data for gen AI](#how-to-prepare-data-for-gen-ai)
- [How to evaluate quality and mitigate risk](#how-to-evaluate-quality-and-mitigate-risk)
- [How to optimize and manage foundation models](#how-to-optimize-and-manage-foundation-models)
- [How to deliver and maintain your solution](#how-to-deliver-and-maintain-your-solution)

## What is your use case

Understand the goal of your solution, whether that goal is feasible and valuable, and how you can determine when your solution is ready:

**AI task**
What do you need the model to do?

**Feasibility**
Understand the limits of AI so that you can evaluate whether your use case is feasible.
- `Gen AI` For example, you can check foundation model benchmark scores for the type of use case that you want to implement.
- `ML` For example, to train a machine learning (ML) model, you need enough high-quality labeled data for an algorithm to make accurate predictions or classifications.

**Business value**
Consider whether the benefits of the solution are greater than the cost of running the solution.

**Success criteria**
Decide how to measure whether the solution is successful. For example, you can rely on evaluation metrics or user feedback from target users.

## Whether to implement gen AI or machine learning

The type of data that you plan to work with and what you want to do with that data can help you decide whether you need machine learning or generative AI.

**Type of data**
Whether the data that you want to process with AI is structured or unstructured can often indicate which type of AI you need:
- Structured: If your labeled datasets are in tabular format, you probably need machine learning.
- Unstructured: If you have large amounts of documents or other types of unstructured data, you probably need generative AI.

**Type of goal**
Whether you want to analyze your data with mathematical algorithms or generate new content indicates which type of AI you need:
- Analyze your data: If you want to use mathematical and statistical equations to analyze structured data, then you need machine learning. For example, with machine learning, you can make predictions, detect patterns, and solve optimization problems.
- Generate content: If you want to generate or process unstructured content, then you need generative AI. For example, with gen AI, you can summarize, classify, translate, transform, and generate text or code.

### More information about the difference between ML and gen AI

- Foundation model architecture

## Who to involve

If you involve the appropriate stakeholders from the beginning, you have less risk of needing to change direction or repeating parts of the process. At a minimum, involve stakeholders from these teams in the planning process:

**People who define your organization's priorities and processes**
You need these people to tell you about requirements and restrictions that you must abide by. You might need to document specific information about your solution, follow a workflow to comply with a regulation, or select a foundation model with a specific type of source. For example, your organization might require that you select an open source foundation model.

**People who use the solution**
You need these people to define the requirements of the solution and to help test and validate that the solution works in their processes.

**People who create the solution**
You need these people involved in design and operational decisions. This team of collaborators might include designers, data engineers, AI engineers, data scientists, and risk and compliance managers.
- `Gen AI` For example, if you are implementing a retrieval-augmented generation (RAG) solution on your documentation, consider including your content writers, who can adapt the content for AI.
- `ML` For example, if you are implementing a mortgage application solution, ensure that you involve risk and compliance managers.

## How to manage risk and compliance

If you understand your risks and compliance needs before you start developing your solution, you can be better prepared for audits later.

**AI-related risks**
Understand key risk dimensions like reputational, regulatory, and operational risk. Many risks are the same for using generative AI and machine learning models, but some risks are amplified by generative AI, and other risks are specific to generative AI.
- `Gen AI` For example, a foundation model might generate output that contains factually inaccurate or untruthful content, which is referred to as hallucinating.
- `ML` For example, your machine learning model might show a tendency to provide favorable outcomes more often for one group over another.

**Legal and regulatory compliance**
Determine which laws and regulations you must comply with, the methods for tracking compliance, and the methods for ensuring compliance. For example, your organization might require a formal risk assessment or an approval workflow for AI solutions.

**Use case documentation**
Create an AI use case to gather all of the information for managing a model or prompt template from the request phase through development and into production. Documenting your use case provides a convenient way to track your progress whether your organization requires it for regulatory purposes.

### More information about risk and compliance

- AI risk atlas
- Managing risk and compliance
- Governing assets in AI use cases

## How much to automate versus code

You and your development team can choose between different tools and methods in the watsonx.ai user interface or to work entirely with code:

**Coding language**
If you want to write code, you can choose between REST APIs, Python, and Node.js code. Factors for choosing the language include the preference and skills of your developers, how you want to deploy the solution, and how much work your team wants to do in their interactive development environment (IDE) versus the watsonx.ai user interface.

**Level of automation**
You can choose how much of your solution code is generated for you:
- No code: You can complete all prompt engineering, model tuning, and document embedding and vectorizing tasks with tools.
  - `Gen AI` For example, you can automate the search for the best RAG pattern with AutoAI for RAG, create a prompt template in the Prompt Lab, and build an AI agent in Agent Lab.
  - `ML` For example, you can automate the search for the best data algorithms, transformations, and parameter settings with AutoAI for machine learning to create the best predictive model. You can develop predictive models on a graphical canvas with SPSS Modeler.
- Some code: You can generate Python notebooks with many tools and then adapt the code as needed.
  - `Gen AI` For example, you can generate a notebook based on a prompt template, for embedding and vectorizing documents, or for implementing an AI agent.
  - `ML` For example, you can solve a prescriptive analytics problem with a Decision Optimization notebook.
- All code: You can write code with REST APIs in your IDE. You can write and run code with Python libraries with the notebook editor.

**Functionality**
Most of the watsonx.ai functionality is available both with tools in the user interface and with code, such as APIs and SDKs.

### More information about working methods

- Comparison of working with tools and code
- watsonx Developer Hub

## How to choose foundation models for gen AI

You don't need to choose foundation models before you make a plan for your gen AI solution. However, if you understand which criteria are most important to you and your organization, you can reduce the risk of selecting an inappropriate foundation model. For some types of generative AI solutions, you need multiple models with different capabilities. For example, a RAG solution can include models for inferencing, extracting text from documents, vectorizing documents, and reranking search results.

**Task**
The task that you want the foundation model to do can be a limiting factor for choosing a foundation model. For many gen AI tasks, you can choose between many foundation models. However, for other gen AI tasks, such as translation or vectorizing documents, you have fewer choices.

**Cost**
The cost of inferencing varies among foundation models. If keeping costs low is a priority for you, choose a cheaper foundation model, a smaller foundation model, a quantized foundation model, or a foundation model that you can tune.

**Environmental impact**
In general, larger models have a larger environmental impact during both training and inferencing. Smaller foundation models and quantized foundation models have a smaller environment impact.

**Accuracy and other scores**
You can compare foundation model benchmarks and choose the foundation model that has high scores in the areas that are most important to you.

**Indemnity and model origin**
Your organization might have policies about choosing foundation models that are transparent about their training data, are open source, or that offer indemnity.

**Customization**
You can customize a foundation model for a specific domain by tuning it. You can choose to tune some foundation models that are provided with watsonx.ai in the Tuning Studio or programmatically. Alternatively, you can tune a foundation model in an external tool and import your custom foundation model into watsonx.ai.

If you want to deploy foundation models in your own data center, you can purchase and install watsonx.ai software.

### More information about choosing a foundation model

- Supported foundation models
- Choosing a foundation model
- Foundation model benchmarks
- Methods for tuning foundation models
- IBM watsonx.ai software

## How to prepare data for gen AI

Foundation models are trained on large amounts of data, but not on your internal company data. If you need a foundation model to know your company data, you must decide how to provide your data to the model.

**Knowledge base**
If you need a solution that answers questions by grounding the model with the information in your knowledge base of documents, you can set up a RAG pattern. In a RAG pattern, you vectorize your documents for efficient retrieval of passages that answer user questions.

**Tuning and testing data**
If you need to improve or tailor the output for natural language processing tasks such as classification, summarization, and generation, you can tune the foundation model. If you want to test the quality of your prompt, you can evaluate it with generative AI metrics. For both tasks, you must provide a set of validated prompt input and output examples. If your data contains any sensitive information, such as personally identifiable information (PII), make sure that you know your organization's policy about PII. For example, you might need to mask PII or generate synthetic data for tuning or testing your foundation model.

### More information about data preparation for gen AI

- Retrieval-augmented generation
- Tuning Studio
- Generating unstructured synthetic data

## How to evaluate quality and mitigate risk

You must decide how to measure quality and ensure safety.

**Evaluation**
You can evaluate solution performance and risks against industry-standard metrics. These metrics help you to ensure that AI solutions are free from bias, can be easily explained and understood by business users, and are auditable in business transactions.
- `Gen AI` You can measure the textual accuracy, similarity, and quality of foundation model output. You can also evaluate fairness, performance, and drift of model output. You can evaluate the performance of multiple assets simultaneously and view comparative analyses of results to identify the best solutions.
- `ML` You can monitor your machine learning model deployment results for fairness, quality, drift, and explainability.

**Risk assessment**
You can identify potential risks by completing a risk assessment questionnaire.

**Guardrails**
`Gen AI` You can enable guardrails to remove potentially harmful content or PII content from both input and output text in prompts.

**Testing**
Consider setting up a red team to emulate adversarial attacks.

### More information about evaluating quality and mitigating risk

- Generative AI quality evaluations
- Evaluation Studio
- Removing harmful content
- Evaluating machine learning deployments
- Completing a risk assessment

## How to optimize and manage foundation models

You can optimize a foundation model that is deployed on watsonx for accuracy, cost, inferencing latency, and control of the model lifecycle.

**Default optimization**
IBM provides a set of foundation models that are deployed on multi-tenant hardware. You pay for inferencing per token. IBM controls the model lifecycle by updating and deprecating models. When a model is deprecated, you must update your solution to inference the new version of the model or a different model.

**Optimize for accuracy and cost**
If you need to improve the accuracy of your prompt and reduce costs by inferencing a smaller foundation model, you can tune a provided foundation model. You deploy a tuned model on multitenant hardware and pay for inferencing per token.

**Optimize for accuracy and control**
If you trained or tuned a model externally to watsonx.ai for your use case, you can import and deploy a custom model. You deploy the model on dedicated hardware. You pay per hour for hosting the model instead of for inferencing. You control the model lifecycle.

**Optimize for latency and control**
If your solution must support a high number of concurrent users, you can deploy a deploy-on-demand model that is provided by IBM on dedicated hardware. Dedicated hardware provides lower latency than multi-tenant hardware. You pay per hour for hosting the model instead of for inferencing. You control the model lifecycle.

Alternatively, you can access models that are deployed on other platforms through the model gateway. You optimize the models on the other platform.

### More information about optimizing and managing foundation models

- Tuning Studio
- Foundation model lifecycle
- Deployment method comparison
- Planning to deploy custom foundation models
- Accessing models through the model gateway

## How to deliver and maintain your solution

You must decide how to deliver your gen AI solution and help ensure its continued quality.

**Deploying your solution**
You deploy your AI asset in a deployment space and then retrieve the deployment endpoint to call your AI solution in your application.
- `Gen AI` For inferencing a foundation model, the endpoint to inference the model might be in a code snippet, a Python function, an AI service, or code that your team developed.
- `ML` For a machine learning solution, the endpoint might be for a machine learning model, a Python function, an R Shiny application, an NLP model, or a script.

**Managing ModelOps with deployment spaces**
You can support a ModelOps flow by creating separate deployment spaces for testing, staging, and production versions of your solution. You can manage access to your production solution by adding the appropriate collaborators to each space.

**Orchestrating ML pipelines**
`ML` You can assemble and configure a pipeline to create, train, deploy, and update machine learning models and Python scripts.

**Monitoring**
Similar to evaluating your solution during development, you can monitor solution performance and risks, such as fairness, quality, and explainability. You can view trends over time and set thresholds to alert you when performance dips.

**User feedback**
Consider implementing a user feedback mechanism and creating a process for gathering that feedback and improving your solution with it.
`Gen AI` For example, if you implement a RAG pattern, you can add a feedback mechanism for users to evaluate the answers to their questions. You can set up a process to evaluate incorrect and inadequate answers and either adapt the RAG pattern or adapt your content to provide better answers.

### More information about delivery and maintenance

- Deploying foundation model assets
- Deploying machine learning assets
- Evaluating AI
- Managing the AI lifecycle with ModelOps
- Orchestrating tasks with Orchestration Pipelines

## Learn more

- Comparison of tools to code
- Planning the implementation workflow for your generative AI solution
- Planning the implementation workflow for your machine learning solution
