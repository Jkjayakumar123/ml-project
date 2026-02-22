## **Stage 2: Version Control Workflow (Application)**

### Step 1: Stage only specific files  
**Command:**  
`git add train.py utils.py`  
**Explanation:**  
Stages only `train.py` and `utils.py` (not the other files)  
`git add` used to stage the files for commit  

---

### Step 2: Commit the changes  
**Command:**  
`git commit -m "Add training script and utilities"`  
**Explanation:**  
`git commit` creates a snapshot of staged changes with a descriptive message.  

---

### Step 3: Ensure branch is main  
**Command:**  
`git branch -M main`  
**Explanation:**  
Renames current branch to `main` (GitHub default branch).  

---

### Step 4: Create repository on GitHub  
**Explanation:**  
Go to GitHub → Click New Repository → Repository name: `ml-project` → Click Create repository  

---

### Step 5: Link local repo to GitHub  
**Command:**  
`git remote add origin https://github.com/yourusername/ml-project.git`  

**Explanation:**  
Connects your local repository to GitHub.  

---

### Step 6: Push to GitHub  
**Command:**  
`git push -u origin main`  

**Explanation:**  
Pushes your commits to GitHub and sets upstream tracking.  

---

## **Stage 3: Mini-Project - Collaborative Workflow (Synthesis)**

### Step 1: First, commit your local changes  
**Command:**  
`git add utils.py config.py`  

**Explanation:**  
Stage your remaining changes on GitHub.  

**Command:**  
`git commit -m "Update utils and add config file"`  

**Explanation:**  
`git commit` creates a snapshot of staged changes with a descriptive message.  

---

### Step 2: Retrieve teammate’s changes  
**Command:**  
`git pull origin main`  

**Explanation:**  
Fetches changes from GitHub  
Merges them into your local `main` branch  
Since we assume no conflicts, merge happens automatically  

---

### Step 3: Push your updated project  
**Command:**  
`git push origin main`  

**Explanation:**  
Sends new commits from your local (including merged changes) to GitHub  
Now your repo is fully synchronized  

---

### Step 4: Potential Issues & How to Handle Them  

#### Issue 1: Push Rejected – “Your Branch is Behind”  
This issue occurs when teammate has pushed new changes to GitHub after your last pull.  
When we try to push our changes, Git rejects it because our local branch is not up to date with the remote branch.  
Git prevents this to avoid accidentally overwriting someone else's work.  

To resolve this, we need to first pull the latest changes from GitHub using `git pull origin main`.  
After that, we can safely run `git push origin main` to upload your changes.  
This ensures that both our changes and our teammate’s changes are preserved.  

---

#### Issue 2: Merge Conflicts  
A merge conflict happens when two people modify the same part of the same file.  
Git cannot automatically decide which change to keep, so it asks us to manually resolve the conflict.  

Git marks the conflicting sections inside the file with special symbols:  
`<<<<<<<`, `=======`, `>>>>>>>`  

We must open the file, review both versions, decide which changes to keep (or combine them), and remove the conflict markers.  

After fixing the file:  
`git add filename`  
`git commit -m "Resolve merge conflict"`  
`git push`  

Merge conflicts are normal in collaborative projects.  

---

#### Issue 3: Uncommitted Changes Before Pulling  
If we try to pull changes from GitHub while we have uncommitted local changes, Git may stop the operation.  

To fix this:  
`git add .`  
`git commit -m "Save work"`  
`git pull origin main`  

Or temporarily store changes:  
`git stash`  
`git pull origin main`  
`git stash pop`  

This prevents loss of local work.  

---

#### Issue 4: Remote Repository Not Linked  
If we try to push without linking a remote repository, Git shows an error saying that `origin` does not exist.  

To fix this:  
`git remote add origin <repository_url>`  

This step is required only once when setting up the project.  

---

#### Issue 5: Wrong Branch Name  
Sometimes our local branch might be named `master` while GitHub expects `main`.  

To resolve this:  
`git branch -M main`  
`git push -u origin main`  

Keeping consistent branch names avoids confusion.  

---

#### Issue 6: Authentication or Permission Errors (403 Error)  
This problem happens when we do not have permission to push or when authentication fails.  

It may occur if:  
- We are logged into the wrong GitHub account  
- We do not have collaborator access  
- We are using a password instead of a Personal Access Token  

Fix:  
Ensure correct credentials and repository access.  
Generate and use a Personal Access Token if required.  

---

#### Issue 7: Not Pulling Before Starting Work  
If we begin working without pulling the latest changes, our local repository may become outdated.  

Best practice:  
`git pull origin main`  

This ensures we are working on the most recent version of the project.
