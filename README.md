# Create new python project
## Create the project structure

* Open the terminal and change the current working directory to your local project.
* Create the project folder using poetry:
```
poetry new python-project-template
```
![img.png](images/new_python_project_using_poetry.png)

## Create the poetry interpreter
* Step 1: Add new local interpreter
![img.png](images/add_poetry_interpreter_step_1.png)
* Step 2: Create a new poetry interpreter
![img.png](images/add_poetry_interpreter_step_2.png)
  * Step 3: Rename the newly created poetry interpreter
  ![img.png](images/add_poetry_interpreter_step_3.png)
  
        venv location: /Users/badr/Library/Caches/pypoetry/virtualenvs/github-projects-SNtUKpNA-py3.11/bin
  
## Install the requirements using poetry:
* poetry add sklearn
* poetry add pandas
* ...

## Automatic format of the python code

* Install ```black``` package:

```bash
poetry add black
```
* How to use?

  Either to open a terminal and write:
```bash
black python_script_name.py
```
or if we want to format more than one python file, write :
```bash
black folder_name/
```
or using pre-commit automatic formatting:
* First, we need to install not only black but also pre-commit package:
```bash
poetry add pre-commit
```
* Create a new file and name it: ```.pre-commit-config.yaml```
* Write in the file the following code, make sure you are choosing your 
current python version ```python --version```:
```
repos:
-   repo: https://github.com/psf/black
    rev: stable
    hooks:
    - id: black
      language_version: python3.11.0
```
* Install pre-commit, meaning, create a new hook for the yaml file. 
Using the terminal, change the current working directory to your local project 
(where the yaml file is created and then execute:
```
pre-commit install
```
## Add the local python project to your GitHub
* Open the terminal, change the current working directory to your local project.
* Initialize the local directory as a Git repository.
```
git init
```
* Stage and commit all the files in your project:
```
git add . && git commit -m "initial commit"
```
* To create a repository for your project on GitHub, use the ```gh repo create ``` subcommand.

If it is the first time you are adding a project to your GitHub you need to set up few things:
- First, install ```gh```:
```
poetry add gh
```
```
brew install gh
```
- Now, when you type ```gh repo create ``` on the terminal, it will ask you to login:
![img.png](images/git_login.png)
-Go to the GitHub website and generate new classic token:
![img.png](images/GitHub_classic_token.png)
- Configure SourceTree:
![img.png](images/sourcetree_configure_with_github.png)
- Configure Pycharm:
![img.png](images/pycharm_configure_with_github.png)
- GitHub's authentication: 
- Solution 1: 
- Create a file ```script.sh``` containing the following:
```
#!/bin/env bash
set -u
echo "$GITHUB_TOKEN" > .githubtoken
unset GITHUB_TOKEN
gh auth login --with-token < .githubtoken
rm .githubtoken
gh release create $VERSION --notes "Release $VERSION. $COMMIT_MESSAGE"
```
- Create a configuration file with adding some environmental variables:
![img.png](images/github_authen_cli_script_sh.png)
- Execute the shell script to validate the authentication.
After executing that script you will be able to create a repo using 
```bash
gh repo create
```
![img.png](images/add_remote_repo_using_cli.png)
To set the password and commit/push changes:
![img.png](images/github_add_changes_with_authentification.png)







