# learngit
learngit
Following https://www.liaoxuefeng.com/wiki
Based on youtube: "learn Git in 20 minutes"

Git global setup:
git config --global user.name "liuyongzhiatyahoo"
git config --global user.email "liuyongzhi@yahoo.com"

Basic Operations

git status 				                    #get repository information
git diff <filename> 		                #verify file difference 
git add <filename>							#stage for commit
git commit -m "some message"				#commit into local repo, "git push" to remote
git log --pretty=oneline --abbrev-commit	#log history
git reset --hard HEAD^		                #HEAD -> -1 commit, HEAD^^ -> -2, HEAD~20 -> -20 
git reset --hard 128833ef	                #HEAD -> arbitrary commit


Remove files in filesystem and repo

git rm <filename>
git commit -m "remove a file in both filesystem and repo"
git push

Push an existing folder

git init
git remote add origin git@gitlab.com:YongzhiAtVoith/learngit.git
git add <filename>
git commit -m "notes here"
git push -u origin master


Push an existing repository

git remote add origin git@gitlab.com:YongzhiAtVoith/learngit.git
git push -u origin --all
git push -u origin --tags
git push origin master     #push local repo master branch to remote repository
git push origin dev        #push local repo dev branch to remote repository


Create a new repo based on remote server
git clone git@gitlab.com:YongzhiAtVoith/learngit.git


Create a new branch
git checkout -b dev		#create & checkout 'dev' branch 
git branch dev				#or in two steps
git checkout dev

...(work on dev branch)...

git commit -m "notes"		#local repo in dev branch get updated, ready to mergy with master branch
git checkout master		#switch to master
git merge dev				#merge with master branch

Work out branch conflicts
git pull					#update local repo, in case new update from colleague

Check remote repo information
git remote -v              #display the access previlidge, fetch / push

Collaboration: usually remote repo has master and dev branches
Developer 1:
 git clone ... 
 git branch ...            #only display master branch
 git checkout -b dev origin/dev    #ready working on dev branch
...
 git add ...
 git commit -m "notes"
 git push origin dev       #push to dev branch of remote repo

Developer 2: if also work on the same file, push dev branch to remote -> conflict!
 git pull                  #immediate pull will fail
 git branch --set-upstream-to=origin/dev dev  
 git pull                  #pull would success
...manually merge changes
 git push origin dev       #finally push

Temporarily switch between branches when there is uncommited file:
Before we switch to another branch, "git status" to check if we have change pending.
if there is "git stash", "git checkout" .... "git checkout" back, "git stash apply", ...

 git stash
switch to other branches, and work


Git Account:
SSH Keys contains the client infor: 1) User create SSH keys, 2) upload public key

learngit failed to push/pull, thus removed and cloned from remote. 
1) get out of local learngit/; 
2) rm -fr learngit, 
3) git clone http://..., 
4) cd learngit, 
5) modify and git add....

ADiS Setup: One step to update PIP from Windows Bash  - Proxy needed.
$ python -m pip install --upgrade pip --proxy=http://liyxxxz:Loxxxx73@hdhproxy1.euro1.voith.net:8080
I encountered error when pip install atlas-api in windows or raspberry pi 4.
