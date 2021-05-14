# production_environment_ML

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
 
