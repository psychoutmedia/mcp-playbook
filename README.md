# MCP-Playbook: Async RPC the Easy Way

**Elevator Pitch:**  
MCP-Playbook is your go-to starter kit for quickly building and consuming async RPC tools in Python—no boilerplate fuss, just pure productivity. With both stdio- and SSE-based transports supported out of the box, you’ll be wiring up custom tools and LLM integrations in minutes.

---

## 🚀 Demonstrated Skills

- **Async Programming** with `asyncio`  
- **RPC Server & Client** using `mcp` and `FastMCP`  
- **StdIO & SSE Transports** for flexible integration  
- **Environment Management** via `python-dotenv`  
- **Dependency Management** and virtual environments  
- **Clean Project Layout** and modular code organization  

---

## 📁 Repository Layout

MCP-Playbook/
├── .venv/ ← your virtualenv lives here
├── .gitignore ← ignore .venv/, pycache, *.pyc
└── mcp-stdio/
├── client-stdio.py ← Async client that calls your tools
├── server.py ← FastMCP server exposing calculator tool
├── requirements.txt ← Project dependencies
└── .env.example ← Sample env vars (if needed)

yaml
Copy
Edit

---

## 🔧 Prerequisites

- Python 3.11+ (3.13 tested)  
- `pip` for installing dependencies  
- (Optional) A terminal multiplexer or two shells for running client & server side by side

---

## ⚙️ Installation

1. **Clone the repo**  
   ```bash
   git clone https://github.com/your-org/mcp-playbook.git
   cd mcp-playbook
Create & activate a virtual environment

bash
Copy
Edit
python -m venv .venv
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
# Bash / macOS / Linux
source .venv/bin/activate
Install dependencies

bash
Copy
Edit
pip install --upgrade pip
pip install -r mcp-stdio/requirements.txt
🚦 Usage
1. Run the Server
Open a terminal in mcp-stdio/ and start the server (stdio transport by default):

bash
Copy
Edit
cd mcp-stdio
python server.py
You should see:

sql
Copy
Edit
Running server with stdio transport
2. Run the Client
In a second terminal (same mcp-stdio/ folder, venv activated):

bash
Copy
Edit
python client-stdio.py
Expected output:

sql
Copy
Edit
Available tools:
  - add: Add two numbers together
2 + 3 = 5
🔄 Switching to SSE Transport
In server.py, change:

python
Copy
Edit
transport = "sse"
Restart the server:

bash
Copy
Edit
python server.py
Point your HTTP-capable client (or browser) at http://localhost:8050/events

📦 Extending the Playbook
Add new tools by decorating functions with @mcp.tool() in server.py.

Customize your client by calling session.call_tool("<your_tool>", arguments={…}).

Integrate LLMs by wiring openai or httpx inside your tool implementations.

🤝 Contributing
Fork the repo

Create a feature branch (git checkout -b feature/your-tool)

Commit your changes (git commit -m "Add cool new tool")

Push to your branch (git push origin feature/your-tool)

Open a Pull Request—see our CONTRIBUTING.md for details.

📜 License
This project is released under the MIT License. See LICENSE for full details.
