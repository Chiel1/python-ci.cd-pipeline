# python-ci.cd-pipeline

DOCUMENTATION FOR GITHUB PROJECT

•	Go to your GitHub account
•	Click on “Repositories”, then “New Repository”
•	Create a name for it
•	Under “Initialize this repository”, click the “Add README file” (optional)
•	Click the “Add .gitignore” section and pick that for Python (since this is a python project)
    .gitignore file tells Git the files it should ignore when committing your project to GitHub
•	Click “Create Repository”



On Virtual Studio Code (VSCode)

Having created the repository on GitHub, create a new folder for this project on your local machine, open the folder on VSCode.

Go back to the created repository on GitHub, click on “Code” and then copy the link to the repo from the drop down menu.

•	Open a new terminal on GitHub and clone the repo with the command - git clone “link”
•	On the terminal, move into that repo you just clone (cd “repository”)
•	Create two more folders (“src” and “test”) in it
    src folder - will consist of the source code that'll be used for the project
    test folder - consists of the test cases for the code (e.g pytest)
•	Create a .txt file named “requirement.txt”, it'll contain the Python library we will be using, and its current version.



File Creation
•	In the src folder, create a file that'll contain your code (e.g main.py) and in it write your python code.

•	In the test folder, create a file for the test cases (e.g test_main.py) and write the test cases for the Python code on the main.py file.
    Use the “from” function to reference the main.py file.
    For example:
    from src.main import add



To install the Python library in the requirements.txt file

Run:
pip install -r requirements.txt



To Run the Test Case File 

Running the test_main.py file, tests if the code in main.py will work.

Run “pytest”, alongside the name of the test case folder 
pytest test/

NOTE:
You might get an error because the test_main.py can't look into the main.py file because of the directory structure.
To resolve it, you can do one of this:
●	Add “init.py” file to the src folder, or
●	Create a “contest.py” file directly in the directory of the repo being worked on.

Run “pytest test/” again. 


Next, to push to GitHub
Run the following command
•	git add .     ----- adds all the modified file
•	git status   ----- to verify all the changes that have been added or are yet to be added
•	git commit -m “message”    ----- to commit changes to staging area ready to be pushed
•	git push ----- to send project to GitHub


NOTE:
Create an alias for your link, so that you don't have to always add the link to git push everytime you want to push to GitHub

Run:
git remote add origin “link”



CONTINUOUS INTEGRATION (CI)

Continuous integration is a practice that requires consistently commiting code to a repository on GitHub. This is the automated testing phase. When you commit code to GitHub you can continuously build and test the code for errors.

To integrate GitHub Actions

•	Click on Actions on GitHub (it gives template recommendations based on the programming language used in your repo)
•	Pick an Action template that you need (for this case pick Python Application) and click Configure
•	Copy the code given. This code will only work when kept in a sub folder (“workflows folder”) of “.github folder”

Go back to VSCode
•	In the repo directory, create a “.github folder”
•	In the “.github folder” create a folder named “workflows”
•	Lastly in the workflows folder, create a .py file (python-app.py) and save.

NOTE: You can leave everything as default or change the branches for the “push and pull request”.

Run the following command
•	git add .
•	git status 
•	git commit -m “message”
•	git push



CONTINUOUS DEPLOYMENT
This gets all the committed codes that contains fixes and changes that has successfully passed the automated testing phase into production environment.

After the build operation is completed in CI phase, the code needs to be deployed for production.

•	To that code on the project-app.yml file, add a deploy job to it with the necessary steps.

Run the following command
•	git add .
•	git status 
•	git commit -m “message”
•	git push



To Push This Code to Docker Hub

•	Create a new job (push to registry) on the .yml file.
The new job would indicate, the necessary steps such as checking out the code, logging to Docker Hub with your username and password, build and push using extracted metadata the image. 

•	In order for the code to run successfully and login to Docker Hub to create the image, your Docker Credentials ought to be saved in GitHub Secrets.

In GitHub
•	Go to Settings
•	Click on Secrets and Variables
•	Click on Actions
•	Click on New Repository Secret
•	Save the username and password separately and accordingly in the these heading DOCKER_USERNAME and DOCKER_PASSWORD
This way when you call these variables on the .yml file, it picks the values from GitHub Secrets.


Also to the repository directory, create: 
•	index.json file: used for handling HTTP requests and responses.
•	dockerfile: a text based documents that serves as a blueprint for building docker image. It gives the command to run, port etc
•	package.json: contains the dependencies to be installed
•	.dockerignore: describes files and directories that you want to exclude when building a Docker image. 

Having updated the .yml file, run the following command
•	git add .
•	git status 
•	git commit -m “message”
•	git push

Login into Docker Hub, go to Repositories and open your successfully run project there.
