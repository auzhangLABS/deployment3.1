# Deployment 3.1 Documentation
## Purpose:
Deployment 3.1 is a continuation of Deployment 3. To see Deployment 3, please click [here](https://github.com/auzhangLABS/c4_deployment3). This deployment 3.1 file serves as an incident report regarding an issue we had with our application on Sep 20. Upon investigating, we had a recent update to our application by a new hire resulting in a 500 Internal Server Error whenever the application was used. Here are our methods of resolving this issue:

## Method 1: Looking into Git commit.
My first method was to look into git commits and investigate the changes within the code. Upon investigating, I noticed that there was an error with the application.py file that caused the error. Once, I fix that Jenkins will automatically rerun, build, test, and deploy (using Webhooks), and the application will work. Given that this would take up too much time, I present another solution using rollback (Method 2).

## Method 2: Using Rollback.
Once, we encounter the error we would roll back to the previous version and then diagnose the problem. To do this, I had to revert the code within the application.py code that would throw the error. Once I did this, I would validate this by trying to rerun the application and got a 500 error. 
1. Get the most recent changes in the Github repository
   - `git pull`
   - You can verify this by using:
      - `git log --oneliner` or `git log --pretty=oneline` to show full commit id
   - Here is a snippet of the results I got:
![image](https://github.com/auzhangLABS/deployment3.1/assets/138344000/e8c5d626-b127-476a-89b3-a41b19677bba)
   - Here, I was able to tell what the commit ID was Version 1 and Version 2

2. Rollback to the previous version
