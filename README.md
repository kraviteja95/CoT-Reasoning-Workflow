# Workflow for "Chain-of-Thought Reasoning Without Prompting"

## Introduction
- The paper "Chain-of-Thought Reasoning Without Prompting" by Xuezhi Wang and Denny Zhou explores a novel way to trigger chain-of-thought (CoT) reasoning in large language models (LLMs) instead of using traditional explicit prompting mechanisms. 
- CoT reasoning has normally been prompted via few-shot or zero-shot prompting, which has been demanding of careful prompt engineering. 
- The researchers suggest a new way by augmenting the process of decoding at text generation level to reveal naturally occurring CoT reasoning paths native to LLMs.

## Objective 
- The goal/objective is to unpack and organize the discussion in the paper to show how Chain-of-Thought (CoT) reasoning can be elicited without explicit prompting.

## Key Concepts:
### Standard Decoding vs. CoT-Decoding: 
- In standard cases, LLMs apply greedy decoding, choosing the top-most likely token at every step, which is not always guaranteed to result in complete reasoning paths. 
- The authors suggest investigating other top-k tokens during decoding to uncover hidden CoT reasoning sequences that could be missed with greedy decoding.

### Intrinsic Reasoning Skills: 
- By varying the decoding strategy, the work attempts to measure the LLMs' native reasoning skills independently of external inputs, giving a better idea of their capabilities.

### Confidence Correlation: 
- Having a CoT in the decoding sequence is linked with greater confidence in the final answer of the model. 
- The confidence measure does a good job of distinguishing between CoT and non-CoT sequences.

## Workflow Overview
I have attached the workflow in the draw.io file. Please find the same to understand about it diagrammatically.

The workflow consists of four major steps: 
### 1. Input Processing

#### 1.1. User Query
- The model receives a question that requires multi-step reasoning.
- Example Input Formats would be: `Q: [complex reasoning question] A:` , `Q: [question]\nA:`

#### 1.2. Tokenization & Initial Processing
- The input question is tokenized and prepared for the model.
- No explicit CoT prompting is provided.

### 2. Decoding Strategy

#### 2.1. Standard Decoding vs. CoT Decoding
- Standard Decoding (e.g., greedy decoding) chooses the most likely next token at every step.
- This technique instead alters decoding to investigate alternative reasoning routes by sampling top-k tokens at every step.

#### 2.2 Generating Multiple Reasoning Paths
- The model generates multiple sequences by allowing exploration of different paths.
- This helps uncover implicit CoT reasoning.

### 3. Confidence Evaluation

#### 3.1 Scoring Generated Paths
- Each sequence is given a confidence score depending on probability distribution.
- More confident paths typically have higher-quality CoT reasoning.

#### 3.2 Filtering Low-Confidence Paths
- Reject paths of low confidence.
- Keep paths that have structured reasoning and logical consistency.

### 4.Final Answer Selection

#### 4.1 Selecting the Best Path
- The path with the highest confidence is chosen.
- The final response is created based on this path.

#### 4.2 Output Generation
- The selected/chosen response is formatted and output to the user.
- Example Output Format: `A: [CoT reasoning steps] -> [Final Answer]`
## Conclusion
- This workflow shows one way to elicit Chain-of-Thought reasoning by changing the decoding procedure instead of through explicit prompting. 
- By venturing down many possible reasoning pathways and choosing the best one, the model is able to produce formal, rational answers without needing hand-tuned prompt engineering.
