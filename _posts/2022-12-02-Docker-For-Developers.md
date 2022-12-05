---
layout: post
title: Docker for Developers 
---

This blog is meant to be a supplementary reading material for the below youtube videos on Docker. However, it can also be used as a standalone reading material to understand docker if you are new to it. 
* [Docker for Developers - English](https://youtu.be/CHP97oqRNgs)
* [Docker for Developers - Malayalam](https://www.youtube.com/watch?v=Q6FfAOKGTzg)


### "It works on my machine problem!"
Have you encountered the notorious "it works on my machine" problem?
If you are a developer, I am sure you have! 
What is this problem? 
We write a code and test it on our machine. When everything works fine, we move the code to a fellow developer or to the testing team only to find that it doesn't work on their machines! 
Does this sound familiar?

### What changes while shipping a code? 
Why does this happen? What changes when we move the code to another team member? Some of the differences could be:
* the operating system in which both of us work
* the difference in the version of the software in which the code is being compiled
* dependencies/libraries and their versions 

### Solving the problem
All of us take different approaches in solving a problem like this. The solution would mostly depend on the technology in which we are working. For eg, if we are working on Python, a readme file mentioning the right version of Python to be used, a properly udpated requirements.txt file and a virtual environment would solve the problem.

However, in this blog, we are trying to solve this problem with Docker. This solution can be extended to work on any language in which you are opting to code. 

### Demo Code 
This demo is done on Python. But, it should not be problem to extend this learning to any other language. The course which I did had this taught in node-js. However, extending this to Python was not a problem. 
So, let us get into the demo. 
Let us try to run [this code](https://github.com/pyari-k/docker-demo) on Python

As per the [readme file](https://github.com/pyari-k/docker-demo#readme), it can be seen that we are trying to run the file `test.py` on Python. The Python version to be used is `3.10`. The dependencies seems to be mentioned in the file `requirements.txt`

If we clone this repository and run the command `python test.py`, we get an error:
```ModuleNotFoundError: No module named 'pandas'```

 ![_config.yml]({{ site.baseurl }}/images/docker_demo_no_pandas_error.png)

This is expected, because we have not installed the library yet. 

### Running the code via docker 
As per the readme file, if we have to run the code via docker, we have to follow the below steps:
1. Install docker. This can be done from [here](https://docs.docker.com/get-docker/)
2. Ensure that the docker daemon runs (If on a mac, double clicking the docker icon would do the job)
3. Clone the [repository](https://github.com/pyari-k/docker-demo) and change the working directory to docker-demo
4. Run the below commands:

``` 
docker build -t demo . 
docker run demo 
```

If we do the above, the code should execute successfully. Irrespective of the version of Python on your machine, the version printed out via the code would be 3.10 (As seen in the picture) 
 ![_config.yml]({{ site.baseurl }}/images/docker_demo_success_docker.png)

### What really happened?
The code did not run on our existing infrastructure as it is. Docker created an isolated container environment for us to run our code. 
The advantages we get because of this are as follows:
* The existing infrastructure on your machine doesn't get tampered with. This would mean that, if you had a Python version of 3.8 on your machine and you were running your own codes with 3.8 version, this particular set up will not affect your other codes. That is because the version of Python on your code remains 3.8 even though the code we tried to run ran on Python 3.10. *The version `3.10` was set only  inside the container. And so are the libraries* 

* If the same repo is passed onto anyone else, they get the same experience as what you got on your machine

### How do you achieve this? - Dockerfile
The [`Dockerfile`](https://github.com/pyari-k/docker-demo/blob/master/Dockerfile) in the repository is what helps us achieve this. 

If we take a look at the contents of the dockerfile, we can see that, it sets up the python version in the docker container. The dockerfile also installs the dependencies from the requirements.txt file. It also runs test.py on Python. 


### If you need some practise
#### Practise Problem 1 
Try running the repository on docker following the instructions in the [readme file](https://github.com/pyari-k/docker-demo/blob/master/readme.md) in the [demo repository](https://github.com/pyari-k/docker-demo)

### Practise problem 2 
* create a new test.py
* Add a line to print out the version of Python in test.py file 
* Add a feature to print out the mean of 5 constant numbers using numpy 
* Run test.py on Python 3.10
* Does it run without docker? If so, how?
* Make it run on docker
* Try asking your friend to run test.py with the dockerfile you created. Does it run?

### Solution for the practise problem 1 
* This solution can be seen the videos. ([Video - English](https://youtu.be/CHP97oqRNgs) or [Video - Malayalam](https://www.youtube.com/watch?v=Q6FfAOKGTzg))

### Solution for the practise problem 2
1. Create test.py, requirements.txt and dockerfile as below & dump them into a folder, say "docker-learn":
2. Navigate to the folder docker-learn
3. Install docker 
4. Ensure that the docker daemon is running (double clicking the docker icon would do if you are on a mac)
5. Run the below commands & check the version of Python printed out. It has to be 3.10
``` 
docker build -t demo . 
docker run demo 
```
`test.py` 
```
import sys
import numpy as np
print(sys.version)
a = 1
b = 2
c = 3
d = 4
e = 5
avg = np.average([a, b, c , d, e])
print("average of {}, {}, {}, {}, {} = {}".format(a, b, c, d, e, avg))
```

`requirements.txt`
```
numpy==1.23.5 
```

`dockerfile`
```
FROM python:3.10-slim
copy requirements.txt requirements.txt
copy *.py .
run pip install -r requirements.txt
cmd ["python", "test.py"]
```

### Tips for practise:
* Try out the practise problems to get a firm grip on the concept. 
* Go through the video/blog multiple times until you finish both the practise problems. 

### Thank you! 
Thanks to all the organisers and speakers of the current cohort of WDA & to my patient mentor [Usha Rengaraju](https://www.linkedin.com/in/usha-rengaraju-b570b7a2/) for all the guidance and tips shared while working on the various course works. 
Thanks to Ian, my manager for helping me transition to new technologies with ease. 
Thanks to [Brian Holt](https://www.linkedin.com/in/btholt/) and his course on front end masters. It is from that course that I learnt Docker. 
And, last but not the least, thanks to [Muneer Marath](https://www.linkedin.com/in/muneermarath/), my perfectionist designer friend who has always taken time and given detailed inputs that keep helping me improve the quality of my works. 
