# sawtooth-simplewallet
A wallet application built on top of `hyperledger-sawtooth`   
This application has two componenets.  
1. Transaction Processor (Implemented in Java)
2. Client Application (Implemented in Python) (Currently sawtooth does not provide client sdk for Java)

# Pre-requisites
This example uses docker-compose and Docker containers. If you do not have these installed please follow the instructions here: https://docs.docker.com/install/

# How to Run
1. Initiating Transaction Processor

   `docker-compose -f simplewallet-build-tp-java.yaml up --build` (It might minutes to get all set in the container. Took 5-10 min on my machine)

2. Initiating client  
   In a a separate terminal window, run  `docker exec -it simplewallet-client bash` and after logging in into the container, execute the following to to simulate the wallet:  
   ```bash
    sawtooth keygen jack #This creates the public/private keys for Jack, a pre-requisite for the following commands
    
    simplewallet deposit 100 jack #This adds 100 units to Jack's account
    
    simplewallet withdraw 50 jack #Withdraws 50 units from Jack's account
    
    simplewallet balance jack #Displays the balance left in Jack's account
    
    sawtooth keygen jill #This creates the public/private keys for Jill, a pre-requisite for the following commands
    
    simplewallet deposit 100 jill #This adds 100 units to Jill's account
    
    simplewallet balance jill #Displays the balance left in Jill's account
    
    simplewallet transfer 25 jack jill #Transfer 25 units money from Jack to Jill
    
    simplewallet balance jack #Displays the balance left in Jack's account
    
    simplewallet balance jill #Displays the balance left in Jill's account
```
