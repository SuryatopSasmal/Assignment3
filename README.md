# Assignment3-4
# Assignment3
**Objective:** Experience working with branches and resolving conflicts.
**Tasks:**
1.	Create a new repository implementing GitHub Flow
   <pre>
     https://github.com/SuryatopSasmal/Assignment3
   </pre>
GitFlow in this assignment:
</br>
![image](https://github.com/user-attachments/assets/f87d35c5-0696-4e29-a93e-0704211d0c41)
</br>
2.	Create a simple web page with HTML/CSS or a script in your preferred language/ technology
</br>
<pre>
  <img src="https://github.com/user-attachments/assets/2217053e-606e-4b48-bbf9-11ba7f76fac0">

</pre>
![image](https://github.com/user-attachments/assets/93fefb10-b53d-4ec6-aa58-1603261bcc97)
</br>
3.  Create two feature branches from main: </br>
  o	Branch A: "feature/update-styling" - Update styling or formatting </br>
  o	Branch B: "feature/add-content" - Add new content </br>

  <pre>
    git branch feature/update-styling
    git switch feature/update-styling
    //ad h1,h2 in style
    //change in h1
    
    
    git branch feature/add-content
    git switch feature/add-content
    //ad para and background_color
    //change h1

  </pre>
  </br>

4.	Make commits to both branches, ensuring they modify the same files in different ways
   </br>
<img src="https://github.com/user-attachments/assets/83994878-f46e-45f6-8309-ab0a58baf066">
<img src="https://github.com/user-attachments/assets/79e9a85f-f32a-4b82-94ab-3bda1e105673">
5.	Create pull requests for both branches
   </br>
   <img src="https://github.com/user-attachments/assets/c5f5652b-74b2-4de6-ab0b-1430ef1e82ab">
</br>
6.	Merge one branch first
   <img src="https://github.com/user-attachments/assets/e080d5a0-8b74-4e43-8df4-5782ebbb9aa0"> </br>
7.	Experience and resolve the merge conflict with the second branch </br>
    <img src="https://github.com/user-attachments/assets/536f4d52-b3bf-42c0-ae50-75e13f47d9fe">
</br>
  <img src="https://github.com/user-attachments/assets/58ebafff-0cd6-4a9f-a1b5-99e577cef545">
</br>
8.	Successfully merge both changes </br>
   <img src="https://github.com/user-attachments/assets/efbb817e-7ce5-4d23-a7f2-42cc46916a65"> </br>
</br>
in VSCode we have<b> Resolve in merge editor </b> bu clicking 
    <img src="https://github.com/user-attachments/assets/7a1a470c-26e9-4d1d-9d9f-8fd668688a11"> </br>
we can see two page prompt, by clicking desire code - it will get resolved.
<img src="https://github.com/user-attachments/assets/9f33a72f-295d-4ea8-a2a1-a31139c10be1"> </br>

<p><b>With this i resolve the conflict</b></p>

# Assignment4: Git Hooks & Automation
**Objective:** Learn to implement quality controls and automation in Git workflow.
**Tasks:**
Working on setting up quality controls and automation in a Git project using Husky, lint-staged, commitlint, and GitHub Actions.
STEP_1:
1. Initialize a project
   <pre>
      mkdir git-quality-control
      cd git-quality-control
      npm init -y
      git init
   </pre>
2. Install required packages
   <pre>
       npm install husky lint-staged --save-dev
   </pre>
  
3. Enable Husky hooks
   <pre>
      npx husky install
   </pre>
   Add this line to package.json under "scripts":
   <pre>
      "scripts": {
  "prepare": "husky install"
}
   </pre>
Then run:
<pre>
   npm run prepare
</pre>
here i learned to set up Repo with Husky and lint-staged
STEP_2:
1. Install Iinters
   <pre>
      npm install eslint prettier --save-dev
   </pre>
2. Initialize ESLint
   <pre>
      npx eslint --init
   </pre>
Create .prettierrc:
<pre>
   {
  "semi": true,
  "singleQuote": true
}
</pre>
Configure lint-staged in package.json
<pre>
   "lint-staged": {
  "*.js": [
    "eslint --fix",
    "prettier --write"
  ]
}
</pre>
STEP_3:
1. Add pre-commit hook
   <pre>
      npx husky add .husky/pre-commit "npx lint-staged"
   </pre>
2. Install commitlint
   <pre>
      npm install --save-dev @commitlint/{config-conventional,cli}
   </pre>
Create commitlint.config.js:
3. Add commit-msg hook
<pre>
   npx husky add .husky/commit-msg 'npx --no-install commitlint --edit $1'
</pre>
here i learned Huskey Hooks
STEP_4:
Test Commits with Issues
-Try committing:
-Bad code formatting
-Linting errors
-Invalid commit messages
-You should see these are rejected before committing.
STEP_5:
Create .github/workflows/lint.yml:

<pre>
   name: Lint Check

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
    - run: npm install
    - run: npx eslint .
</pre>
//GitHub Actions CI for Linting

Outcome:
   Rejected commits
   Successful commits
   GitHub Action passing
   -according to the GitHub Actions lint workflow

