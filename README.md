## End to End Machine Learning Project

### Task:

1. Setup github repository
    - new environment
    - setup.py
    - requirements.txt
2. Src folder and build the package
    __________________________________________________________________________________________

Step 1:

    On Anaconda, navigate to the folder (Create a new folder) and use following command:
        >> code .

    On VS code, open CMD and start typing following commands:

        >> conda create -p venv python==3.8 -y
        >> conda activate venv/

        Create a new "README.md" file

        >> git init
        >> git add README.md
        >> git commit -m "First Commit"
        >> git branch -M main
        >> git remote add origin https://github.com/iseakash/end-to-end-ml-project.git
        >> git remote -v

            For those starting out first time:
            Google : "git global config"
            >> git config --global user.name "John Doe"
            >> git config --global user.email johndoe@example.com
            >> git config --global user.email (should give your new email id)

        >> git push -u origin main

    On Github, select "Add file" -- "Create new file"
               name it ".gitignore" -- select "Python" language -- Commit.

        >> git pull

    On VS code,

        Create two files :
            1. "requirements.txt" (lists dependencies to install for Python project using pip).
            2. "setup.py" (create machine learning application as a package and distribute).

        How to fill "setup.py" file?
            - start with imports
            - do the setup by filling author, project name, email, etc.
                (find_package() to locate external libraries)
            - through src folder, setup is able to identify and build package.
            - create a function to read all libraries from "requirements.txt" 
                rather than mentioning them here in a list.
            - this function reads "\n" as well from the "requirements.txt" file,
                which should be avoided.

        Create a new folder "src",
            - create a file named "__init__.py" inside it.
                (All these folders with "__init__.py" file will help in identifying package)

        How to fill "requirements.txt" file?
            - '-e .' helps to enable running the setup.py file.

        >> pip install - requirements.txt (to build the complete package,
                                           '-e .' will disappear from "requires.txt" file of package info)
        
Step 2:

    On VS code, in src folder:
    
        Create a new folder named "components" with "__init__.py" file.
            - The benefit of having component folder is containing all the modules at one place,
                eg., data ingestion, data processing, model training, etc.

        Create a new folder named "pipeline" with "__init__.py" file.
            - Create sub folders namely, "predict_pipeline.py" and "train_pipeline.py".

        Create three additional files,
            - logger.py (to record and monitor events, errors, and other information during runtime)
            - exception.py (to handle specific error conditions and improve code robustness)
            - utils.py (a file containing various helper functions or tools for a specific project)
        
        How to fill "exception.py" file?
            - Purpose: Creating custom exception with detailed error message using sys module.
            - import a library sys
            - exc_info() (Gives exception type, value, and traceback where traceback contains all details
                 related to error like filename, error line, etc.)
            - Google "custom exception handling in python read documentation".
            - "CustomException" class (define a custom exception that includes a detailed error message).
            - super().__init__(error_message) (sets the exception message to the provided error message).

        How to fill "logger.py" file?
            - Purpose: To record events and messages in a python project for monitoring and debugging.
            - import libraries like logging, datetime, os.
            - logging.basicConfig() (configures the basic logging system).
            - severity levels can be INFO, WARNING, ERROR, and CRITICAL where INFO is the minimum.
                (DEBUG is even lower than INFO)

