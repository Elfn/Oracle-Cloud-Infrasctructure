#Picture1  
* As you can see here, the two key aspects-- you detect a problem.   

* And there are a couple of ways you do that.   

* You can check configurations, you can monitor activities, and then you can apply a response. And you can automate this response.  

#Picture2  
###1-Target  
* So the first thing you do is, you specify a target.  

* And a target basically sets the scope of resources to be examined for OCI Compartments can be targeted, and their child compartment can be the target.  

* So target is nothing but resources to be examined.  

###2-Detectors  
* Detectors are Cloud Guard components that identify issues with resources or user actions and alert when an issue is found. 

* So, as you can see here, if there is a public instance where it should not be, it will flag that. 

* If there's a public bucket, it would flag that, et cetera.  

###3-Responders    
* provide notification and corrective actions for security problems.  
* So, as you can see here, if the instances public, you could stop that instance.   
* If a bucket is public, you could disable that bucket or make it private and so on and so forth.   
* You could decide what kind of responders you want.  

#Picture3  
* Now, let us look at this in action. So the scenario here is a public bucket, and you don't want this bucket to be public. You want this to be a private bucket because that aligns with your security posture. So, first, what Cloud Guard does, suppose this bucket is living in a compartment, which is monitored by Cloud Guard.  

* Cloud Guard is running this configuration monitoring. So it's looking at your bucket, and it triggers a flag saying that this particular bucket is public. And it flags that as a critical issue, and a problem gets created. So think of our problem as sort of a ticket. So it gets created saying, bucket is public. And, at the same time, because it assigns a security score, it says it's a critical risk. So it notifies that-- that it's a critical risk.  

* And, then, there are responders, which look at that. And they say, is my responder enabled on for this kind of issue? And if the answer is yes, it can also have additional functionality-- so things like Cloud Event. It could go to Cloud Event, trigger that as an event, and then you could get notifications out of that.  

You could also go to OCI functions, which is our serverless service, and it could do something else. It could slack you or something like that. So it could have some other feature built in. So the responder looks at that, and then it hands it over to a Cloud Guard operator. This is a policy which you write, which says, can I remediate the problem?

Do I have the permission to remediate the problem because one interesting thing about Cloud Guard is, you could automate all this. And if the answer is yes, then it responds. And it makes the bucket private. And that's how you go to that critical risk on, and the situation turns to green again.