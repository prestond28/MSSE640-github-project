# Github Project Assignment 3
## Git Configuration

This is how you configure your username and email with git:

```
git config --global user.name <username>
git config --global user.email <email>
```
Notice the --global flag that will set this for all your local repositories. It's best to have this set to global just so you only set it once and you don't have to keep track of multiple usernames and/or emails, especially if these are your personal repositories that are for school or personal projects.

To view the current config you have set for the repo, you can use the same command but just omit the parameters after user.name or user.email:

```
git config user.name
git config user.email
```

When I ran this in my terminal, this is the output I got:

```
prestond28
pdavis2897@gmail.com
```

Notice that this time I also omitted the --global flag. If you leave that out, git will default to the local repo configs. So if you want to do anything globally, make sure you include --global. You can also include --local in place of --global if you want to be sure you are affecting only the local repository.

## Working with a local repo

To start a new local repo:

```
git init
```

Make sure you are in the correct folder, or create the necessary folder first before you initialize the repo.

To clone an existing repo:

```
git clone <repo-url>
```

Cloning a repo copies all of the files from the target repo and creates a local copy saved to your device. It also includes all of the history and branches of the repo. This is useful in saving some time if you want to create a similar repo from an already existing one and don't want to start from scratch.

To check the status of your repo is quite simple:

```
git status
```

You should see something similar to what I got for output:

```
On branch develop
Your branch is up to date with 'origin/develop'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Week4/

nothing added to commit but untracked files present (use "git add" to track)
```

Git will tell you what branch you are working on, changes to any files, and which files are staged to commit. You can see in my example it told me I have an untracked file (because I just created it and have not yet committed it to the repo).

To stage changes to your repo in preparation to commit those changes:

```
git add <filename>
```

To commit changes to your repo that have been staged:

```
git commit -m "commit message"
```

If I want to ignore some files while I stage and commit the rest, I can store those file names (or every file with the same extension) in a config file that git can read. It's usually a file called .gitignore placed at the root of your directory. Some files I would want to ignore, for example, are all the files in the node_modules folder if you are making a project with a package_json config file. There can be thousands of files in that folder, and they are changed and updated all the time, plus, they are downloaded automatically to your local machine if your config file notices they are missing or out of sync. So, there really is no point in uploading all those files.

To delete files under version control using git:

```
git rm <filename>
```

## Working with a remote repo

To view the remote repo associated with your local repo:

```
git remote -v
```

One command that is useful is:

```
git fetch
```

Git fetch downloads any data that is new from the remote repository, like any added branches or commits to the repo. It doesn't upload any of your work, and it doesn't merge any of the new changes into your working directory, but acts like a refresh button to see the latest updates from others and the work they've done.

Git pull, on the other hand, will fetch and merge any new updates from the remote repo directly into your local copy. It still doesn't upload any of the work you've done to the remote repo.

Examples of each and their outputs:

```
git fetch
```
```

```
I got no output (which is a good sign because nothing went wrong)

```
git pull
```
```
Already up to date.
```

After you commit changes to your local repo, you still have to sync those changes with the remote repo. Use this command:

```
git push
```

Heres an example of what I did from start to finish to sync some changes I made to my repo:

```
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git add .
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git commit -m updates
[develop c016e83] updates
 1 file changed, 122 insertions(+)
 create mode 100644 Week4/Assignment3Davis.md
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 2.04 KiB | 2.04 MiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/prestond28/MSSE640-github-project
   0bdce6f..c016e83  develop -> develop
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project>
```

## Branches

To view branches in a repo:

```
git branch  ///this will show you local branches

git branch -r  ///this will show you remote branches

git branch -a  ///this will show you both local and remote branches
```

I'm going to create a new local branch, but before I do that, I'll show you what my current branches are:

```
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git branch
* develop
  main
```

The asterisk next to the develop branch means that tha is the one I am currently on.

To add a branch is simple, just add a name for the branch after the command:

```
git branch <name>
```

Example:

```
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git branch test
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git branch
* develop
  main
  test
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> 
```

To switch to a new branch:

```
git checkout <branch_name>
```

To delete a local branch:

```
git branch -d <branch_name>
```

Example:

```
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git branch -d test
Deleted branch test (was c016e83).
PS C:\Preston\Regis_University\MSSE640_X70\MSSE640-github-project> git branch 
* develop
  main
```