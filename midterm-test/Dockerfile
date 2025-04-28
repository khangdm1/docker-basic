# Use this empty Dockerfile to build your assignment

# This dir contains Python app, you need to get it running in a container
# No modifications to the app should be necessary, only edit this Dockerfile

# Instructions from the app developer
# - you should use the 'ubuntu' official image
FROM ubuntu:18.10
# - then it should install the Python pip package to the ubuntu linux distribution: 	
		# 'apt-get update -y'
		# 'apt-get install -y python-pip python-dev build-essential'
	# optimize it !
RUN apt-get update -y\
&& apt-get install -y python3-pip python3-dev build-essential\ 
&& rm -rf /var/lib/apt/lists/*
# - then it should create directory /usr/src/app/ for app files with 'mkdir -p /usr/src/app/'
RUN mkdir -p /usr/src/app/
WORKDIR /usr/src/app/	
# - then it needs to copy requirements.txt and app.py to /usr/src/app/
COPY requirements.txt . 
# - then it needs to run 'pip install --no-cache-dir -r /usr/src/app/requirements.txt' to install dependencies from that file
RUN pip3 install --no-cache-dir -r requirements.txt
# - this app listens on port 5000, but the container should launch on port 80
EXPOSE 5000
COPY app.py .
  #  so it will respond to http://localhost:80 on your computer
# - then it needs to start container with command 'python /usr/src/app/app.py'
CMD ["python3", "./app.py"]
# - build this dockerfile with another optimize images and find a smallest