# demo-app
This CI/CD pipeline automates the following:
1. **Build & Test** the Spring Boot application using Maven.
2. **Containerize & Push** the Docker image to Docker Hub.
3. After CI/CD builds and pushes the Docker image: perform this command 
Start Minikube using minikube start
Apply the Kubernetes manifests using in K8s folder location
kubectl apply -f postgres.yaml
kubectl apply -f deployment.yaml
To get the exposed service URL, run: minikube service demo-api-service --url
Now run the url
http://127.0.0.1:59996 this was given as base url, 

# To create customer
curl --location 'http://127.0.0.1:59996/customers' \
--header 'Content-Type: application/json' \
--data-raw '{
    "firstName": "John",
    "middleName": "Doe",
    "lastName": "Smith",
    "email": "john.smith@example.com",
    "phoneNumber": "1234567890"
}'

# To get customer
http://127.0.0.1:60469/customers

# To delete customer
curl --location --request DELETE 'http://127.0.0.1:60469/customers/ba554fad-daab-43b1-8a34-5960ca8e161f'
# To update customer
curl --location --request PUT 'http://127.0.0.1:60469/customers/79fe36fe-23c1-4f21-ac93-c075a9311aea' \
--header 'Content-Type: application/json' \
--data-raw '{
    "firstName": "Aisha",
    "middleName": "abc",
    "lastName": "Doe",
    "email": "john.doe@example.com",
    "phoneNumber": "9876543210"
}'

# To get customer on the basis of UUID
curl --location 'http://127.0.0.1:60469/customers/72fe36fe-23c1-4f21-ac93-c075a9311aea' \
--header 'Content-Type: application/json'


