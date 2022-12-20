

### Making the tree right when you split two commits and into two branches


if you make changes in your local reposity that you want to push to the remote while bypassing the requirement for a fast-forward merge (ie you want to maintain the changes to your local which remove some commit present in the remote, for example) then you simply run:


```
	git push --force origin master
```

**Additionally, if you want to push all branches, then run this:**

```
	git push --all origin
```

*This concludes the current prototyping. As you can observe, this repository has two branches and several commits on each branch, some of which are the result of splitting commits. Obviously, you don't typically want to make these changes if you've already pushed it to a remote that others are also working on.*
