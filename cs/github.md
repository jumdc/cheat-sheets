 <img width="300" alt="octocat" src="https://user-images.githubusercontent.com/62952163/205496926-f04a3e92-c632-4619-901d-6a689ff43fe2.png">    
 
 

- [git fetch \& pull ](#git-fetch--pull-)
    - [git fetch](#git-fetch)
    - [git pull](#git-pull)
- [Branches](#branches)
- [Useful commands \& infos](#useful-commands--infos)
  - [.gitignore  ](#gitignore--)
  - [remove git dir](#remove-git-dir)
  - [store credentials](#store-credentials)
  - [remove last commit](#remove-last-commit)



> GitHub is a code hosting platform for version control and collaboration.  


# git fetch & pull <a name="fetch"></a>
### git fetch
`git fetch` is the command that tells your local git to retrieve the latest meta-data info from the original (yet doesn’t do any file transferring. It’s more like just checking to see if there are any changes available).

### git pull 
`git pull` on the other hand does that AND brings (copy) those changes from the remote repository.

# Git merge & branches 
> Branches allow you to develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository.

Say that we have a new branch `feature`that is based on `main`. We did a few commits, and we now want to merge this feature into `main`.
<img width="439" alt="image" src="https://github.com/jumdc/cheat-sheets/assets/62952163/195be558-d01e-4fcd-af33-6157662fc581">

Invoking this command will merge the specified branch `feature` into the current branch. 

<img width="439" alt="image" src="https://github.com/jumdc/cheat-sheets/assets/62952163/23e23765-7b4d-4d14-bd23-73658d61cbfa">

A fast-forward merge can occur when there is a linear path fro mthe current branch tip to the target branch. Instead of actually 'merging', all Git has to do to integrate the history is move (i. fast-forward) the current branch tip up to the target branch tip. 
<img width="439" alt="image" src="https://github.com/jumdc/cheat-sheets/assets/62952163/129a883b-b78d-4dcc-a940-cd7f5f8dc759">

```bash
# Start a new feature
git checkout -b new-feature main
# Edit some files
git add <file>
git commit -m "Start a feature"
# Edit some files
git add <file>
git commit -m "Finish a feature"
# Merge in the new-feature branch
git checkout main
git merge new-feature
git branch -d new-feature
```

# Useful commands & infos
##  .gitignore  <a name="ignore"></a>
Create a file `.gitignore`, add directories wished to be ignored from your git remote repository. 

## remove git dir 
`rm -rf .git`

## store credentials 
`git config --global credential.helper store`

## remove last commit
- preserve the changes : ` git reset --soft HEAD~1`  
- if you don't want to keep the changes : `git reset --hard HEAD~1`

# A few useful links 
- [Git merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge#:~:text=Merging%20is%20Git's%20way%20of,merge%20into%20the%20current%20branch.)
