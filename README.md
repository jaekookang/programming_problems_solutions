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
# Issure 02:
- Problem: Installing specific version of boost
- Date: 2018-06-22 Friday
- Environment: macOS High Sierra v10.13.5
- Solution:
	- [https://stackoverflow.com/questions/3987683/homebrew-install-specific-version-of-formula](https://stackoverflow.com/questions/3987683/homebrew-install-specific-version-of-formula)
	
		```
		# Check the specific version of boost
		brew search boost@
		```
		
		```
		# Install boost v1.59
		brew install boost@1.59
		```
		
		```
		# Make sure export BOOST_ROOT variable in .bashrc; e.g.,
		export BOOST_ROOT="/usr/local/Cellar/boost@1.59/1.59.0"
		```