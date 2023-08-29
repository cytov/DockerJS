# DockerJS
A homelab project to learn dockerizing a Node js project.

In this little homelab project, I will be learning how to fully dockerize a Node JS app.

Steps taken:
  1-Create a dummy Node app for testing (express)
  2-Write a dockerfile for the app, our base will be the "node" image.
  3-Make sure the correct ports/


The commands executed through this project:
  npm init -y (creates package.json & package-lock.json)
  npm install express (creates node_modules & package-lock.json)
  **Create the index.js file
  node index.js (launch app)
  **Create Dockerfile
  docker build -t node-app-image .
  **Create .dockerignore
      node_modules
      Dockerfile
      .dockerignore.
      .git
      .gitignore
  **Setup nodemon
    npm install nodemon --save-dev
  **Setup scripts (start and dev) in package.json
  **delete node_modules
  docker run -d -v $(pwd):/app -v /app/node_modules --name node-app -p 3000:3000 node-app-image

Key learning points:
  -In a Dockerfile, cached results are important, this is why for example we put "COPY package.json" before "COPY . ./" which seems redundant, but it optimizes the process.
  -Diff between RUN and CMD in the dockerfile: RUN is executed when we are building the image, CMD is assigned to the container and executes at runtime.
  -We setup dockerfile as: CMD ["npm", "run", "dev"] because we want to run nodemon in dev mode (package.json's script)
  -Nodemon solves the issue of having to restart Express everytime there is an update.
  -Docker logs node-app (to check logs for a container)
  
