Hit a wall trying to run PM2 within Jenkins on a Windows machine 😅 After testing PM2, Forever, NSSM, and Task Scheduler, it’s clear that Windows isn’t PM2’s playground. Sharing this to help anyone facing the same CI/CD challenge 💡


Hello Developers,

During my recent CI/CD pipeline implementation using Jenkins on a Windows environment, I attempted to integrate **PM2** as a background process manager for a Node.js application. Despite successfully installing PM2 and validating it via CLI, I encountered issues running it persistently within the Jenkins pipeline.

The process did not behave as expected — PM2 failed to run in the background through Jenkins, and the functionality was no different than invoking `node app.js` directly. Extensive troubleshooting, including using `npx`, global installs, and different execution flags (`--no-daemon`, etc.), did not resolve the issue.

I also explored potential Jenkins plugins for PM2 integration but confirmed that no native or community-supported plugins are currently available.

As a result, I evaluated alternative Node.js process managers that support Windows environments:

- **Forever** – lightweight but lacks advanced features like monitoring and clustering.
- **NSSM (Non-Sucking Service Manager)** – effective for converting scripts to Windows services, though limited in logs and ecosystem integration.
- **Windows Task Scheduler** – native but lacks real-time monitoring and isn't CI/CD friendly.

Unfortunately, none of the alternatives offer the robustness and features of PM2, particularly in CI/CD pipelines running on Windows.

I’m sharing this update for awareness and future reference. If there’s a more effective service/process manager that supports background execution for Node.js apps within Jenkins on Windows, I’m open to exploring it and sharing further findings.

Here is a snapshot of it 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lh5wvxpol3b8px6fgd1l.png)



Thanks,  
**Horla (Jahmeeu-Cloud)**  
Cloud & DevOps Engineer  

#DevOps #CloudEngineering #CICD #Jenkins #NodeJS #Automation #ProcessManager #PM2 #WindowsDevOps #BuildInPublic #TechCommunity
