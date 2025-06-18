# Gen AI

- Prompt engineering is also referred to as in-context learning.

## 🧠 GenAI Concepts: Cost Awareness and Token Efficiency in LLMs

When designing GenAI-based solutions, especially those involving Large Language Models (LLMs), it’s important to balance accuracy, performance, and cost-effectiveness. Even the most accurate model may be unsuitable if it incurs excessive operational cost for the business.


## 💰 Why Cost Matters in GenAI
	•	LLMs like GPT-4 or Claude charge based on token usage, not just API calls.
	•	Tokens are chunks of words or characters. Each word in your prompt or response consumes tokens.
	•	The more tokens your application uses per request, the higher the cost.

🔍 Example:
A classification system that processes thousands of product descriptions daily must optimize token usage to remain affordable in the long run.

⸻

🛠 Measuring Token Usage with tiktoken

To manage cost, we must measure how many tokens each prompt or response uses.

```
import tiktoken

def count_tokens(prompt, model="gpt-3.5-turbo"):
    encoding = tiktoken.encoding_for_model(model)
    return len(encoding.encode(prompt))

# Example
prompt = "Classify this product: Apple iPhone 15 Pro Max"
print("Tokens used:", count_tokens(prompt))
```
Understanding token consumption is crucial when deciding which prompting technique to use.

⸻

🎯 Choosing the Right Prompting Strategy

LLMs offer different prompting strategies, each with different token requirements and accuracy tradeoffs:

| Prompting Style         | Token Usage | Accuracy | Notes                     |
|-------------------------|-------------|----------|---------------------------|
| Zero-shot               | Low         | Medium   | Fast and cost-efficient   |
| Few-shot                | Medium      | High     | Examples improve accuracy |
| Chain-of-Thought (CoT)  | High        | Highest  | Best for reasoning tasks  |

🚨 Observation:
	•	cot_fewshot uses the most tokens.
	•	few-shot uses more than zero-shot.
	•	For large-scale tasks, reducing token usage while maintaining accuracy can yield substantial cost savings.

⸻

⚖️ Evaluation Metrics

For this classification problem (with a balanced dataset), we can use accuracy as the primary metric.

If your dataset were imbalanced, consider using precision, recall, or F1-score instead.

Also remember: since this is a perpetual task (e.g., daily classification of new products), efficiency is not optional—it’s essential.

⸻

🧪 Gold Examples
	•	Gold examples refer to unseen examples—data not previously exposed to the LLM during prompt training or fine-tuning.
	•	They’re used for evaluation to measure real-world model performance.

⸻

🧠 Semantic vs Lexical Evaluation
	•	BERTScore is better for semantic similarity — it captures meaning.
	•	ROUGE is better for lexical overlap — it measures common word matches.

Use these tools depending on what kind of evaluation you’re aiming for.

⸻

💡 Summary Generation: Cost-Efficient Approach

If you’re using two LLMs (e.g., GPT-3.5 and GPT-4) for tasks like summary generation and evaluation:
	•	✅ Use the older/cheaper model for generation (e.g., GPT-3.5).
	•	✅ Use the newer/more accurate model for evaluation (e.g., GPT-4).

This approach:
	•	Reduces cost.
	•	Maintains high evaluation reliability.
	•	Balances performance with practicality.

⸻

✅ Key Takeaways
	•	Token usage directly affects cost.
	•	Measure and optimize token use with tiktoken.
	•	Choose prompting techniques based on both accuracy and efficiency.
	•	Always evaluate models on gold (unseen) examples.
	•	Understand the tradeoff between semantic and lexical evaluation metrics.
	•	For generation tasks, prefer cheaper models for generation and stronger models for evaluation when cost is a concern.

https://console.groq.com/login

## TODOs
- [ ] What is Azure AI Foundry?
- [ ] What does Azure AI Foundry offers?
- [ ] ROUGE and BERT for content summarization
- [ ] What is LLM as a judge (Ground truth)
- [ ] https://openai.com/index/whisper/
- [ ] https://github.com/openai/whisper/blob/main/model-card.md
