## End to End Machine Learning Project

### Task:

1. Setup github repository
    - new environment
    - setup.py
    - requirements.txt
2. Src folder and build the package
3. Component folder and code the data ingestion, data tranformation and model training.
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

        How to fill "utils.py" file?
            - Aim: To store all the common functions that are used in the project.
            - At first, Use "dill" library to create pickle file.
            - Second, create save_object() function to save the pickle file at desired location.
            - Third, create evaluate_models() function to generate model performance report.
            - Fourth, in evaluate_models() function also add GridSearchCV() for hyperparameter tuning.
            - Fifth, create load_object() function to load the existing pickle file.

Step 3:

    On VS code, in src\components folder:

        How to fill "data_ingestion.py" file?
            - Aim: Read & Split the data from different data source (created by big data or cloud team).
            - At first, import all libraries (os, sys, logs, exception, pandas, sklearn, dataclasses).
            - Second, create a class for storing input data related details (eg., location of data files).
            - Third, using dataclass a decorator to avoid using __init__ to declare class variables and
                when you just need to declare varibles in a class and no functions.
            - Fourth, for beginner - it's better to create this DataIngestionConfig class rather than
                creating a new 'config' folder.
            - Fifth, create the DataIngestion class which includes:
                > initiating path varibales and making new directories,
                > reading raw data file and saving train-test data files,
                > logging the details and raising the exceptions.
            - Add .artifacts in the .gitignore file in the Environments to avoid data save. (can avoid)

        How to fill "data_transformation.py" file?
            - Aim: Perform feature engineering, data cleaning, handle categorical data, etc.
            - Use ColumnTransformer to create the data transformation pipeline.
            - At first, import libraries like Pipeline, SimpleImputer, OneHotEncoder, StandardScaler, etc.
            - Second, create a class DataTransformationConfig for all transformation related varibales.
            - Third, create preprocessor object path to store the model in pickle file at some location.
            - Fourth, create get_data_transformer_object() function to create all the pickle files responsible
                for categorical encoding, scaling , etc.
            - Fifth, create pipeline for numerical (impute, scale) and categorical (encode, impute, scale) features.
            - Sixth, create ColumnTransformer object - a combination of num and cat pipeline.
            - Seventh, call the save_object() function to save datatransformer pickle file.
            - np.c_ is a function used to concatenate arrays along the second axis (100, 4) & (100,) ~ (100, 5).

        How to fill "model_trainer.py" file?
            - Aim: Train multiple models and check their performances.
            - Models: Linear Regression, KNN, Decision tree, XG Boost, Catboost and ensemble models like adaboost.
            - At first, import all libraries (os, sys, logs, exception, utils, sklearn, dataclasses).
            - Second, create two classes: 1. "ModelTrainerConfig" (for model path) & 2. "ModelTrainer".
            - Third, In "ModelTrainer" class, initiate a function initite_model_trainer() which declares
                X-y split, all models, evaluation report and finds best model, save model and return R2.
            - Fourth, in the function initite_model_trainer() add parmas as dictionary to consider all
                possible values of required parameters w.r.t. each model.

Step 4:

    On VS code,

        Create one more file:
            3. "app.py" (lists dependencies to install for Python project using pip).

        Create one folder as well:
            1. templates 
                        (Inside, create files "index.html" (default page),
                        "home.html" (input data fields for model prediction))

        How to fill "app.py" file?
            - At first, start with imports like flask, pandas, numpy, sklearn.
            - Second, initialize the Flask application and assign it to the app.
            - Third, define the home route with index() function for displaying homepage.
            - Fourth, define predict_datapoint() function for taking user input and
                displaying prediction using GET and POST method.
            - Fifth, call CustomData() fn with extracted values from POST query.
            - Sixth, call get_data_as_data_frame() fn to convert all values into a dataframe.

Step 5:

    On VS code, in src\pipeline folder:

        How to fill "predict_pipeline.py" file?
        - Aim: To make the web application interact with model.pkl, preprocessor.pkl and new input file.
        - At first, import os, sys, exception, utils to load object.
        - Second, create two classes: "PredictPipeline" and "CustomData".
        - Third, define CustomData class:
                > Purpose is to map user input from html page to backend. 
                > Initiate all variables that are passed in as an input to __init__() function.
                > Through this, it will be able to map the values with "home.html".
                > get_data_as_data_frame() function maps user input values to the names and create dataframe.

        - Fourth, define PredictPipeline class:
                > Declare the model and preprocessor paths, load the pickle objects.
                > Transform the features using preprocessor and predict using model.
