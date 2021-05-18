# Production_environment_ML

- The end point is like a function call
- The funciont itself would be the model
- python program is the application

# How does it look like?

**Production environment:** Where the user is going to get the service (i.e. prediction) 

app.py -> 

def main():
          
          input_user_data = get_user_data()

**End point:** The interface to the model. It aim´s to communicate the model with the application.

- Allows the application to send user data to the model

- Receives predictions back from the model based upon that user

          predictions = ml_model(input_user_data)
          
          display_predictions_to_user(predictions)


**Model**

def ml_model(user_data):
     
     loaded_data = load_user_data(user_data)
     
This example highlights how the endpoint itself is just the interface between the model and the application; where this interface enables users to get predictions from the deployed model based on their user data.

Next we'll focus on how the endpoint (interface) facilitates communication between application and model.

The endpoint is considered the Application Programming Interface (API). A set of rules that enable programs, here the application and the model, to communicate with each other.
In this case, our API uses a REpresentational State Transfer, REST, architecture that provides a framework for the set of rules and constraints that must be adhered to communication between programs.
This rest API is one that uses HTTP requests and responses to enable communication between the application and the model through the endpoint (interface).

The HTTP request that's sent from the application to our model is composed of four parts: 

- End point, often this is a Uniform Resource Locator (URL)

- HTTP method, generally using the POST method only in deployment ML (we are going to create new information)

- HTTP headers, additional information, like the format of the data within the message, that's passed to the receiving program.

- Message (Data or Body) The final part is the message (data or body); for deployment will contain the user's data which is input into the model.

- The HTTP response sent from your model to your application is composed of three parts: 

  -- HTTP status code: If the model successfully received and processed the user's data that was sent in the message, the status code should start with a 2, like 200.
  
  -- HTTP headers: Additional information, like the format of the data within the message, that's passed to the receiving program.
  
  -- Message (Data or Body): What's returned is the prediction that's provided by the model.
  
 The prediction is then presented to the application user through the application. The endpoint is the interface that enables communication between the application and the model, using a REST API.
 
Model, Application and Containers

Production environment is composed of two primary programs, the model and the application, that communicate each other through the endpoint (interface).

Model, Application, and Containers
When we discussed the production environment, it was composed of two primary programs, the model and the application, that communicate with each other through the endpoint (interface).

The model is simply the Python model that's created, trained, and evaluated in the Modeling component of the machine learning workflow.
The application is simply a web or software application that enables the application users to use the model to retrieve predictions.
Both the model and the application require a computing environment so that they can be run and available for use. One way to create and maintain these computing environments is through the use of containers.

Specifically, the model and the application can each be run in a container computing environment. The containers are created using a script that contains instructions on which software packages, libraries, and other computing attributes are needed in order to run a software application, in our case either the model or the application.
Containers Defined
A container can be thought of as a standardized collection/bundle of software that is to be used for the specific purpose of running an application.
As stated above container technology is used to create the model and application computational environments associated with deployment in machine learning. A common container software is Docker. Due to its popularity sometimes Docker is used synonymously with containers.

Containers Explained
Often to first explain the concept of containers, people tend to use the analogy of how Docker containers are similar to shipping containers.

Shipping containers can contain a wide variety of products, from food to computers to cars.
The structure of a shipping container provides the ability for it to hold different types of products while making it easy to track, load, unload, and transport products worldwide within a shipping container.
Similarly Docker containers:

Can contain all types of different software.
The structure of a Docker container enables the container to be created, saved, used, and deleted through a set of common tools.
The common tool set works with any container regardless of the software the container contains.
Container Structure
The image below shows the basic structure of a container, you have:

The underlying computational infrastructure which can be: a cloud provider’s data center, an on-premise data center, or even someone’s local computer.
Next, you have an operating system running on this computational infrastructure, this could be the operating system on your local computer.
Next, there’s the container engine, this could be Docker software running on your local computer. The container engine software enables one to create, save, use, and delete containers; for our example, it could be Docker running on a local computer.
The final two layers make up the composition of the containers.
The first layer of the container is the libraries and binaries required to launch, run, and maintain the next layer, the application layer.
The image below shows three containers running three different applications.
This architecture of containers provides the following advantages:

Isolates the application, which increases security.
 
Requires only software needed to run the application, which uses computational resources more efficiently and allows for faster application deployment.
 
Makes application creation, replication, deletion, and maintenance easier and the same across all applications that are deployed using containers.
 
Provides a more simple and secure way to replicate, save, and share containers.

