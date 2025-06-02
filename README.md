# Python development setup on macOS (VS Code + venv + pip)

## Objectives

- Set up a minimal, beginner-friendly Python development environment on macOS using:
    - VS Code editor
    - Python extension for VS Code  
    - The latest Python from python.org  
    - Built-in venv for environment isolation  
    - pip for package management

## Prerequisites

- macOS 12 or later  
- Admin access to install software  
- Internet connection

## Install Python

1. Visit the official [Python download page][mac-python-download].  
2. Download the latest Python 3 installer for macOS 64-bit.
3. Open the `.pkg` file and run the installer. Accept the default options.
4. Open the Terminal app and verify the Python install:

```zsh
python3 --version
```

You should see something like:

```zsh
Python 3.x.x
```

(Version numbers may vary depending on the current release.)

## Install VS Code

1. Visit the official [VS Code download page][vs-code-download].
2. Click Download for macOS.
3. Open the `.zip` file, and drag the Visual Studio Code app to your Applications folder.
4. (Optional) Add the `code` command to your Terminal shell:
   - Launch VS Code
   - Press `Cmd+Shift+P`
   - Run `Shell Command: Install 'code' command in PATH`

## Install the Python extension for VS Code

Install the Python extension by Microsoft to enable Python syntax highlighting, code completion, and debugger integration.

1. Open VS Code  
2. Go to the Extensions sidebar (`Cmd+Shift+X`)  
3. Search for "python"  
4. Click Install on the extension by Microsoft  

This extension also installs Pylance, Pylint, and the Python Debugger. See these individual extensions for more details.

## Set up your project

### Create a new project folder and open it in VS Code

1. Open VS Code  
2. Press `Cmd+Shift+P` to open the command palette  
3. Type `New Window` and select File: New Window
4. In the new window, go to the File menu and choose Open Folder
5. Navigate to where you'd like to create your project, then:
   - Click New Folder, name it `test-python-project`
   - Click Open to open the new folder in VS Code

You should now be working inside your new project folder in an empty VS Code window.

### Use the VS Code terminal

1. In the Terminal menu, choose New Terminal
2. The integrated terminal will open in the lower panel

All following terminal instructions should be run here.

### Create and activate a virtual environment

Create the virtual environment:

```zsh
python3 -m venv .venv
```

Activate it:

```zsh
source .venv/bin/activate
```

You should see `(.venv)` in the terminal prompt, indicating that the virtual environment is active.

### Select the virtual environment Python interpreter

1. Press `Cmd+Shift+P` to open the command palette  
2. Type "python", then run `Python: Select Interpreter`  
3. Choose the interpreter from `.venv/bin/python`

### Create a Python script

1. In the File menu, choose New Text File
2. Save it as `main.py` in the root of your project folder
3. Add the following code and save:

```python
import requests

def main():
    URL = "https://httpbin.org/get"
    response = requests.get(URL)
    data = response.json()
    my_ip = data.get("origin")
    print(f"Your IP: {my_ip}")

if __name__ == "__main__":
    main()
```

### Upgrade pip

In the VS Code terminal:

```zsh
pip install --upgrade pip
```

### Install required packages

```zsh
pip install requests
```

### Run the script

You can run the script using the VS Code terminal:

```zsh
python main.py
```

Or click the Play (Run Python File) button at the top of the editor when `main.py` is active.

The script makes a request to httpbin.org and prints your IP address from the response.

```zsh
Your IP: <your IP>
```

Thank you for following along!

## Roadmap

- [ ] Create sibling repo to compare the development experience of Microsoft's VS Code Python extensions with Astral's uv, ty, and ruff:
  - Python versions  
  - Installing packages and modules  
  - Virtual environments  
  - Static type checking  
  - Linting  
  - Formatting  
  - Packaging

## Contributions
  
Contributions are welcome — fork the repo, create a branch, and open a pull request.

Learn more at GitHub’s [Contributing to a project][contributing-to-a-project].

## Resources

Microsoft Docs  
- [Getting Started with Python in VS Code][getting-started-with-Python-in-VS-Code]

Python.org 
- [Beginner's Guide to Python][beginners-guide-to-python]
- [Virtual Environments and Packages][virtual-environments-and-packages]
- [venv — Creation of virtual environments][venv-creation-of-virtual-environments]
- [Installing Python Modules][installing-python-modules]

## License

MIT License: [LICENSE](LICENSE.md)  
More details: [Choose an open source license][choose-an-open-source-license]

<!-- Reference links -->
[mac-python-download]: <https://www.python.org/downloads/mac-osx/>
[vs-code-download]: <https://code.visualstudio.com/>
[contributing-to-a-project]: <https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project>
[getting-started-with-Python-in-VS-Code]: <https://code.visualstudio.com/docs/python/python-tutorial>
[beginners-guide-to-python]: <https://wiki.python.org/moin/BeginnersGuide>
[virtual-environments-and-packages]: <https://docs.python.org/3/tutorial/venv.html>
[venv-creation-of-virtual-environments]: <https://docs.python.org/3/library/venv.html>
[installing-python-modules]: <https://docs.python.org/3/installing/index.html>
[choose-an-open-source-license]: <https://choosealicense.com/licenses/mit/>