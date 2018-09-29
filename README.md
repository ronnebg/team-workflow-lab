# Team GIT Workflow Lab

In this lab you will practice following a workflow that will help you to collaborate as an engineering team on joint project that is stored in git.

The lab will walk you through the following steps:


### Team members

For the purposes of this lab, each team member will pick one of the following colors. 

- Red
- Green 
- Blue
- Yellow

We will use each team members color as their name in the instruction below. 
Before you start with lab, agree within your team which team member gets which color. 


### Step 0: Create a project repository for the team:

1. Pick **one** team member to fork (= copy) the [lab repository](https://github.com/ronnebg/team-workflow-lab) to 
   their Github space:
   - Follow this [link](https://github.com/ronnebg/team-workflow-lab)
   - Click on the button labeled **Fork** on the top right of the screen
   - Select your personal github space as the destination where the team repository will be created.
2.  Permission all team members as collaborators:
   - Click the **Settings** button on the just created fork of the project repository
   - Select **Collaborators**, and add all team members as collaborators
   - Each team member should accept the collaboration invitation.
3. _[Optional]_ Protect the master branch of the repository from being written to directly:
   - Click the **Settings** button on the just created fork of the project repository
   - Select **Branches** adn then click on **Add rule** in Branch protection rules and check off the following:
      - :white_check_mark: _Require pull request reviews before merging_
      - :white_check_mark: _Include administrators_
4. Each team member now should clone the team repository to their computer.  In git bash run:
   ```
       git clone <link-to-team-repository>
   ```   

### Step 1: Create Feature Branch and Make First Contribution

The instrunctions below are written for team memeber *Red*, but should be followed accordingly by the other team members as well.

1. In git bash, ensure you are in the folder/directory that contains the project. 

   Run `git remote -v` - this should list the project repository on the Github server and look similar to this:

   ```
   origin	git@github.com:jadelet/team-workflow-lab.git (fetch)
   origin	git@github.com:jadelet/team-workflow-lab.git (push)
   ```

2. Create a branch called `red` for you to do your work on:

   ```
   git checkout -b red
   ```

   _Note_: Branch names should brief, but descriptive. They must not contain spaces, but people use hyphens to separate words if needed. 

3. In the `docs` folder add a file called `red.md` with the content
   ```
   Team member RED is John Doe.
   ```

   _[Optional]_ Check if git notices the new file:

   ```
   git status
   ```

   This should list `docs/red.md` in red, indicating it is a new file that needs to be added. 
   

4. Add the file the file to git:
   ```
   git add docs/red.md
   ```
  
   Running `git status` will show the file in green now, indicating that the file is not ready to be commited

   Commit the file 
   ```
   git commit -m 'add file red.md showing who team member red is'
   ```

5. Commit the content of the feature branch to the team repository on Github:

   ```
   git push -u origin red
   ```

   _Note:_ Remember, at this point you are on your feature branch red, but this branch does not exist yet in the team repository on Github.  The push command creates this new branch in the team repository. The flag `-u` in the command connects the local copy of your branch to the new created branch on the server.  This way, going forward, future commits can be made using `git push origin red`.

6. Create a _Pull Request_  (PR) to request a code review and merge the code into the `master` branch:

   - Go to the team repository on Github and click on **New Pull Request**. 

   - In the window that opens up, make sure the **right** button says `red` (the name of the source branch) and the 
     **left** button says `master` (the name of the target branch). 

   - Add a brief comment about the changes that were made in this update

   - Click **create pull request**.

   - Assign a team member to review the code: under **Assignees** add one of your team members. In this example, assign the PR to team member Blue.  

7. Team member Blue now reviews the changes and merges it into the `master` branch:
  
   - Blue opens the team repository on Github and selects the **Pull requests** tab towards the top of the page.

   - Open the pull request that Red had created and click on **Files changed**. This will show all the changes that 
     Red made.

   - _[Optional]_ It is possible to add comments to the changes that Red made. Hover over a new line (one with a green background), towards the line number. and then click on the blue `+` symbol that appears. Enter a short comment. Click either **Add single comment** or **Start a review** depending on wether your planning to provide more comments.

   - To approve the changes, click on the green button **Review changes**, select **Approve** and click submit review.

   - On the next screen, there should now be a green button **Merge pull request**, click it merge the changes into the master branch. 

8. All  team members (except Red) should now retrieve the updated code. In project folder in git bash:

   - Checkout the master branch:  `git checkout master`.  
   
     If you have made changes in your folder that you have not commited to git,  you will need to commit them first with `git add ...put.your.file.names.here...` and then `git commit -m '... put commit message here..'`

   - Retrieve the updated `master` branch:

     ```
     git pull master
     ```

   - Merge the changes into your feature branch.  E.g, if you are user Blue, run

     ```
     git checkout blue
     git merge master
     ```

     This should not cause a merge conflict in this lab. In the next step we will discuss how to handle merge conflicts when 
     they do arise.

     **Important**: As a best practice, always merge `master` into your feature branch when working in a team, not the other way around.  Any code that gets added to the `master` branch needs to be added through a pull request. 
