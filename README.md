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
![Screenshot (310)](https://user-images.githubusercontent.com/46739055/93012847-1fd88c00-f5c1-11ea-8d65-da48d4e34831.png)


(Here the curl command after deployment should return “HTTP/1.1 200 OK”)



Understanding the yaml file(See the comments starting with “#”):



name: Deploy Website
	

	on: [push]                                                           #make changes when any commit is pushed
	

	jobs:
	  build:
	    runs-on: ubuntu-latest                                #runs the code on ubuntu operating system
	    name: Deploying to surge                           #name of the job
	    steps:
	      - uses: actions/checkout@v1
	      - name: Install surge and fire deployment
	        uses: actions/setup-node@v1
	        with:
	          node-version: 14   #the node version of the website  
	      - run: npm install -g surge                                                   #to build and install the surge libraries
	      - run: npm install --global mocha                                                       #to install the mocha gloabally
	      - run: npm test #to run the test 
	      - run: surge ./ ${{ secrets.SURGE_DOMAIN }} --token ${{ secrets.SURGE_TOKEN }}  #to deploy on surge
	      - run: sudo apt install curl                                                                    #to install the curl
	      - run: curl -Is http://www.google.com | head -n 1                         #to perform after-deploy test


Note: You can visit the web page: http://kindly-birthday.surge.sh/







