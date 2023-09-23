# Deployment 3.1 Documentation

## Incident Report:
To see the incident report regarding an issue we had with our application on Sep 20, please click [here!](https://github.com/auzhangLABS/deployment3.1/blob/main/incident_report.md).

## Purpose:
Deployment 3.1 is a continuation of Deployment 3. To see Deployment 3, please click [here](https://github.com/auzhangLABS/c4_deployment3). This deployment 3.1 file serves as a documentation report for deployment 3.1.  Upon investigating, we had a recent update to our application by a new hire resulting in a 500 Internal Server Error whenever the application was used. Here are our methods of resolving this issue:

## Method 1: Looking into Git commit.
My first method was to look into git commits and investigate the changes within the code. Upon investigating, I noticed that there was an error with the application.py file that caused the error. Once, I fix that Jenkins will automatically rerun, build, test, and deploy (using Webhooks), and the application will work. Given that this would take up too much time, I present another solution using rollback (Method 2).

## Method 2: Using Rollback to the previous application.py (version 1).
This method would allow you to roll back to the Version 1 application.py file without changing any other files within the repository. This allows you to keep your original templates. To do this, I had to revert the code within the application.py code that would throw the error. Once I did this, I would validate this by trying to rerun the application and got a 500 error. 
1. Get the most recent changes in the Github repository
   - `git pull`
   - You can verify this by using:
      - `git log --oneliner` or `git log --pretty=oneline` to show full commit id
   ![1](https://github.com/auzhangLABS/deployment3.1/assets/138344000/67ea5a3e-2259-41fd-ba3d-c06bbff13ade)

   - Here is a snippet of the results I got: image
   - Here, I was able to tell what the commit ID was Version 1 and Version 2
     
2. Get to the previous version of application.py
   - `git checkout <commit id>` to check out the files in version 1
   - `git status` to see what files are different than the current version.
   - `git commit application.py -m "reverting back to version 1 of appliation.py" ` to commit the only python file
     ![m1 1](https://github.com/auzhangLABS/deployment3.1/assets/138344000/4822880d-ad6d-4771-8378-34f9539a24f7)

   - `git push` pushing the changes into the repository 

This method only changes the application.py file to the older version. This would allow it to solve the issue we were encountering. Method 3 will show you how to roll back to version 1 entire files.

## Method 3: Using Rollback to the previous version
1. We would follow Method 2 Step 1 to get the commit ID for version 1 and version 2.
2. Get to the previous version.
   - `git checkout <commit id>` to check out the files in version 1
   - `git commit -m "reverting back to version 1" ` to commit back to version 1.
   - `git push` pushing the changes into the remote repository 

Keep in mind, with this method we also had to edit the Jenkins file and the test_app.py (see below)

## System Design Diagram:
To view the system design diagram for methods 1-3, click [here!](https://github.com/auzhangLABS/deployment3.1/blob/main/System%20Diagram.png)


## Issues/ Troubleshooting:
The main issue I encountered was with Method 3. After reverting back to version 1, I got an issue within the Jenkins test and deploy stage. Upon investigating, I figured out that the test_app.py file had an error. Additionally, we also had to add a deploy stage to Jenkins: `stage ('Deploy') { steps { sh '/var/lib/jenkins/.local/bin/eb deploy' } }`
![image](https://github.com/auzhangLABS/deployment3.1/assets/138344000/d109d087-efb6-4911-9973-67511da5040e)

## Optimization:
I would try to optimize this process by ensuring that version 1 worked. In this example (method 3), we would roll back to version 1 and I would not work. I would look for a way to verify that the previous version works before rolling back to it.

