# User-Login-System
Develop a User Login System for a banking app using Git Flow, creating and managing branches manually. tip: all merges should be done by open PR (Pull Request)
user Login System by Git Flow
This repository demonstrates the construction of a user login system based on a Git Flow approach with an emphasis on using the `git rebase` command for conflict resolutions, as per the steps provided for the assignment. Each step outlines the Git commands used and the rationale behind them in order to provide for the development cycle of the project while maintaining a linear history wherever feasible.
Task 1- Set Up Repository
Git Commands Used
- git clone (user-login-system - https://github.com/BudiDulce/User-Login-System ) GitHub link
Then to into the directory
cd user-login-system
Then to go to main branch we use command “Git chechkout”
git checkout main
Then we created a new branch called “ development” by using Git branch command
git branch development
Sum up :
We're checking out a new branch called development to try out new things without interfering with main. It's a replica of main at the moment.
git checkout development ( to go the development directory)
Now we're checking out our development branch to continue our work.
touch File1.txt to create a empty file in .txt form by using bash command touch
while we are in development branch
git add file1.txt to add this new file to the development branch
git commit -m "file1.txt" to commit a copy of our project and giving it a tag by using -m “”
Then we push it to the remote repo
git push origin development
Task 2: Feature Branch
Git Commands Used:
git checkout development
Gitt checkout -b feature or we can use the Git branch feature to create a new branch
echo "Implement the login functionality" >> File1.txt to write into the file we created
git add file1.txt to add the new edits the followed by
git commit -m "" and gave it name tag the we push it
.
git push origin feature to push it to the remote repository in github
Task 3: Simulate Merge Conflict
Git Commands Used:
Again back to git checkout development
echo "" >> file1.txt to add a new line in that file
git add file1.txt
git commit -m ""
git push origin development
then
git checkout feature
Back to the feature branch to make another change on the feature branch and pushing it online
echo "" >> file1.txt
git add file1.txt
git commit -m ""
git push origin feature
____________________________
Then Trying to merge feature branch with development branch. We trying to merge but there will be a conflict and we will continue and solve it
git checkout development
git merge feature
we resolved the conflict in file1.txt manually, we inform git that it is resolved and store that resolution in the remote repo
git add file1.txt
git commit -m "" giving it a tag related to solving the problem
git push origin development
Task 4: Integrate Feature (using rebase later) Instead of a typical merge, we're doing rebase. This applies our development updates and plays them again as if they were done after the feature update. It leaves a tidier, linear history. We force-push afterwards because we've changed history.
By using the following commands :
git checkout development
git rebase feature/login
git push origin development --force-with-lease
Then
We're informing git that we're done with the standalone featurebranch and removing it locally and on the web (although we're simply logging this, not actually removing).
git branch -d feature
git push origin --delete feature
Task 5: Prepare Release We are branching a new track release 0 from our development to stage a new version.
git checkout development
git checkout -b release or by just using git branch release
git push origin release
Task 7: Add More to Feature (even though it's "merged") Going back to the login feature branch to put in some additional content
git checkout feature
echo "Case 1" >> file1.txt
git add file1.txt
git commit -m " Case 1 to file1"
git push origin feature
echo "Case 2" >> file1.txt
git add file1.txt
git commit -m "Case 2 to file1"
git push origin feature
echo "Case 3" >> file1.txt
git add file1.txt
git commit -m "Case 3 to file1"
git push origin feature
Task 8: Selectively Bring Changes to Release (using rebase)
git checkout release
Merging selectively only the changes of "Case 1" and "Case 2" from the login feature branch into our release track online by using what is so called cherry-pick command
git cherry-pick <commit-id-for-Case-1>
git cherry-pick <commit-id-for-Case-2>
git push origin release
git checkout main
git rebase release
git push origin main
git checkout development
git rebase release
git push origin development
Saying that we're done with the release branch for now and removing it locally and remotely (just documenting, not destroying).
git branch -d release
git push origin --delete release
Task 9 : Hotfix
We found a big problem! We are building a new, emergency branch from our main,
git checkout main
git checkout -b hotfix or git branch hotfix
git push origin hotfix
We are adding the fix to our file and committing on the hotfix branch online.
echo "Security fixes applied" >> file1.txt
git add file1.txt
git commit -m "" we gave it a name tag
git push origin hotfix
We're pushing our urgent fixs :
git checkout main
git rebase hotfix
git push origin main
and then to the development branch as well
git checkout development
git rebase hotfix
git push origin development
Then we deleting the hotfix branch we made locally and remotely
git branch -d hotfix
git push origin --delete hotfix
Task 10:
Checking commit history by using git log :
git log --graph --oneline
Going back in time on our development branch to change its history. We're choosing the point before when we'd added "Case 2git checkout development
git rebase -i < 7562f1e >
(Then, in the editor, we would have swapped pick for drop for the "Case 2" commit.)
Pushing our cleaned-up development branch
git push origin development
