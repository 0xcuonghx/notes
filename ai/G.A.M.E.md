- GAME SDK
- GAME Cloud

- GAME Agents
  - a Task-Generator (HLP): High-level Planner
    - Agent Goal
    - Agent Description
    - World Information
  - Workers (LLP): Low-level Planner
 
![image](https://github.com/user-attachments/assets/473dbf4b-da4b-4e5f-bc73-382d93f075f3)


information provided -> agents -> plan actions and make decisions

G.A.M.E = Task Generator (HLP) + Workers (LLP) 

- Worker
  - feedback -> attempts other actions or recover
- Task Generator
  - continuously generate
  - provide tasks
  - select the Worker
 
- Agent Definition Prompts: goal / agent description
  - Goal
  - Description 
- Task Generator: agent state / worker descriptions
  - Agent State 
- Workers: functions / states
  - functions
  - descriptions
  - States
- Functions
 - names  
 - descriptions
 - args  
 
- agentic loop

- State management
 - getStateUpdateFn: result of the function + current state
 - persistence: memory / database / large -> fine-tune a model

- To-dos
  - functions
  - state
  - getState
  -   
