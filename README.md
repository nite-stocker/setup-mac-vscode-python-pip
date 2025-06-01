# Python Development Setup on macOS (VS Code + venv + pip)

## Objective

Set up a modern, isolated Python development environment on **macOS** using:

- [Visual Studio Code](https://code.visualstudio.com/)  
- [Python ≥3.10](https://www.python.org/downloads/)  
- Built-in `venv` module  
- Package management via `pip`  
- The [Microsoft Python Extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

## Prerequisites

- macOS 12+ (tested on Monterey, Ventura, Sonoma)
- Homebrew (for installing Python if needed)

## Install Python 3.10+ with Homebrew

If you don’t already have Python ≥3.10 installed:

```bash
brew install python@3.10
```

Check the installed version:

```bash
python3 --version
```

If Python 3.10 is not your default, you may need to run:

```bash
brew link python@3.10 --force
```

## Create a Project Folder

```bash
mkdir my-python-app
cd my-python-app
```

## Create a Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

> 💡 Use `python -m venv .venv` to avoid relying on a global Python version. This creates a local environment under `.venv`.

## Upgrade pip and Install Dependencies

```bash
pip install --upgrade pip
```

Install any packages your project needs. For example:

```bash
pip install requests
```

Freeze your requirements for reproducibility:

```bash
pip freeze > requirements.txt
```

## Open the Project in Visual Studio Code

```bash
code .
```

If `code` is not recognized:

- Open VS Code
- Press `Cmd+Shift+P`
- Type and run `Shell Command: Install 'code' command in PATH`

## Install the Python Extension for VS Code

Install the [Python Extension by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python) via the Extensions sidebar (`Cmd+Shift+X`), or from the [Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.python).

## Select the Python Interpreter

1. Press `Cmd+Shift+P`
2. Run `Python: Select Interpreter`
3. Choose the interpreter under `.venv/bin/python`

VS Code will automatically use the selected interpreter in the integrated terminal and for running/debugging.

## Configure `.vscode/settings.json` (Optional)

Create `.vscode/settings.json` to automatically set the interpreter:

```json
{
  "python.defaultInterpreterPath": ".venv/bin/python"
}
```

## Create a Starter File

```bash
touch main.py
```

Example contents:

```python
import requests

def main():
    response = requests.get("https://api.github.com")
    print(response.json())

if __name__ == "__main__":
    main()
```

Run it:

```bash
python main.py
```

## (Optional) Enable Formatters and Linters

Install optional tools:

```bash
pip install black ruff
```

Enable in VS Code:

- Open Command Palette → Preferences: Open Settings (JSON)
- Add:

```json
"python.formatting.provider": "black",
"editor.formatOnSave": true,
"python.linting.enabled": true,
"python.linting.ruffEnabled": true,
```

## Additional Resources

- [Python.org: venv Documentation](https://docs.python.org/3/library/venv.html)  
- [Microsoft Docs: Python in VS Code](https://code.visualstudio.com/docs/python/python-tutorial)  
- Real Python – [Setting Up Python for VS Code on macOS](https://realpython.com/python-in-vscode/)  
- Astral – [How to Isolate Python Environments with venv](https://docs.astral.sh/uv/guide/venv/)

## License

MIT

## Code of Conduct

See [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)