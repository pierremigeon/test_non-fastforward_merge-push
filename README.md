
# Experimental repository: Personal exercises, testing git procedures prior to applying them elsewhere, and notes for future reference
*In application, I am performing these steps for my ft_printf project repository. The exercise will allow me to practice more intermediate level git usage and promote my use of git version control best practice*

## Branching and commit history modification after the fact
I wanted to split the current branch into two tips and also split an earlier commit into two commits.

### Create two branches from one
In order to split a branch into two tips, you create a new branch, and remove from the main branch the commits which you want to be exclusive to the new branch. 
```
git branch new_branch_name
git rebase -i HEAD~2 #add d for drop before the commit that you want to remove 
```
You have now removed the most recent commit(s) from the main branch, while the branch 'new_branch_name' contains these commit(s)

### Spliting commits:

In order to split the most recent commit in two, you can run:
```
git reset HEAD^
git add -p
git commit -m "commit first half"
git add .
git commit -m "commit second half"
```

With interactive git add, you can specify which patches (or specific user defined subsets) to add to the staging area. Simply add the portion you want in a commit, then make the commit, then add uncommited changes as you go.

In order to split commits earlier than the most recent commit, simply nest the commits inside of a interactive rebase. For example, assuming you want to split the penultimate commit: 

```
git rebase -i HEAD~2 #Now change the target commit to e
git reset HEAD^
git add -p
git commit -m "commit first half"
git add .
git commit -m "commit second half"
git rebase --continue
```

### Pushing to remote after changing commit history/branch structure:
if you make changes in your local reposity that you want to push to the remote while bypassing the requirement for a fast-forward merge (ie you want to maintain the changes to your local which remove some commit present in the remote, for example) then you simply run:
```
git push --force origin master
```

**Additionally, if you want to push all branches, then run this:**
```
git push --all origin
```
*Typically, you do not want to make these sorts of changes when it would create different version histories, for example when you've already pushed to a shared remote. Since I am not collaborating with anyone, I felt justified in modifying my commit history.* 

