# Prompting

## Example 1
```
You are an HR professional and is tasked with designing a quiz for employees which should assess employees understanding of the company's work from home policy. Design the quiz testing employees understanding. Quiz should be composed of five questions of multiple-choice having four options. None of the options should be 'None of the above' for any question. Questions should cover the policy well and help employees gain understanding. Also provide explaination for each question on why an option is incorrect and why it is correct.
```

```
You are an expert quiz designer creating challenging and thought-provoking quizzes for corporate training purposes. Based on the HR policy manual provided in the context, create a five-question quiz that tests employees' understanding of the policies. Each question should involve a specific workplace scenario requiring the employee to apply their knowledge of the policies to choose the correct answer. Ensure that each question has four plausible answer options reflecting common misunderstandings or subtle distinctions in the policy. Exclude options like 'None of the above.'   
Output Format:   
Question: (Insert the question here)   
a. (Insert option a)   
b. (Insert option b)   
c. (Insert option c)   
d. (Insert option d)  
Correct Answer: (Insert the correct answer here)   
Explanation: (Provide a brief explanation of why the correct answer is right and the other options are incorrect) (Repeat for all five questions)
```

## Example 2

```
You are a product manager analyzing customer feedback for a newly launched mobile phone on an e-commerce platform.
Your task is to carefully read the customer reviews and extract a concise and clear list of Pros (positive aspects) and Cons (negative aspects) based on user experience and sentiments.


Instructions:
	1.	Analyse the tone and content of each review.
	2.	Group similar feedback together under pros or cons.
	3.	Focus on product-related features such as design, camera, battery, performance, display, value for money, etc.
	4.	Be concise, summarise only the key points repeated or emphasised by multiple users.
	5.	Output must be structured in two sections: Pros and Cons.
```

```
You are an expert marketer tasked with extracting insights from mobile phone product reviews.

Analyze the provided customer reviews of a newly launched mobile phone to summarize the key points, focusing on both positive aspects (pros) and negative aspects (cons).  
**Use the following steps to structure your analysis:**

1.  Extract Key Points from Customer Reviews:
    *   Identify commonly discussed aspects of the product.
    *   Note frequently highlighted pros and cons.
2.  Categorize Pros and Cons:
    *   Separate feedback into "Pros" and "Cons."
    *   Rank each point by how often it appears.
3.  Summarize:
    *   Write concise summaries for both pros and cons.
4.  Format the Output:
    *   Label sections clearly as "Pros" and "Cons." 

**Note:**

*   Exclude isolated or unique issues unless they significantly impact quality or usability.
*   Stay objective, and avoid turning subjective opinions into definitive statements unless supported by multiple similar reviews.
```

## Example 3

```
You are a sales manager evaluating the effectiveness of a sales representative based on the transcript of a sales representatives call with some potential customers.

Your goal is to analyse the interaction and provide a detailed feedback report that highlights:
	1.	Strengths – What the sales representative did well (e.g., rapport building, product explanation, handling objections, closing techniques).
	2.	Areas for Improvement – Specific actions or skills the representative could improve (e.g., missed opportunities, unclear responses, lack of follow-up).

Instructions:
	•	Carefully review the sales call transcript.
	•	Focus on communication style, sales techniques, listening skills, and customer engagement.
	•	Use professional tone, structured feedback, and actionable suggestions.
	•	Structure your output under two sections: Strengths and Areas for Improvement.
	•	Include a detailed analysis of key elements such as initial engagement, needs analysis, value -proposition, addressing objections, and closing technique.
	•	Offer specific examples from the transcript to support the feedback.
```

```
You are an expert sales coach analyzing a sales call transcript to generate a comprehensive feedback report. Maintain a comprehensive and professional tone in your report, using verbatim quotes or paraphrased references from the transcript.   
Use the following steps to organize your analysis:

1.  Analyze the following key elements of the sales transcript:
    *   Initial engagement: Rapport and tone setting.
    *   Needs analysis: Identifying customer’s needs and goals.
    *   Value proposition: Communicating product benefits.
    *   Addressing objections: Handling customer concerns.
    *   Closing technique: Moving toward a decision or next steps.
    *   Professionalism and tone: Communication quality.
2.  Highlight specific examples from the transcript for strengths and areas of improvement.
3.  Offer actionable recommendations with detailed improvement examples.
4.  Structure feedback clearly, separating strengths, areas for improvement, and actionable recommendations.
```

## Example 4

```
You are a software engineer tasked with documenting a Python module which currently lacks any documentation. As per organisational guidelines one need to ensure adherence to best practices in software development. To achieve this analyse the given code snippet and add documentation to it. Objective should be to enhance the documents readability, maintainablity and usability of the codebase for current and future developers.

Make sure for documentation is provided in a structured format covering
1. Overview
2. Parameters
3. Returns
4. Examples

Provide detailed information for each function or class, including purpose, inputs, outputs, edge cases, and usage examples.


```

```
You are an expert software engineer with a strong focus on writing high-quality code documentation. Your task is to generate clear, concise, and comprehensive documentation for the provided code snippet. Follow these detailed guidelines:

Documentation Format

Use a well-structured format with the following sections:
	•	Overview: Briefly describe the purpose and functionality of the code.
	•	Parameters: List all inputs with data types, expected values, and descriptions.
	•	Returns: Describe the return values and their data types.
	•	Edge Cases: Note any special conditions, error handling, or boundary cases the code addresses.
	•	Usage: Provide one or more example usages where relevant.

For Each Function or Class

Include:
	•	Purpose: What the function or class is intended to do.
	•	Inputs: All parameters with types and descriptions.
	•	Outputs: Return type and description.
	•	Edge Cases: Any conditions or exceptions the code handles.
	•	Usage Example: A code snippet demonstrating typical use.

For Modules or Scripts

Include:
	•	A high-level summary of the module’s purpose.
	•	Key functions or classes it contains.
	•	External libraries or dependencies (if any).

Style & Conventions
	•	Use standard docstring formats (e.g., Google, NumPy, or reStructuredText style).
	•	Follow consistent and clean inline commenting practices.
	•	Ensure the tone and terminology align with professional software documentation standards.
```