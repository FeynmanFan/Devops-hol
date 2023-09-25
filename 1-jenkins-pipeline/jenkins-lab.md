# 1. Jenkins Lab

You're working for Cyberdyne Systems, and you have a build you need to set up for the new production model, the T-800.
The repo for the build is located here: 

https://github.com/FeynmanFan/cyberdyne

This repo is public and will not require credentials - thank Cyberdyne for their commitment to open source.

## Fork this repo and use the url for the rest of the lab.

## Lab Steps
1. Clone the repo to your local machine with this command:
git clone {url to your forked repo}

2. This project is written in C# using DotNet Core. Ensure that the Dotnet Core SDK is installed on your local machine using the instructions found here:

https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu-2204

https://learn.microsoft.com/en-us/dotnet/core/install/windows?tabs=net70

3. Compile the project using the following command **executed in the directory where the .sln file resides** on your local machine:
dotnet build

4. If you do not have a local Jenkins instance, create one with Docker using the following command:

`docker run -p 8080:8080 jenkins/jenkins:latest`

### Notes: 
This command is *not* creating a volume - if you would prefer to work with a volume and are familiar with the syntax, feel free to mount a volume.

This command is assuming that port 8080 is free on your machine - if another application is already using it, you can adjust the port by changing the *first* number in the sequence, e.g., 8081:8080

5. Once your Jenkins instance is up and running, create a new pipeline build called `cyberdyne-t-800`.

6. Complete the following using an inline pipeline script: using the syntax helper, the reference material in the course, and whatever other resources you would like, create a Jenkinsfile with two stages: *scm*, where the code is pulled from the repo, and *compile*, where the code is compiled using the `dotnet build` command as a shell script. 

7. Take this Jenkinsfile and commit it to the root of your forked Cyberdyne directory. Modify the build to pull this Jenkinsfile from the repo.

8. Execute the build and verify that it succeeds.

9. Paste the url of your forked repo into the **DevOps Hands-on Lab** Discord channel for review.

The *asset* mentioned in the base lab instructions for this lab is the Jenkinsfile you've created, and this is what will be evaluated.