As indicated by the fourth advantage of using containers, a container script file is used to create a container.

This text script file can easily be shared with others and provides a simple method to replicate a particular container.
This container script is simply the instructions (algorithm) that is used to create a container; for Docker these container scripts are referred to as dockerfiles.
This is shown with the image below, where the container engine uses a container script to create a container for an application to run within. These container script files can be stored in repositories, which provide a simple means to share and replicate containers. For Docker, the Docker Hub is the official repository for storing and sharing dockerfiles. Here's an example of a dockerfile that creates a docker container with Python 3.6 and PyTorch installed.


Characteristics of Deployment and Modeling
Recall that:
Deployment to production can simply be thought of as a method that integrates a machine learning model into an existing production environment so that the model can be used to make decisions or predictions based upon data input into this model.

Also remember that a production environment can be thought of as a web, mobile, or other software application that is currently being used by many people and must respond quickly to those users’ requests.

Keeping these things in mind, there are a number of characteristics of deployment and modeling that I’m going to introduce here. These concepts are introduced now to provide you with familiarity with these concepts for when you see them discussed in future lessons. Specifically, these concepts are provided as features that are made easier to use within cloud platforms services than if implemented with your own code.


Characteristics of Modeling
Hyperparameters
In machine learning, a hyperparameter is a parameter whose value cannot be estimated from the data.

Specifically, a hyperparameter is not directly learned through the estimators; therefore, their value must be set by the model developer.
This means that hyperparameter tuning for optimization is an important part of model training.
Often cloud platform machine learning services provide methods that allow for automatic hyperparameter tuning for use with model training.
If the machine learning platform fails to offer an automatic hyperparameter option, one option is to use methods from scikit-learn Python library for hyperparameter tuning. Scikit-learn is a free machine learning Python library that includes methods that help with hyperparameter tuning.


Characteristics of Deployment
Model Versioning
One characteristic of deployment is the version of the model that is to be deployed.

Besides saving the model version as a part of a model’s metadata in a database, the deployment platform should allow one to indicate a deployed model’s version.
This will make it easier to maintain, monitor, and update the deployed model.

Model Monitoring
Another characteristic of deployment is the ability to easily monitor your deployed models.

Once a model is deployed you will want to make certain it continues to meet its performance metrics; otherwise, the application may need to be updated with a better performing model.
Model Updating and Routing
The ability to easily update your deployed model is another characteristic of deployment.

If a deployed model is failing to meet its performance metrics, it's likely you will need to update this model.
If there's been a fundamental change in the data that’s being input into the model for predictions; you'll want to collect this input data to be used to update the model.

The deployment platform should support routing differing proportions of user requests to the deployed models; to allow comparison of performance between the deployed model variants.
Routing in this way allows for a test of a model performance as compared to other model variants.

Model Predictions
Another characteristic of deployment is the type of predictions provided by your deployed model. There are two common types of predictions:

On-demand predictions
Batch predictions
On-Demand Predictions
On-demand predictions might also be called:
online,
real-time, or
synchronous predictions
With these type of predictions, one expects:
a low latency of response to each prediction request,
but allows for possibility high variability in request volume.
Predictions are returned in the response from the request. Often these requests and responses are done through an API using JSON or XML formatted strings.
Each prediction request from the user can contain one or many requests for predictions. Noting that many is limited based upon the size of the data sent as the request. Common cloud platforms on-demand prediction request size limits can range from 1.5(ML Engine) to 5 Megabytes (SageMaker).
On-demand predictions are commonly used to provide customers, users, or employees with real-time, online responses based upon a deployed model. Thinking back on our magic eight ball web application example, users of our web application would be making on-demand prediction requests.

Batch Predictions
Batch predictions might also be called:
asynchronous, or
batch-based predictions.
With these type of predictions, one expects:
high volume of requests with more periodic submissions
so latency won’t be an issue.
Each batch request will point to specifically formatted data file of requests and will return the predictions to a file. Cloud services require these files will be stored in the cloud provider’s cloud.
Cloud services typically have limits to how much data they can process with each batch request based upon limits they impose on the size of file you can store in their cloud storage service. For example, Amazon’s SageMaker limits batch predictions requests to the size limit they enforce on an object in their S3 storage service.
Batch predictions are commonly used to help make business decisions. For example, imagine a business uses a complex model to predict customer satisfaction across a number of their products and they need these estimates for a weekly report. This would require processing customer data through a batch prediction request on a weekly basis.
