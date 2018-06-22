# Problems & Solutions

This is a personal repository for tracking problems and solutions that I've come across mostly while programming.

# Issue 01:
- Problem: brew error after `brew install opencv3`.

	```
	Permission denied @ dir_s_mkdir - /usr/local/Frameworks
	```
- Date: 2018-06-22 Friday    
- Environment: macOS High Sierra v10.13.5
- Solution: 
  - [https://stackoverflow.com/questions/16432071/how-to-fix-homebrew-permissions](https://stackoverflow.com/questions/16432071/how-to-fix-homebrew-permissions)
   
	``` 
	sudo chown -R $(whoami) $(brew --prefix)/*
	```
