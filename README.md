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
4. (Optional) Add the `code` command to your Terminal shell allow:
   - Launch VS Code
   - Press `⌘+Shift+P`
   - Run `Shell Command: Install 'code' command in PATH`

Adding the VS Code `code` command to your terminal allows you to open files or directories in VS Code directly from the command line. For example, you can use commands like `code .` to open the current directory in VS Code or `code filename` to open a specific file.

## Install the Python extension for VS Code

Install the Python extension by Microsoft to enable Python syntax highlighting, code completion, formatting, linting, and debugger integrations.

1. Open VS Code  
2. Go to the Extensions sidebar (`⌘+Shift+X`)  
3. Search for "python"  
4. Click Install on the extension by Microsoft  

The Python extension installs the Pylance and Python Debugger extensions. See these individual extensions for feature and use details.

## Set up your project

### Create a new project folder and open it in VS Code

1. Open VS Code  
2. In the `File` menu, select `Open Folder…`
3. Browse to and select a folder to hold your Python projects
4. Click `New Folder`, enter a project name such as python-setup, and click `Add`

VS Code prompt:

> Do you trust the authors of the files in this folder?
> 
> You are adding files that are not currently trusted to a trusted workspace. Do you trust the authors of these new files?
>
> Yes No

5. Since the new folder is empty and you will be creating its contents, select `Yes`.

You should now be working inside your new project folder in an empty VS Code window.

### Use the VS Code terminal

1. In the Terminal menu, choose New Terminal

The VS Code integrated terminal will open in the lower panel. All following terminal instructions can be run here.

### Create and activate a virtual environment

#### Create a virtual environment with the `venv` module

```zsh
python3 -m venv .venv
```

The Explorer in the navigation pane should show your project folder with the newly-created .venv virtual environment folder.

#### Activate the virtual environment with the `source` command

```zsh
source .venv/bin/activate
```

This tells your terminal to run the `activate` script inside the .venv folder. It configures the terminal to use the virtual environment’s Python interpreter and pip package manager. Any packages you install or scripts you run will stay isolated to this project. You’ll see (.venv) appear in your terminal prompt to indicate that it’s active.

You should see something like:

```zsh
(.venv) your-name@your-computer project-name %
```

### Select the virtual environment Python interpreter

1. Press `⌘+Shift+P` to open the command palette  
2. Type "python", then select `Python: Select Interpreter`  
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

### Upgrade pip in the virtual environment

`pip` is the Python package manager. It’s included with Python installers from python.org but isn’t part of Python’s standard library.

When you activate a virtual environment, it updates your terminal’s path so that the environment-specific `python` and `pip` are used instead of the system-wide ones.

The [Python Packaging User Guide][python-packaging-user-guide] recommends upgrading pip inside an activated environment to keep it isolated and up to date for your project.

Make sure that `pip` is up-to-date by running:

```zsh
pip install --upgrade pip
```

…and confirming the version and virtual environment location with:

```zsh
pip --version
```

You should see something like:

```zsh
pip 25.1.1 from .venv/lib/python3.12/site-packages/pip (python 3.12)
```

### Install a package

We'll use the third-party requests package to make a request to a website, and retrieve your IP address from the response.

Install the requests package:

```zsh
pip install requests
```

### Run the script

Run the script with the `python` command:

```zsh
python main.py
```

…or click the Run Python File "Play" button at the top of the editor when `main.py` is active.

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
[python-packaging-user-guide]: <https://packaging.python.org/en/latest/>
[contributing-to-a-project]: <https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project>
[getting-started-with-Python-in-VS-Code]: <https://code.visualstudio.com/docs/python/python-tutorial>
[beginners-guide-to-python]: <https://wiki.python.org/moin/BeginnersGuide>
[virtual-environments-and-packages]: <https://docs.python.org/3/tutorial/venv.html>
[venv-creation-of-virtual-environments]: <https://docs.python.org/3/library/venv.html>
[installing-python-modules]: <https://docs.python.org/3/installing/index.html>
[choose-an-open-source-license]: <https://choosealicense.com/licenses/mit/>