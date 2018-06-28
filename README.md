# Problems & Solutions

This is a personal repository for tracking problems and solutions that I've come across mostly while programming.

- [Issue-01](## Issue 01): Installing opencv3 on macOS using brew
- [Issue-02](## Issue 02): Installing boost
- [Issue-03](## Issue 03): Deploying Flask app on Heroku
- [Issue-04](## Issue 04): Binding opencv3 with python3


---

## Issue 01:
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
	
## Issue 02:
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

## Issue 03:
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

	
# Issue 04:
- Issue: binding opencv3 on python3 (not using brew python3, but using anaconda python3)
- Date: 2018-06-27 Wednesday
- Environment: macOS High Sierra v10.13.5
	- conda==4.5.4 (anaconda3)
	- pip==10.0.1 (anaconda3)
- Procedure:

	```
	# 1. (MUST) Create virtual environment with python3.5 and conda
	$ conda create -n opencv python==3.5.5 conda   # for example
	$ source activate opencv
	
	# 2. Install opencv3
	$ conda install -c menpo opencv3
	
	# 3. Test
	$ python
	>> import cv2
	>> cv2.__version__  # e.g., '3.1.0'
	```

- Note:
	- If you are using openface, install opencv3 using homebrew as the instruction tells you. You have to bind brew-installed opencv3 to python3, but python3 has to be homebrew-installed, which might make your python version complicated. I preferred sticking to anaconda python3.
	
- References:
	- [https://stackoverflow.com/questions/38787748/installing-opencv-3-1-with-anaconda-python3](https://stackoverflow.com/questions/38787748/installing-opencv-3-1-with-anaconda-python3)
