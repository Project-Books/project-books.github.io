# Rewriting pushed commits with a different email address

_Step 1:_

While on your feature branch, run 
`$ git rebase -i HEAD~n` where _n_ are the number of commits you would like to change

This will then open your commits in the default text editor for Git (which may be Vim or Vi, so you may wish to change this if you prefer a different editor).

_Step 2:_ 

Change the lines with 'pick' to 'edit' and then save and quit the file

_Step 3:_

`$ git commit --amend --author= "[Your name] [your email address as shown on GitHub]" --no-edit`

_Step 4:_

`$ git rebase --continue`

You'll need to run steps 3 and 4 _n_ number of times, where n represents the number of commits that you are rewriting.

_Step 5:_ 

Once you've finished with the rebase, force push: 

`$ git push -f origin [your-branch-name]`