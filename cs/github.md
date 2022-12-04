# git cheatsheet 
 <img width="300" alt="octocat" src="https://user-images.githubusercontent.com/62952163/205496926-f04a3e92-c632-4619-901d-6a689ff43fe2.png">

## Summary 
1. [git fecth & pull](#fetch)
2. [git merge](#merge)
3. [.gitignore](#ignore)
4. [remove git dir](#remove)
5. [store git credentials](#credantials)


## git fetch & pull <a name="fetch"></a>
### git fetch
`git fetch` is the command that tells your local git to retrieve the latest meta-data info from the original (yet doesn’t do any file transferring. It’s more like just checking to see if there are any changes available).

### git pull 
`git pull` on the other hand does that AND brings (copy) those changes from the remote repository.

## git merge
Let say we have created a __feature branch__ from the __main branch__ and we want to merge them i.e commit the change from the __feature branch__ into the __main branch__.


## .gitignore  <a name="ignore"></a>
Create a file `.gitignore`, add directories wished to be ignored from your git remote repository. 

## remove git dir 
`rm -rf .git`

## store credentials 
`git config --global credential.helper store`
