# Aliases

1. Change default git editor to VSCode (```--global``` or ```--local```)

```
git config --global core.editor "code --wait”
```

1. Open gitconfig for edit (you use  this for ```—global``` too) 

```
git config --local --edit
```

1. Add Alias for commands: you can create any combination and programs with bash using this example 

```
[alias]
	example= "!f() { \
		echo 'Hello! this is alias example.'; \
		echo '🦥'; \
        }; f"
```

1. Save file and run new command

```
git example
```

As a result, you should see the following 

```
$ git example
Hello! this is alias example
🦥
```

1. Now, if we want to add time stamp to our commits, we can use bash syntax, for example

```
$ echo "$(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')"
(Mon, Mar 27, 2023 07:42:50 AM)
```

By combining git commands and timestamps, the aliases can look like this (with RSSchool guidline)

```
[alias]
	mdocs = "!f() { \
		git commit -am \"docs:📜 $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')\"; \
        }; f"
	minit = "!f() { \
		git commit -am \"init: $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')\"; \
        }; f"
	mfeat = "!f() { \
		git commit -am \"feat:🦄 $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')\"; \
        }; f"
	mfix = "!f() { \
		git commit -am \"fix:🐞 $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')\"; \
        }; f"
	mref = "!f() { \
		git commit -am \"refactor:✨ $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')\"; \
        }; f"
```

Note: try not to use reserved words such as init.

To commit, you just have to execute:

```
$ git minit "starting task"
[gh-pages 80eff88] init: starting task  (Mon, Mar 27, 2023 07:49:17 AM)
```

PS: You can combine commands or execute entire scripts, for example this alias combine commit and push

```
pref = "!f() { \
		echo 'refactor:✨' $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)'); \
		git commit -am \"refactor:✨ $1 $(TZ='Moscow' date +' (%a, %b %d, %Y %I:%M:%S %p)')\"  && git push; \
        }; f"
```

