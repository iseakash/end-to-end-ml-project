## End to End Machine Learning Project

    Create a new Folder and give it a name.
    Open Anaconda, navigate to the folder and use following command:
    code .

    Open CMD in VS code and start typing following commands:

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

        Create a new folder "src",
            - create a file named "__init__.py" inside it.