Step by step process:
	1.	Set environment variables (API keys & secrets)
	•	Put them in a .env file and keep it in .gitignore.
	•	Load them in code (e.g., with python-dotenv) or from the OS.
	
    2.	Create setup.py (project packaging info)
	•	Add name, version, dependencies, and entry points.
	•	(Optional modern alternative: pyproject.toml.)
	
    3.	Configure the LLM in config/config.yaml
	•	Define provider, model_name, temperature, max_tokens, timeouts.
	•	Keep anything that might change here (so code stays clean).
	
    4.	Write load_config() in utils/config_loader.py
	•	Read the YAML file, validate required fields, and return a config dict/object.
	•	Handle missing or bad values with clear errors.
	
    5.	Write/update load_llm(config) in utils/model_loader.py
	•	Use config + env vars to create the LLM client.
	•	Handle auth, retries, and timeouts; return a ready-to-use LLM instance.
	
    6.	Build the agent workflow in agent/agentic_workflow.py
	•	Create the state graph: nodes (steps/tools) and edges (when to move next).
	•	Plug in tools, memory (if any), and logging/error handling.
	
    7.	Add SYSTEM_PROMPT in prompt_library/prompt.py
	•	Write a clear system message: role, rules, style, and placeholders for variables.
	
    8.	Create FastAPI endpoints in main.py
	•	Add /chat or /run to accept input, call the agent, and return output.
	•	Define request/response schemas; enable CORS for the frontend.
	
    9.	Build the Streamlit frontend in streamlit_app.py
	•	Simple UI: input box, “Send” button, chat/history display.
	•	Call the FastAPI endpoint and show responses/errors nicely.
	
    10.	Create tools for the agent
    •	In utils/: write functions that call external APIs (auth, request, parse).
	•	In tools/: wrap those functions as tool objects (name, description, input schema) and expose them to the agent.