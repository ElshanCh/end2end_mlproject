# End to End ML Project

## Workflow Steps
1. Set up Project With GitHub
2. Data Ingestion
3. Data Transformation
4. Model Trainer 
5. Model Evaluation
6. Model Deployment
7. CI/CD Pipelines - GitHub Actions
8. Deployment - AWS

# Tutorial 1: End To End ML Project With Deployment-Github And Code

## Environment Creation

1. Create a new environment:

    ```bash
    conda create -p venv python==3.8 -y
    ```

2. Activate the new environment:

    ```bash
    conda activate venv/
    ```

## GitHub Setup

1. Set up the GitHub Repository

    - Create a new repository on GitHub.
    - Copy the repository URL.

## Initialize Git Repository & First Commit

1. Initialize GitHub Repository locally:

    ```bash
    git init
    ```

2. Create one README.md file locally

3. Add README.md to the git repository:

    ```bash
    git add README.md
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