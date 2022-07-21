# C# Modules

This is git repo, just for management, contains all C# modules which be used in other projects.


## Module concept

Suppose we want to implement a feature over some frameworks.

To make it simple, for eg,. we wanna implement `http` networking for frameworks: `Net, Asp, Unity`.
We just need one namespace `Tool.Compet.Http` for all that frameworks, and need below 4 repositories
instead of 3 repositories to handle sharing source code between frameworks.

```bash
# Share abstraction/implementation stuffs between frameworks
https://github.com/darkcompet/csharp-core-http.git
# Implementation for Net
https://github.com/darkcompet/csharp-net-http.git
# Implementation for Asp
https://github.com/darkcompet/csharp-asp-http.git
# Implementation for Unity
https://github.com/darkcompet/csharp-unity-http.git
```

At `Core` module, we should provide abstraction, and implement stuffs which is unique implementation
over all frameworks.
Because, if there exists 2 ways to implement a `http` feature at `Core` and `Unity`, then we have to use
different class names on that frameworks => it is not convenience for using later.


## How this project was made

- Setup

	```bash
	# Init git
	git init
	nano README.md

	# Create modules folder
	mkdir tool; mkdir tool/compet; cd tool/compet;

	# Add git submodules
	git submodule add https://github.com/darkcompet/csharp-core.git
	git submodule add https://github.com/darkcompet/csharp-core-http.git
	git submodule add https://github.com/darkcompet/csharp-core-messagepack.git
	git submodule add https://github.com/darkcompet/csharp-core-photon.git
	# For .NET
	git submodule add https://github.com/darkcompet/csharp-net-core.git
	git submodule add https://github.com/darkcompet/csharp-net-log.git
	git submodule add https://github.com/darkcompet/csharp-net-json.git
	git submodule add https://github.com/darkcompet/csharp-net-http.git
	# For ASP.NET Core
	git submodule add https://github.com/darkcompet/csharp-asp-core.git
	git submodule add https://github.com/darkcompet/csharp-asp-photon.git
	# For Unity
	git submodule add https://github.com/darkcompet/csharp-unity-core.git
	git submodule add https://github.com/darkcompet/csharp-unity-log.git
	git submodule add https://github.com/darkcompet/csharp-unity-json.git
	git submodule add https://github.com/darkcompet/csharp-unity-http.git
	git submodule add https://github.com/darkcompet/csharp-unity-preference.git
	git submodule add https://github.com/darkcompet/csharp-unity-photon.git
	git submodule add https://github.com/darkcompet/csharp-unity-messagepack.git
	```


## How to make new module

- Register new module

	```bash
	# Turn off root git
	mv .git .git-tmp

	# Make new module
	# For faster, just copy a module from tool/compet to current folder.
	mkdir csharp-mymodule && cd csharp-mymodule

	# Publish the module
	# For faster, go with vscode Lens plugin
	git init
	git add --all
	git commit -m "Initial commit"
	git push
	cd ../

	# Delete create module
	rm -rf csharp-mymodule

	# Get back root git
	mv .git-tmp .git

	# Add the module to this project
	cd tool/compet
	git submodule add https://github.com/darkcompet/csharp-mymodule.git
	cd ../..
	```


## Tips

- How to remove a submodule

	```bash
	# Goto directory of added submodules and Delete from git
	cd tool/compet
	git submodule deinit -f csharp-core
	git rm -f csharp-core

	# Delete from disk
	rm -rf .git/modules/tool/compet/csharp-core

	# Delete record from .gitmodules
	Manually delete lines of the submodule from file `.gitmodules`
	```
