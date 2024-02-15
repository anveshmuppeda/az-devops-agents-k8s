# Add an windows agent to agent pool  


### Create the agent  

```  
PS C:\> mkdir agent ; cd agent
PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win-x64-3.234.0.zip", "$PWD")
```  

### Configure the agentDetailed instructions  

```
PS C:\agent> .\config.cmd  
```

### Optionally run the agent interactively  
If you didn't run as a service above:  

```
PS C:\agent> .\run.cmd 
```



https://vstsagentpackage.azureedge.net/agent/3.234.0/vsts-agent-win-x64-3.234.0.zip


