
git init	Initializes a new Git repository in the current directory.

git remote add origin <url>	Links your local repository to a remote repository on GitHub.

git remote -v	Verifies that the remote repository has been added correctly.

git config --global user.name "Your Name"	Sets your global username for all commits.

git config --global user.email "your.email@example.com"	Sets your global email address for all commits.

 Cloning and Updating a Project
 
git clone <url>	Downloads the entire project and its history from a remote URL.

git pull origin main	Fetches the latest changes from the main branch on GitHub and merges them into your local branch.

git add .	Stages all modified and new files for the next commit.

git commit -m "Your commit message"	Saves the staged changes to your local history with a descriptive message.

git push -u origin main	Pushes your local commits to the main branch on GitHub for the first time.

git branch	Lists all local branches in your repository.

git checkout -b <new-branch>	Creates a new branch and switches to it.

git checkout <existing-branch>	Switches to a different existing branch.

git merge <branch-to-merge>	Merges changes from the specified branch into your current branch.

git status	Shows the current state of your repository, including staged and unstaged changes.

git log	Displays a list of all past commits in a readable format.

git show	Shows the full details (author, date, changes) of the last commit. Use git show <commit-hash> for a specific commit.

git revert <commit-hash>	Creates a new commit that undoes the changes from a specified commit. This keeps the history clean.

git branch -d <branch-name>	Deletes a local branch.

git push origin --delete <branch-name>	Deletes a branch from the remote repository on GitHub.

git restore --staged temp.txt

ssh-keygen -t ed25519 -C "your_email@example.com"

Click on your profile picture in the top-right corner of the page.

In the dropdown menu, select Settings.

In the left sidebar of the settings page, click on SSH and GPG keys.

git log -1 -- <filename>

FROM tomcat:9.0-jdk11-openjdk

COPY target/your-app-name.war /usr/local/tomcat/webapps/

docker build -t your-image-name:1.0 .

docker tag your-image-name:1.0 your-dockerhub-username/your-image-name:1.0

docker push your-dockerhub-username/your-image-name:1.0

a. Run nginx on port 8080:
* docker run -d -p 8080:80 nginx

b.  List all running containers:
* docker ps

c.  Stop carcontainer:
* docker stop carcontainer

d.  Check container logs:
* docker logs <container_id_or_name>

e.  Check CPU/RAM, limit RAM, and open a shell:
* Check stats: docker stats
* Limit RAM: docker run --memory="512m" ...
* Open shell: docker exec -it app /bin/bash

f.  Open a shell in ubuntu container:
* docker exec -it ubuntu /bin/bash

g.  Run 3 instances with docker-compose:
* docker-compose up --scale app=3

h.  Check for port 3000 usage:
* docker ps -f "publish=3000"

i.  Start and work in a container immediately:
* docker run -it --rm ubuntu /bin/bash

j.  Delete a built image:
* docker rmi <image_id_or_name>

docker-compose.yml

for post gre sql

    version: '3.8'

    services:
  
    app:
  
    image: your-dockerhub-username/your-app-name:1.0
  
    container_name: maven-app-container
    
    ports:
    
      - "8080:8080"
    
    depends_on:
    
      - postgres_db
    
    environment:
    
      # These environment variables link your app to the database
      
      DB_HOST: postgres_db
      
      DB_USER: myuser
      
      DB_PASSWORD: mypassword
      
      DB_NAME: mydatabase
   
    networks:
    
      - app-network

 
     postgres_db:

    image: postgres:13
    container_name: postgres-container
    environment:
      POSTGRES_DB: mydatabase
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
    volumes:
      - pgdata:/var/lib/postgresql/data
    networks:
      - app-network

    networks:
    app-network:
    driver: bridge

    volumes:
     pgdata:


mongo db

	version: '3.8'

	services:
 	 # Container 1: Your Maven Application
  	app:
    image: your-dockerhub-username/your-app-name:1.0
    container_name: maven-app-container
    ports:
      - "8080:8080"
    depends_on:
      - mongo_db
    environment:
      # These environment variables link your app to the database
      MONGO_URI: mongodb://mongo_db:27017/mydatabase
    networks:
      - app-network

  
  	mongo_db:
    image: mongo:latest
    container_name: mongo-container
    ports:
      - "27017:27017"
    volumes:
      - mongodata:/data/db
    networks:
      - app-network

	networks:
 	 app-network:
    driver: bridge

	volumes:
 	 mongodata:

  sql

 	 version: '3.8'

	services:
  
 	 app:
    image: your-dockerhub-username/your-app-name:1.0
    container_name: maven-app-container
    ports:
      - "8080:8080"
    depends_on:
      - mssql_db
    environment:
      # These environment variables link your app to the database
      DB_HOST: mssql_db
      DB_USER: SA
      DB_PASSWORD: "YourPassword123!"
      DB_NAME: mydatabase
    networks:
      - app-network

  	mssql_db:
    image: mcr.microsoft.com/mssql/server:2019-latest
    container_name: mssql-container
    environment:
      ACCEPT_EULA: "Y"
      SA_PASSWORD: "YourPassword123!"
    ports:
      - "1433:1433"
    volumes:
      - mssql-data:/var/opt/mssql
    networks:
      - app-network

	networks:
 	 app-network:
    driver: bridge

 docker build -t your-image-name:1.0 .

 docker tag your-image-name:1.0 your-dockerhub-username/your-image-name:1.0

 docker push your-dockerhub-username/your-image-name:1.0

 docker compose up -d


	volumes:
 	 mssql-data:



