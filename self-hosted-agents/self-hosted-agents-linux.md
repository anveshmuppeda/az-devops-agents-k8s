

## Add an agent to agent pool  
### Step 1 - Create the Agent 
```mkdir myagent && cd myagent```  

### Step 2 - Download the agent  
```wget https://vstsagentpackage.azureedge.net/agent/2.214.1/vsts-agent-linux-x64-2.214.1.tar.gz  ```

### Step 3 - Configure the Agent   

```tar zxvf vsts-agent-linux-x64-2.214.1.tar.gz  ```   

List the files in the directory after extracting.  
```ls -al```  

### Step 4:  
Run the below command:  
```./config.sh```

### Step 5:  
Enter server URL >  
```https://dev.azure.com/yourorganization```  

### Step 6:  
Enter authentication type (press enter for PAT) > PAT  

### Step 7:  
Enter personal access token, generated from this step  

### Step 8:  
Enter Agent pool  
Give some name  

### Step 9:  
Enter Agent name --> myBuildAgent_1  

### Step 10:  
Enter work folder > enter  

that's it agent is successfully configured.  

## Configure the Agent to run as a Service  

```sudo ./svc.sh install &```  

### Execute now to run as a service  
```./runsvc.sh &```  


## Steps for removing Agent from the agent pool  
Remove the service first  
```sudo ./svc.sh uninstall```  

```./config.sh remove```

## To Perform Java related builds on this Agent, make sure you install Java and Maven on this VM.  

Install Java 11  
```sudo apt-get install default-jdk -y```

## Maven Installation   
Maven is a popular build tool used for building Java applications. Please click here to learn more about Maven. You can install Maven by executing below command:    

```sudo apt update && sudo apt install maven -y```

Check if Maven got installed  

```mvn --version```

