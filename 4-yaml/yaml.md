
```yml
# simple key value pairs
name: angel
age: 24
city: Puebla
```

## Dictionary / Map
- 2 spaces bar
```yml
person:
  name: angel
  age: 24
  city: Puebla
```

## Array / Lists
- Dash indicates an element of an array
```yml
person: # Dictionary
  name: angel
  age: 24
  city: Puebla
  hobbies: # List  
    - learning
    - reading
  hobbies: [learning, reading]   # List with a differnt notation  
```  

## Step-04: Multiple Lists
- Dash indicates an element of an array
```yml
person: # Dictionary
  name: angel
  age: 24
  city: Puebla
  hobbies: # List  
    - learning
    - reading
  hobbies: [learning, reading]   # List with a different notation  
  friends: # Multiple Lists
    - name: friend1
      age: 25
    - name: friend2
      age: 24
  friends: [friend1, 25 [friend2, 24]]        
```  


## Step-05: Sample Pod Template for Reference
```yml
apiVersion: v1 # String
kind: Pod  # String
metadata: # Dictionary
  name: myapp-pod
  labels: # Dictionary 
    app: myapp         
spec:
  containers: # List
    - name: myapp
      image: us-central1-docker.pkg.dev/laboratorio-oct-devoteam/angelgke/stack-helloworld:1
      ports: # Multiple Lists
        - containerPort: 80
          protocol: "TCP"
        - containerPort: 81
          protocol: "TCP"
```




