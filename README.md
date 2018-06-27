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
# Issue 02:
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

# Issue 03:
- Problem: Deploying Flask app using Heroku
- Date: 2018-06-26 Tuesday
- Environment: macOS High Sierra v10.13.5
	- Flask==0.12.2
	- Flask-SocketIO==3.0.1
	- gunicorn=19.7.1
- Solution:
	- Follow the procedure as **LOYAL** as possible
	- For example,

	```
	# 1. make flask app
	
	# 2. make Procfile
	# web: gunicorn --worker-class eventlet -w 1 app:app --log-file=log.txt
	
	# 3. make requirements.txt
	#    add at least: Flask, gunicorn, flask-socketio, eventlet
	
	# 4. check local web
	$ heroku local web # or python app.py
	
	# 5. creat git repository (DO NOT MAKE GITHUB REPOSITORY FIRST. JUST FOLLOW THIS STEP.)
	$ git init
	$ git add .
	$ git commit -m 'init'
	$ heroku create NAME
	$ git push heroku master
	```
- References: 
	- [http://www.alexhadik.com/blog/2015/1/29/using-socketio-with-python-and-flask-on-heroku](http://www.alexhadik.com/blog/2015/1/29/using-socketio-with-python-and-flask-on-heroku)