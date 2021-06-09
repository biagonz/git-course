[user]
	email = biagonz@live.com
	name = Beatriz Silva
[core]
	editor = code
[alias]
  s = !git status -s -> status short
  c = !git add --all && git commit -m
  l = !git log --pretty=format: '%C(blue)%h%C(red)%d %C(white)%s - %(ciano)%cn, %C(green)%cr'
  amend = !git add --all && git commit --amend --no-edit
  count = !git shortlog -s --grep
  prune = !git fetch --prune