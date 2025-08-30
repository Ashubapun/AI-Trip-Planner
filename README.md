Step by step process:
1. Setup env variables or keys
2. Write the setup.py file
3. Go to config>config.yaml and configure llm
4. In utils>confi_loader.py write load_config function
5. Update or write the load_llm function with config in model_loader.py (utils>model_loader.py)
6. Start writing and updating the agentic_workflow.py file in agent folder (create and update the stategraph with tools)
7. Add SYSTEM_PROMPT in prompt.py file (prompt_library>prompt.py)
8. Write endpoints of FastAPI in main.py
9. 