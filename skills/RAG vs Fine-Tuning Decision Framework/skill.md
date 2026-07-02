# RAG vs Fine-Tuning Implementation Skill

## Overview
This skill enables you to systematically choose between RAG and fine-tuning approaches for generative AI applications. Learn the [Core Concepts](references/core_concepts.md) and apply the [Decision Framework](references/decision_framework.md) through concrete steps.

## Step-by-Step Workflow
1. **Requirement Analysis**
   - Document whether needs are knowledge-based (RAG) or behavior-based (fine-tuning)
   - Example: "Need answers from HR docs" → RAG; "Need empathetic response format" → fine-tuning

2. **Prototype Construction**
   ```python
   # RAG prototype pseudocode
   def rag_query(question):
       embeddings = embed_documents(company_docs)
       relevant_chunks = retrieve_similar(question, embeddings)
       prompt = f"Answer using only: {relevant_chunks}\n\nQuestion: {question}"
       return llm.generate(prompt)
   ```

3. **Behavior Gap Analysis**
   - Test if prompts alone achieve desired style/format
   - Example: "Even with perfect context, responses lack our brand voice" → fine-tuning signal

4. **Hybrid Implementation** (if needed)
   ```python
   # Hybrid architecture example
   def generate_response(question):
       # RAG component
       context = retrieve_company_docs(question)
       
       # Fine-tuned model call
       prompt = build_prompt(context, question, style="brand_voice_v2")
       return finetuned_llm.generate(prompt)
   ```

## Best Practices
1. **Start Simple**
   - 80% of use cases can start with RAG alone (per Practical GenAI findings)
   - Only add fine-tuning when measurable gaps exist

2. **Change Management**
   - RAG: Update documents → immediate effect
   - Fine-tuning: Requires retraining pipeline

3. **Validation**
   - For RAG: Implement citation checks and hallucination tests
   - For fine-tuning: Use style adherence metrics

## Common Pitfalls
1. **Premature Fine-Tuning**
   - Mistake: Fine-tuning when better retrieval would suffice
   - Example: "Our policy answers are wrong" → fix documents first

2. **RAG Overconfidence**
   - Mistake: Assuming RAG handles style requirements
   - Example: "Answers are factually correct but sound robotic" → needs fine-tuning

3. **Version Skew**
   - Risk: Fine-tuned models referencing outdated RAG documents
   - Solution: Implement joint version control

## Validation Steps
1. **RAG Validation**
   - Precision: % of cited content actually relevant
   - Recall: Can system find all policy variants?

2. **Fine-Tuning Validation**
   - Style adherence: Human evaluation of tone
   - Pattern compliance: Automated format checks

3. **Hybrid Validation**
   - Conflict detection: Does fine-tuning override factual RAG content?
   - Consistency: Do style rules apply equally across knowledge domains?

For complete implementation details, see the [Practical Guide](references/practical_guide.md).