# Demo_Project_AWSDevOps

# Follow these steps involved  to implement simple Aws DevOps Project

![1685822819048](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/8649534b-2c9c-4b98-a606-b6498fb4fb72)


# Lets Start !!!

1.     First of all, to start with AWS DevOps, we need to create a user by using the IAM service with some specific access(Example : Admin or user only set of some rules).
2.     Storage – In this storage part we will store our built code for that we will use Artifacts or S3 buckets.
3.     CodeCommit - CodeCommit is just like GitHub inside AWS. We can perform push, pull, branching on the repositories, and many other operations.
4.     CodeBuild - Now, the pushed code in CodeCommit, should be built and tested (Continuous Integration (CI)). This will happen inside CodeBuild. And the built code will be stored in Storage.

# Step -1 :

 Goto the AWS console and search for “CodeCommit” and click on “Create Repository.” and  Enter the Name and Description then click on Create.

 ![1](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/2195fcaf-9857-408d-a9b0-3c5bec457efa)

The Repository was created successfully. 

# Note : But it is giving an error as “You cannot configure SSH using root account”


# Step -2 

Go to the IAM Serivice and create a user ( for this i'm attaching admin level permissions)
![2](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/a836d41c-c26c-4085-ad6b-94ebb62361ee)

Now, open the created user and search for “HTTPS Git credentials for AWS CodeCommit” and click on “Generate Credentials”.

![3](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/17457b37-d992-47f3-a4d5-09724f5b03d1)

![4](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/3552c4f7-e2f2-47be-b7b8-454f1d00111f)


# Step -3 

Now, we will clone the “demo-app” repository that we have created in CodeCommit.
Click on “Clone URL” then “Clone HTTPS” and it will provide you the URL.
![5](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/f44bce23-dd27-4272-b1b8-d2deb69c6cc9)
![6](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/897ea4ba-3898-493e-b36e-0595a9bffd57)

# Go to terminal(vscode,commandline, powershell) Run, “git clone https://git-codecommit.us-east-1.amazonaws.com/v1/repos/demo-app”
![7](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/13593784-9815-446d-94a3-1a6f548cb79f)
![7](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/9f7625d0-fbf4-4b05-8559-f9764819f520)


For the First time it will give a popup of git credentials Manager
![9](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/ca496a6f-9a81-4750-8bf8-2ce22ba74a9f)

Provide Cred's which you have downloaded
![10](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/fbe91692-5479-4574-9e84-a962e92f2400)

In Terminal you can see that the repo is empty !!
![11](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/d3efd841-c298-4c3f-9f4f-bea3a1e2e384)

go inside the demo-app/ and perform git actions
# git add .
# git commit -m "demo-AWS_DevOps"
# git push

check the code commit repo, you will find the index.html over there
![13](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/b9a37102-4b0b-4362-a8ed-328e9388900e)


# Step-4 Code Build !!
![14](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/2f14a4ac-8bfa-48e9-b65b-d1102291bec5)

Goto the Build Projects and "Create Build Project "

![15](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/c46a1c7f-4339-4bf8-9797-ddb3bc70e839)

Then Provide Build Name and Select the Repo name from code commit resource
![16](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/845aa5f9-5647-4190-b77c-03166a3cf728)

Select the Branch
![17](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/aca1fd97-aa29-4ccd-9762-f69f5c272346)

In the Environment section, Select
Environment Image: Managed Image
Operating System: Ubuntu
Runtime: Standard
Image: <latest one>
![18](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/53b49aae-7b7e-46ce-bfca-469e3c2be399)

# Note : For this, a Service Role will be required and it will create automatically when we will select the “New Service Role”

![19](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/71b75e7f-cef4-4090-8c93-28940595f141)

Add a file named “buildspec.yaml” in the “demo-app” repository.
(Build file is basically a specification file, that will give the instructions, while building).

# After adding the buildspec.yml perform the git actions 
![Screenshot_1](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/d474ef25-f954-434b-a6f8-1129039cc6b4)


git add.
git commit 
git push

Now, the rest of the things leave as it is, and click on “Create Build Project and Start the Build”.
![21](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/5ce74875-c5ab-434e-8e31-fea44fd0d336)
![22](https://github.com/mohsuhel/Demo_Project_AWSDevOps/assets/127845338/0d66491c-6bd8-4673-9e3f-24818221ac4a)

We can give “Artifacts upload location” if we want to build the code on some specific location.
 Goto “Edit” button and click on “Artifacts”

  Here, select
Type: S3 Bucket. (Create a new s3 bucket if you haven’t created it)
Bucket Name: <Your created bucket>
Name: <Your folder name in S3 bucket> (Go and create one)


















   
