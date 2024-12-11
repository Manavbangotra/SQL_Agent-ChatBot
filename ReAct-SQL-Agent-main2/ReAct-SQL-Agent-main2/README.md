# ReAct-SQL-Agent

This is intended to be a proof of concept for a ReAct Agent that works in text to sql scenario.

For the code in React SQL Agent, it is without memory. I have tested it with the following groq models:

| Model | Performance | Details |
|-------|-------------|---------|
| llama-3.1-70b-versatile | Success | Got answer in 10 iterations |
| llama3-70b-8192 | Success | Got answer in 5 iterations |
| llama3-8b-8192 | Partial | Partial answer |
| gemma2-9b-it | Partial | Partial answer, couldn't extract year of joining |
| mixtral-8x7b-32768 | Failure | No answer |
| llama-3.1-8b-instant | Failure | No answer |
| gemma-7b-it | Failure | No answer |
| distil-whisper-large-v3-en | Failure | Doesn't support chat completions |
| llama-3.2-1b-preview | Failure | Got stuck in Agent Executor chain, no answer |

I had also tested it with Openai's gpt-4o, it worked flawlessly. You can also pass the parameter max_execution_time=10, when you are testing with Openai models, as they have no problem with it. But be aware that, when you pass the same parameter when you are using Groq's models you will get Agent terminated due to limit or iteration time error, use them without this parameter.

#  ReAct SQL Agent with Memory

For ReAct SQL Agent with memory, I had tested them with groq models, but the best groq model currently llama 3:70b & its flavours couldn't detect the memory even if it was in the execution chain(agent executor). I will upload a version that works with them soon.

# ENVIRONMENT DEPENDENCIES:

## LANGCHAIN=0.3.0
## PYDANTIC=2.9.2
## PYTHON=3.10.15
