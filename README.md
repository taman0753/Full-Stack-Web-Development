Website to surge via Github Actions!

This will help you to build , test and deploy your website to surge via Github actions.

The website used here is a basic website with HTML,CSS and NodeJs. All the files are here for the reference.(The test folder here contains a basic test script)

Steps:
1)	Get a Deployment Token- Run the command “surge token” from cmd and save the token for future use.

2)	 Setup 2 secrets in your repository secrets tab
SURGE_TOKEN -> Your Surge Token from cmd
SURGE_DOMAIN -> The domain you want to publish your site 

3)	Now go to actions tab and crate a custom workflow with yaml file and save it.
(Here we are going to do two test ,one before deployment with mocha and second after deployment with curl command)

![Screenshot (311)](https://user-images.githubusercontent.com/46739055/93012822-d8ea9680-f5c0-11ea-8010-81edf72f5fc3.png)

4)	Test it with a commit.

Completed Jobs:

