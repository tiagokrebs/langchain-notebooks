## AI Gateway as a Langchain LLM
Usually simple LLM calls using Langchain are done like this:
```
from langchain_core.messages import HumanMessage
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o", temperature=0)
llm.invoke("Hey")
```
This is a good way to abstract the different models parameters and calling methods from the agent logic and make them easily swappable.

Due to compliance and security reasons we should use AI Gateway LLM Proxy method, which is not currently available yet but it could be integrated though Langchain's Runnable. See https://python.langchain.com/docs/how_to/custom_llm/

## State
To manage states reducers define the behavior of the schemas. Langchain provide some basic reducers, some inherited from the language (i.e. Python operation.add to append to a list).

Usually Agents change messages flowing a single schema containing the input/output keys or channels. It is possible to work with multiple schemas dought if internal graph nodes need to pass information that is not required in the input/output in the graph (i.e. communication data between nodes that will not be exposed to the user at the end of the graph). So, if needed Agents can define an overall state to communication between nodes additionally to different input and output state respectfully.



## Sync or Async responses
TODO: 

## Studio
Server is run locally, but does not work offline. It should be reviewed before usage for security reasons.

## Tracing with LangSmith
Only online. Should not use for security reasons

## Memory Saver
TODO: Dynamo

## Deploy an Agent

1. Work with langgraph locally to create the API
2. Send to an API to bundle the code
3. Provide additional things like a task queue and a persistence method (i.e. PostgreSQL)
4. The API hosted in the cloud (i.e. Langchain cloud) provides remote execution

All this cloud functionality needs to be built inside the company.