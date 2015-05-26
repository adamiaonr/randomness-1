# Another Git tutorial


## Submodules
I need a git repository inside another git repository without messing stuff up. How do I do this?

```
$ ls -a ~/main_project

	.git
	README.md
	main_project_file.c
	main_project_file.h
 	main_project_file.txt
	sub_project1/
	sub_project2/
```

Here, `main_project` is dependent of 2 other subprojects `sub_project1` & `sub_project2` in their own git repos.

```
$ git submodule add https://url/to/submodule
```
**Question:** What if the submodule is a local directory?