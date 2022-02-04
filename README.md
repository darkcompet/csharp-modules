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


## Module List

- Core module (`Tool.Compet.Core`)
	
	```bash
	# For all modules (csharp-*-*)
	https://github.com/darkcompet/csharp-core.git
	
	# For Unity modules (csharp-unity-*)
	https://github.com/darkcompet/csharp-unity-core.git
	```

- Json module (`Tool.Compet.Json`)

	```bash
	# For Net
	https://github.com/darkcompet/csharp-net-json.git
	
	# For Unity
	https://github.com/darkcompet/csharp-unity-json.git
	```

- Http module (`Tool.Compet.Http`)

	```bash
	# For All
	https://github.com/darkcompet/csharp-core-http.git

	# For Net
	https://github.com/darkcompet/csharp-net-http.git
	
	# For Unity
	https://github.com/darkcompet/csharp-unity-http.git
	```

- Log module (`Tool.Compet.Log`)

	```bash
	# For Net
	https://github.com/darkcompet/csharp-net-log.git
	
	# For Unity
	https://github.com/darkcompet/csharp-unity-log.git
	```

- Preference module (`Tool.Compet.Preference`)

	```bash
	# For Unity
	https://github.com/darkcompet/csharp-unity-preference.git
	```


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
	
	git submodule add https://github.com/darkcompet/csharp-net-log.git
	git submodule add https://github.com/darkcompet/csharp-net-json.git
	git submodule add https://github.com/darkcompet/csharp-net-http.git

	git submodule add https://github.com/darkcompet/csharp-unity-core.git
	git submodule add https://github.com/darkcompet/csharp-unity-log.git
	git submodule add https://github.com/darkcompet/csharp-unity-json.git
	git submodule add https://github.com/darkcompet/csharp-unity-http.git
	git submodule add https://github.com/darkcompet/csharp-unity-preference.git
	git submodule add https://github.com/darkcompet/csharp-unity-realtime.git
	git submodule add https://github.com/darkcompet/csharp-unity-messagepack.git
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
