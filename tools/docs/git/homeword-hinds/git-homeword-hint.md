# Hint for Git Homework

## Hint 1: 
Following Git flow to do the homework, check the Git Flow again at https://guides.github.com/introduction/flow/ if you still not clear about it.

## Full guidline to do the homework

Clone the repository https://github.com/pa-vuhn/introduceyourself and follow below steps to do the homework with Git Flow

### Step 1: Create new branch and push the changes to the branch

1. Create new branch from `main` with branch name is your-name.
2. Add your information to bottom of the file like:
```
## Huynh Ngoc Vu
- DoB: 1983/05/05
- Email: vuhn@pascaliaasia.com
- Hobbies: Fishing
``` 
3. Add all changes not staged by command `git add -A`
4. Record changes to the repository by commit command `git commit -m "your message"`
5. Push commit to remote repository `git push origin your-branch`
6. Create a Pull Request

### Resolve conflict

When you create a pull request, there is still no conlict, but if one member merge their source code to master branch, there will be conflict. You got the confict because of you and other members modified content at same line of the file. 

Let update your branch by merge branch `main` into `your-branch`, execute below commands:

```sh
# Switch to main branch
git checkout main
# Pull latest changes in main branch
git pull origin main
#Switch to your-branch
git checkout your-branch
# merge changes on main branch into current branch
git merge main
```

After merged, The conflict on readme.md file looks like:

```
<<<<<<< your-branch
## Huynh Ngoc Vu
- DoB: 1983/05/05
- Email: vuhn@pascaliaasia.com
- Hobbies: Fishing
=======
## John
- DoB: 1983/05/06
- Email: vuhn1@pascaliaasia.com
- Hobbies: Fishing1
>>>>>>> main
```

Look above conflict carefully, there are 2 part separated by the line `=======`, above the line is your change, below the line is someone changes in `main` branch. Because you have to keep both changes of you and someone in this case, therefore you should edit the file like blow:

```
## Huynh Ngoc Vu
- DoB: 1983/05/05
- Email: vuhn@pascaliaasia.com
- Hobbies: Fishing

## John
- DoB: 1983/05/06
- Email: vuhn1@pascaliaasia.com
- Hobbies: Fishing1
```

Now, let commit and push your change to remote reposioty again.

```
git add -A
git commit -m "fix conflict"
git push origin your-branch
```

Let check your pull request again, the conflict is solved.

**Even this homework is simple, but in real-life project, you will use git commands usualy and the git process is almost same with above, so that, let exercise more about git with other members by following this tutorial**
