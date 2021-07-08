# Containerize-Microservice-with-Amazon-ECS-and-Application-Load-Balancer


To achieve this we will perform following steps:
Step1: Create microservice app [3 separate apps to see the ALB effect]
Step 2: Create Dockerfile(s)
Step3: Create ECR Repository and push images to ECR
Step4: Create ECS cluster
Step5: Create Task Definition & add container information
Step6: Create Service to run the Task definition
Step7: Create Application Load Balancer
Step8: Fix security group settings
Step9: Complete creation of service by providing ALB name
Step10: Verify the running services
Step11: Delete resources (ECS Cluster, Load Balancer)

**Step1: Create microservice app**
index.py
from flask import Flask
app = Flask(__name__)
@app.route("/service-1")
def hello():
    return "Hello World from service-1!"
if __name__ == "__main__":
    app.run(host="0.0.0.0", port=int("5001"), debug=True)
    
    **Create Dockerfile**
    
    FROM python:alpine3.7
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
EXPOSE 5001
ENTRYPOINT ["python","./index.py"]








