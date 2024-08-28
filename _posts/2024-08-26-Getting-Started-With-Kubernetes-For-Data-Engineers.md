---
layout: post
title: Getting Started with Kubernetes - From A Data Engineers' persepctive
---

### Kubernetes - From an absolute beginner's perspective
Let us say you write a code, you don't finally run it on your own machine. The production version of it runs on a server. These days, it usually runs on a cloud service provider & in a containarised form. Managing/orchestrating these standalone apps on cloud is a difficult task and that is where Kubernetes comes into picture. Some of the advantages of using Kubernetes is as below:
1. Kubernetes helps scale the applications in case of heavier loads. That way, when the load is low, Kubernetes helps to scale down as well. 
2. If an application crashes, Kubernetes can help bring it up again. In other words, with the help of Kubernetes, the app attains a self healing property. 
3. It helps maintain the applications with minimal downtime. 

This might not be a sophisticated or an exact definition. I just tried to make it as simple as possible. [Kubernetes' offical page](https://kubernetes.io/docs/concepts/overview/) has a very clear definition of what Kubernetes is.


### About the post
Most of the Kubernetes demos, tutorials and books we usually come across have web based applications used for demonstrations. 
Data Engineers have a slightly diffrent requirement and here, a case of a scheduled standalone python application is being demonstrated. 
This post is intended to simulate a case of scheduling an ETL python code on Kubernetes. 

The blog was previously posted on [medium](https://pyari-kumaran.medium.com/learning-kubernetes-simulating-a-scheduled-etl-project-using-minikube-c5ab2ee5ba86). From the feedback I got so far, I was asked to elaborate on what Kubernetes is. So, tne initial section to explain what Kubernetes is added. 

### What to expect and what not to expect from this post
I believe that whatever subject or technology you are learning, getting started is one of the biggest hurdles. Once you get started & get comfortable with the basics & the environment, then, exploring it further is not a difficult task. Most of my blogs are hence written that way - so that it eases one into the subject in hand. In this blog as well, I am handling Kubernetes that way. It doesn't go indepth with Kubernetes. But, it will help you get started if you never knew where & how to get started, if at all you were to start from the scratch. 

### References
There is much more to learn on Kubernetes. Linked below are two resources which are helping me with my learnings. 

(a) [Handson Quickstart Kubernetes by Nigel Poulton](https://www.amazon.de/-/en/Nigel-Poulton/dp/B09QFM8FWJ)

![_config.yml]({{ site.baseurl }}/images/quick_start_kube.jpeg)

(b) [Techworld with Nana - Youtube channel](https://www.youtube.com/c/techworldwithnana)


### Minikube 
Learning any cloud based tool has become a challenging affair because of the cost associated with it. Here, we will be using Minikube to do our first handson project. Minikube is a simplified version of Kubernetes, which can be used for local development and testing. Hence, we use minikube for our project. 

### Prerequisites:
1. We need to have docker intsalled. Docker can be installed from [here](https://docs.docker.com/engine/install/). After installation, ensure that the docker demon is running. If you are a beginner or need a refresher on docker, [my earlier blog on docker](https://pyari-kumaran.medium.com/docker-for-developers-598c231cd140) should give an idea.

2. A dockerised python code performing an etl. A simple code which reads a csv file is already written on a repo [here](https://github.com/pyari-k/docker-demo) on my github. You may also use your own repo. The below git clone command should download the code on my repo in case you want to start from there.

`git clone git@github.com:pyari-k/docker-demo.git`

3. Minikube needs to be installed on our machines. The below command should do the job.

`brew install minikube` 

4. Let us test whether our prerequisites are met. Do the below:

```
#change directory to docker-demo
docker build -t demo . #this is just a test. the command should build the docker image succesfully. 
# we will not be using the above docker image 
docker run demo
```
The above should run our dockerised python code and give an output like the below. It should show the no: of records read from the csv, the result of pinging google.com and also the time of running the code.

![_config.yml]({{ site.baseurl }}/images/docker_run.png)

Let us now start using minikube. We will run the below 3 commands to start minikube and to set docker environment to point to minikube’s docker demon. We can also build the docker image there.

```
minikube start #this will start minikube if it is not already running

# Set Docker environment to point to Minikube's Docker daemon
eval $(minikube docker-env)

# Build the Docker image
docker build -t etl-image .
```

To run the containarised application, you now need to create a Kubernetes Deployment. A sample `deployment.yaml` file is attached below. This would create a deployment by name `etl-deployment`. You may note that the deployment points to the docker image we created above — `etl-image`.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: etl-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: etl
  template:
    metadata:
      labels:
        app: etl
    spec:
      containers:
      - name: etl-container
        image: etl-image:latest
        imagePullPolicy: IfNotPresent
        resources:
          limits:
            memory: "128Mi"
            cpu: "500m"
```

To apply/create the deployment, the below kubectl command may be used:

`kubectl apply -f deployment.yaml `

To ensure that everything has gone smooth, you may use the below commands to check the logs
```
kubectl get pods
kubectl logs <pod_name> #eg: kubectl logs etl-deployment-66ff4ffc5d-rsk5k
```

The above should show the logs of the program. This time, the program runs on the new deployment.

![_config.yml]({{ site.baseurl }}/images/docker_run.png)


### ETL/Data Engineering specific requirements

Now, this is where we need to have etl specific changes. The above is what usual demos and tutorials on k8s demonstrating the deployment of web based applications show us. Is the above enough for ETLs? ETLs are usually scheduled to hit the data sources in a timely manner & re run at regular intervals. So, a regular deployment will not serve our purpose.

This means, we can go ahead and safely delete our deployment. The below command can be used

```
kubectl delete deployment etl-deployment

#the below kubectl command should help to get the name of the deployment
kubectl get deployments 
```

What we need instead is a *Kubernetes Cronjob*.

Let us hence create a Kubernetes Cronjob. The below `cronjob.yaml` may be used to create one. This creates a cronjob which runs every minute.

```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: etl-cronjob
spec:
  schedule: "* * * * *" 
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: etl-container
            image: etl-image:latest
            imagePullPolicy: Never 
          restartPolicy: OnFailure
```
To create the cronjob, you can use the same kubectl apply command, this time with the cronjob file instead.

`kubectl apply -f cronjob.yaml`

To ensure that the jobs have triggered correctly, you can check the logs once again and you should be able to view the new run times in the logs corresponding to every run.

As a reminder, to view the logs of the scheduled runs, like in the case of deployments, you may use the below:

```
kubectl get pods
kubectl logs <pod_name>
```

In case, you need a manual run of the cron job in between, the below command can be used:
`kubectl create job --from=cronjob/etl-cronjob etl-manual-job`

### Clean up:

To remove the cronjob, the below kubectl command can be used

#kubectl delete cronjob <cronjob_name>
kubectl delete cronjob etl-cronjob 

As always, happy coding and I am only a message away if you have any questions or comments!
