# test-pipeline
Testing out heroku pipeline functionality!

The actual files in the repository are just a test site, this github repo gets hooked up to heroku and will autodeploy anytime a change is pushed.

After the git push, the build will appear on the subdomain hooked up to the Development dyno. From here we can promote the development build to staging, and then to production. This allows for us to separate builds cleanly without needing to juggle files depending on who's looking.

# Create new pipeline and connect github repo

![image](https://user-images.githubusercontent.com/7696222/164936431-9a0811f3-8ce0-4040-9560-a5dfa9864520.png)

Add new apps by clicking + Add app at the top of any of the swimlanes

In order to add to the development swimlane (this lane isn’t shown by default), create an app in the staging lane, then click on the bottom right corner, “Move app to development”

![image](https://user-images.githubusercontent.com/7696222/164936448-42832bf4-5823-412f-8fdd-b1207bdc1661.png)

# Settings / Buildpack
In the dyno you plan to deploy to, set the build pack, or the build will fail.
Use the below link for playcanvas builds (https://buildpack-registry.s3.amazonaws.com/buildpacks/heroku-community/static.tgz)

Add a static.json file
This allows you to configure CSP rules
The file itself has a specific format and the rules will vary depending on project setup, domains supported, etc.
Possible starting point: https://report-uri.com/home/generate 

# Overview
You now have a full development pipeline
New changes and build should be pushed to the git branch associated with pipe-dev, with auto deploy, all you need to do is a standard git add/git commit/git push
Once pipe-dev has a new build, it can be promoted to staging (typically for client preview builds), or production (final builds, user facing)

![image](https://user-images.githubusercontent.com/7696222/164934693-40c7fd8c-9a46-4dec-ac45-c197e3d81272.png)
