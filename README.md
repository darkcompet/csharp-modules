# C# Modules
This repo contains all C# modules which be used in projects.


## Concept
Suppose we want to implement a feature over some frameworks.

For eg,. we wanna implement `http` networking on frameworks: `Net, Asp, Unity`.
We will create below 4 repositories instead of 3 repositories to share source code between frameworks.
Note that, we should use same namespace `Tool.Compet.Http` on repos.

```bash
	# Shared part (written in C#)
	https://github.com/darkcompet/cs-http.git
	# Implementation of .NET Core
	https://github.com/darkcompet/cs-net-http.git
	# Implementation of Asp
	https://github.com/darkcompet/cs-asp-http.git
	# Implementation of Unity
	https://github.com/darkcompet/cs-unity-http.git
```

Note that, each lib in framework is based on their core lib,
for eg,. `cs-net-http` is based on `cs-net` which is based on `cs`.


## How this project was made

- Setup

```bash
	# Init git
	git init
	nano README.md

	# Create modules folder
	mkdir tool; mkdir tool/compet; cd tool/compet;

	# Add git submodules
	git submodule add https://github.com/darkcompet/cs.git
	git submodule add https://github.com/darkcompet/cs-http.git
	git submodule add https://github.com/darkcompet/cs-messagepack.git
	git submodule add https://github.com/darkcompet/cs-photon.git
	
	# For .NET Core
	git submodule add https://github.com/darkcompet/cs-net.git
	git submodule add https://github.com/darkcompet/cs-net-log.git
	git submodule add https://github.com/darkcompet/cs-net-json.git
	git submodule add https://github.com/darkcompet/cs-net-http.git
	
	# For ASP.NET Core
	git submodule add https://github.com/darkcompet/cs-asp.git
	git submodule add https://github.com/darkcompet/cs-asp-photon.git
	
	# For Unity
	git submodule add https://github.com/darkcompet/cs-unity.git
	git submodule add https://github.com/darkcompet/cs-unity-log.git
	git submodule add https://github.com/darkcompet/cs-unity-json.git
	git submodule add https://github.com/darkcompet/cs-unity-http.git
	git submodule add https://github.com/darkcompet/cs-unity-preference.git
	git submodule add https://github.com/darkcompet/cs-unity-photon.git
	git submodule add https://github.com/darkcompet/cs-unity-messagepack.git

	# Make as dotnet app
	dotnet new console
```


## Others

- Register new module

```bash
	# Turn off root git
	mv .git .git-tmp

	# Make new module
	# For faster, just copy a module from tool/compet to current folder.
	mkdir cs-mymodule && cd cs-mymodule

	# Publish the module
	# For faster, go with vscode Lens plugin
	mkdir src
	touch .gitignore README.md
	git init
	git add --all
	git commit -m "Initial commit"
	git push
	cd ../

	# Delete create module
	rm -rf cs-mymodule

	# Get back root git
	mv .git-tmp .git

	# Add the module to this project
	cd tool/compet
	git submodule add https://github.com/darkcompet/cs-mymodule.git
	cd ../..
```

- How to remove a submodule

```bash
	# Goto directory of added submodules and Delete from git
	cd tool/compet
	git submodule deinit -f cs-core
	git rm -f cs-core

	# Delete from disk
	rm -rf .git/modules/tool/compet/cs-core

	# Delete record from .gitmodules
	Manually delete lines of the submodule from file `.gitmodules`
```
