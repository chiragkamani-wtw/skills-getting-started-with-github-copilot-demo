---
agent: 'agent'
description: 'Start the development server'
---

Run the development server using the module entry point:

```powershell
.venv\Scripts\python.exe -m uvicorn src.app:app --reload
```

The app will be available at http://localhost:8000
