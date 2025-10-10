Documentating Installation Steps
EWE YONG SHEN B122320023

Week 1 Exercise – Environment Setup, Git Workflows & Hello MongoDB

Step 1: Install Development Tools

Visual Studio Code (VS Code)
- I downloaded VS Code from [https://code.visualstudio.com].  
- Installed it with the default settings.  
- I also added the **MongoDB for VS Code** extension.  
- To check that it works, I opened VS Code and ran the terminal.  

Node.js and npm
- I downloaded the **LTS version** of Node.js from [https://nodejs.org].  
- Installed it using the default setup.  
- To make sure it’s installed, I checked the version in the terminal: Both Node.js and npm are working.

MongoDB Community Server
- I downloaded MongoDB Community Server from [https://www.mongodb.com/docs/manual/administration/install-community/].  
- Installed it and chose the option **“Run MongoDB as a Service.”**  
- Then I started MongoDB: MongoDB runs locally at `mongodb://localhost:27017`.
- MongoDB is installed and running.

Git
- I downloaded Git from [https://git-scm.com].  
- Installed it with default options.  
- Then I set my name and email: EWE YONG SHEN , b122320023@student.utem.edu.my
- Git is working correctly.

(Optional) MongoDB Compass
- I installed MongoDB Compass from [https://www.mongodb.com/products/compass].  
- Used it to view my database and confirm that data was inserted into `testDB > users`.
- Compass connected successfully to my local MongoDB.

Step 2: Git Basics & Repository Setup
1. I have created a GitHub Account with this link [https://education.github.com/pack].
- I also create a new Git Repository name with berr2243-25
2. I created a README.md file to document my installation steps.
3. I commit and push to GitHub with this codes:
git add .
git commit -m "Initial commit: Setup documentation"
git branch -M main
git remote add origin https://github.com/EWEYONGSHEN/berr2243-25.git
git push -u origin main

Step 3: Hello MongoDB

Create a New Project Folder
- I created a new folder named `week1-mongodb`.
- Opened the folder in **Visual Studio Code**.

Initialize Node.js Project
In the VS Code terminal, I ran: npm init -y
- This created a `package.json` file.

Then I installed the MongoDB package: npm install mongodb
- This downloaded the MongoDB driver needed to connect to the database.

Create index.js File
I created a file named **index.js** inside the project folder.  
This is my code:

const { MongoClient } = require('mongodb');

async function main() {
    const uri = "mongodb://localhost:27017";
    const client = new MongoClient(uri);

    try {
        await client.connect();
        console.log("Connected to MongoDB!");

        const db = client.db("testDB");
        const collection = db.collection("users");

        await collection.insertOne({ name: "Alice", age: 25 });
        console.log("Document inserted!");

        const result = await collection.findOne({ name: "Alice" });
        console.log("Query result:", result);
    } catch (err) {
        console.error("Error:", err);
    } finally {
        await client.close();
    }
}

main();

- I run the script in terminal: node index.js
Output:
Connected to MongoDB!
Document inserted!
Query result: { _id: ObjectId('...'), name: 'Alice', age: 25 }

 - I verify in MongoDB compass by connect to my MongoDB instance and check the testDB database.

 Step 4: Push Code to GitHub

 - I created a file .gitignore and then added the node_modules into the .gitignore file
- I commit changes with this code:
git add .
git commit -m "Add NodeJS script and MongoDB connection"
- Lastly, I push it to GitHub.