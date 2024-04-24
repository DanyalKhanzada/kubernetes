# kubernetes

1. Create MongoDB Deployment
2. Create Secrets file - mongo.yaml
    - Created username and password via cli base64 
        - command: echo -n 'username' | base64 and echo -n 'password' | base64
        - kubectl apply -f mongo-secret.yaml 

        - name: MONGO_INITDB_ROOT_USERNAME
          valueFrom: 
            secretKeyRef: (Link between mongo.yaml and Mongo-secret to execute)
              name: mongodb-secret
              key: mongo-root-username
        - name: MONGO_INITDB_ROOT_PASSWORD
          valueFrom: 
            secretKeyRef:    (Link between mongo.yaml and Mongo-secret to execute)
              name: mongodb-secret
              key: mongo-root-password
        
3. Create MongoDB Internal service
    - Other pods can speak to each other

4. Create Mongo Express , Mongo Express External Service and also ConfigMap - DB Url
    - Create mongo-express.yaml file
    - We need to tell mongo express to:
        - Which database to connect?
            - MongoDB Address / Internal Service
        - Which Credentials to authenticate
            - ADMINUSERNAME
            - ADMINPASSWORD




    Commands:
    1. Kubectl apply -f [File name]
    2. To see if the service is attached to correct pod
     - Kubectl describe service [filename]
    3. kubectl get pod -o wide
    4. 