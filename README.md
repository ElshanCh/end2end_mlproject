# End to End ML Project

## Table of Contents

1. [Environment Creation](#1-environment-creation)
2. [GitHub Setup](#2-github-setup)
3. [Initialize Git Repository & First Commit](#3-initialize-git-repository--first-commit)
4. [Setup And requirements.txt](#4-setup-and-requirementstxt)
5. [Setting up src Folder](#5-setting-up-src-folder)

## Workflow Steps
1. Set up Project With GitHub
2. Data Ingestion
3. Data Transformation
4. Model Trainer 
5. Model Evaluation
6. Model Deployment
7. CI/CD Pipelines - GitHub Actions
8. Deployment - AWS

# Tutorial 1: Github And Code

## 1. Environment Creation

1. Create a new environment:

    ```bash
    conda create -p venv python==3.8 -y
    ```

2. Activate the new environment:

    ```bash
    conda activate venv/
    ```

## 2. GitHub Setup

1. Set up the GitHub Repository

    - Create a new repository on GitHub.
    - Copy the repository URL.

## 3. Initialize Git Repository & First Commit

1. Initialize GitHub Repository locally:

    ```bash
    git init
    ```

2. Create files locally:
    - README.md
    - .gitignore

3. Add README.md to the git repository:

    ```bash
    git add README.md .gitignore
    ```

4. Commit the changes to the repository:

    ```bash
    git commit -m "first commit"
    ```

5. Check the status of the changes:

    ```bash
    git status
    ```

6. Create a new branch:

    ```bash
    git branch -M main
    ```

7. Add remote repository:

    ```bash
    git remote add origin <paste_your_repository_url>
    ```

8. Push into the GitHub Repository:

    ```bash
    git push -u origin main
    ```

Now, your local repository is initialized, and the README.md file is committed and pushed to the main branch on GitHub. This sets up the foundation for your end-to-end machine learning project.

## 4. Setup And requirements.txt
- Create a requirements.txt file
- Create a `setup.py` file in the project root to specify project metadata and dependencies.
    
    `setup.py` is used to build an application as a Package(library)

``` python
from setuptools import find_packages,setup
from typing import List

HYPEN_E_DOT='-e .'
def get_requirements(file_path:str)->List[str]:
    '''
    this function will return the list of requirements
    '''
    requirements=[]
    with open(file_path) as file_obj:
        requirements=file_obj.readlines()
        requirements=[req.replace("\n","") for req in requirements]

        if HYPEN_E_DOT in requirements:
            requirements.remove(HYPEN_E_DOT)
    
    return requirements

setup(
name='mlproject',   # To Change
version='0.0.1',    # To Change
author='Your Name',  # To Change
author_email='your_email_address',  # To Change
packages=find_packages(),
install_requires=get_requirements('requirements.txt')

)
```

## 5. Setting up `src` Folder 

 1. Create a `src` Folder:

   - The `src` (source) folder is commonly used to organize the source code of your project.

   ```bash
   mkdir src
   ```

 2. Add `__init__.py` to `src`:
   - `__init__.py` is for `setup.py` Configuration
   - The `__init__.py` file can be an empty file or include initialization code. It signals Python to treat the directory as a package.

   ```bash
   touch src/__init__.py
   ```

 3. Move Code Files to `src`:

   - Move your Python files (modules) from the project root to the `src` folder.

   ```bash
   mv module1.py src/
   mv module2.py src/
   ```

 4. Update Import Statements:

   - Update import statements in your code to reflect the new package structure.

   ```python
   # Before
   from module1 import function1

   # After
   from src.module1 import function1
   ```

 5. Install the Package in Editable Mode:

   - Install your package in editable mode to reflect changes without reinstalling.

   ```bash
   pip install -e .
   ```

   - Add to the end of the `requirements.txt` `-e .` that is mapping to the `setup.py`. 
   - This will help in case if you want to install directly the `requirements.txt` with the `pip install requirements.txt` it will automatically trigger the `setup.py`
   - `get_requirements()` will resolve the problem of `-e .` at the end of the `requirements.txt`

``` python
HYPEN_E_DOT=get_requirements
def get_requirements(file_path:str)->List[str]:
    '''
    this function will return the list of requirements
    '''
    requirements=[]
    with open(file_path) as file_obj:
        requirements=file_obj.readlines()
        requirements=[req.replace("\n","") for req in requirements]

        if HYPEN_E_DOT in requirements:
            requirements.remove(HYPEN_E_DOT)
    
    return requirements
```


 6. Run requirements.txt:
```bash
pip install -r requirements.txt
```
- `-e .` in the `requirements.txt` will trigger the `setup.py`
- As a result you will get all libraries installed and new folder in your directory `mlproject.egg-info`


 Notes:

- The `src` structure enhances modularity and avoids clutter in the project root.
- `__init__.py` is crucial for Python to recognize the `src` folder as a package.
- `setup.py` configures project metadata and dependencies for distribution.
- Using an editable installation (`pip install -e .`) facilitates development and testing.

This organization improves code structure and prepares your project for distribution or deployment. Adjust the package name, version, and dependencies in `setup.py` according to your project's specifications.

##
##
# Tutorial 2: Project Structure, Logging And Exception Handling

## 1. Create `components` Folder inside the `src` Folder

 1. Create `__init__.py` File inside the `components` Folder
    - The components will be created as a package in the way that they can be imported to some other file location, that is why you add `__init__.py` in it.
 2. Start to add components. 
    - The components are the modules (for example, Data Ingestion, Data Transformation) that we are going to create. For example:
    `data_ingestion.py`,
    `data_transformation.py`,
    `model_trainer.py` 

## 3. Create `pipeline` Folder inside the `src` Folder
 1. Create `__init__.py` File inside the `pipeline` Folder
    - The components will be created as a package in the way that they can be imported to some other file location, that is why you add `__init__.py` in it.
    - In the `pipeline` Folder you will have pipelines which will consume modules from the `components` Folder  
 2. Start to add pipelines. 
    - For example:
    `train_pipeline.py`,
    `predict_pipeline.py`

## 4. Create 3 more Files inside the `src` Folder
1. Create `logger.py` File inside the `src` Folder.
2. Create `exception.py` File inside the `src` Folder.
3. Create `utils.py` File inside the `src` Folder. This file will contain any functionalities written in a common way which will be used in entire application (will be used in components).

