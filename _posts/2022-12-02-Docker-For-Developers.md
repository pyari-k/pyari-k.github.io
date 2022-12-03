---
layout: post
title: Docker for Developers (In Progress)
---

This blog is meant to be a supplementary reading material for the below youtube videos on Dockers
* [Video 1](http://)
* [Video 2](http://)

### "It works on my machine problem!"
Have you encountered the notorious "it works on my machine" problem?
If you are a develper, I am sure you have! 
What is this problem? 
We write a code and test it on our machine. When everything works fine, we move the code to a fellow developer or someone from the testing team only to find that it doesn't work on their machine! 
Does this sound familiar?

### Variables in shipping
Why does this happen? What changes when we move the code to another team member?
Usually the variables are limited. Some of them are:
* the operating system in which both of us work
* the difference in the version of the software in which the code is being compiled
* dependencies/libraries and their versios 

### Solving the problem
We all take different approaches in solving a problem like this. The solution would mostly depend on the technology in which we are working. For eg, if we are working on Python, a read me file with the right version of Python, a properly udpated requirements.txt file and a virtual environment would solve the problem.

However, in this blog, we are trying to solve this problem with Docker. This solution can be extended to work on any language in which you are opting to code. 

### Demo Code 
Let us try to run [this code](https://github.com/pyari-k/docker-demo) on Python

As per the [readme file](https://github.com/pyari-k/docker-demo#readme), it can be seen that we are trying to run the file `test.py` on Python. The Python version to be used is `3.10`. The dependencies seems to be mentioned in the file `requirements.txt`

If we clone this repository and run the command `python test.py`, we get an error:
```ModuleNotFoundError: No module named 'pandas'```

 ![_config.yml]({{ site.baseurl }}/images/docker_demo_no_pandas_error.png)

This is expected, because we have not installed the library yet. 

### Running the code via docker 
As per the readme, if we have to run the code via docker, we have to follow the below steps:
1. Install docker. This can be done from [here](https://docs.docker.com/get-docker/)
2. Ensure that the docker daemon runs (If on a mac, double clicking the docker icon would do the job)
3. Clone the repository and change the working directory to docker-demo
4. Run the below commands:
   ``` docker build -t demo . 
    docker run demo ```

If we do the above, the code should succesfully run. Irrespective of the version of Python on your machine, the Python version printed out would be 3.10 (As seen in the picture) 
 ![_config.yml]({{ site.baseurl }}/images/docker_demo_success_docker.png)

### What happened?
Docker created an isolated container environment for us to run our code. 
The advantages we get because of this are as follows:
* The existing infrastrucure on your machine doesn't get tampered with. This would mean that, if you had a Python version of 3.8 on your machine and you were running your own codes with 3.8 version, this particular set up will not affect your other codes. That is because the version of Python on your code remains 3.8

* If the same repo is passed onto anyone else, they get the same experience as what you got on your machine

### How do you achieve this? - Dockerfile
The [`Dockerfile`](https://github.com/pyari-k/docker-demo/blob/master/Dockerfile) in the repository is what helps us achieve all this. 

If we take a look at the contents of the dockerfile, we can see that, it sets up the python version in the docker container. Install the dependencies from the requirements.txt file. It also runs test.py in Python. 


### If you need some practise
#### Practise Problem 1 
Try running the repository on docker following the instructions in the [readme file](https://github.com/pyari-k/docker-demo/blob/master/readme.md) in the [demo repository](https://github.com/pyari-k/docker-demo)

### Practise problem 2 
* create a new test.py. Run it on Python 3.10
* Print out the version of Python in test.py file 
* Print out the mean of 5 numbers using numpy 
* Does it run without docker? If so, how?
* Make it run on docker
* Try asking your friend to run test.py - with and without Python. Does it run?



