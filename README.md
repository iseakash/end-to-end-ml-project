## End to End Machine Learning Project

    Create a new Folder and give it a name.
    
    On Anaconda, navigate to the folder and use following command:
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
        
