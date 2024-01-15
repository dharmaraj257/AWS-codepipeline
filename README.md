
# Project TitleContinuous Deployment using AWS Code Pipeline and S3

Code for a game is hosted in GitHub. We create an S3 bucket for static website hosting, then create a continuous deployment pipeline (using AWS Code Pipeline) to automatically deploy the code whenever changes are made.

# The Game
A simple memory matching game. The user clicks two cards (images of memes) to try to match them. If there's a match, the cards disappear from the board. If there's no match, the cards are flipped back to their blank side so the user can try again.
The game consists of HTML, CSS and JavaScript.

# The Deployment Environment
The code will be deployed and hosted in S3.
1. Create a bucket and give unique name my-meme-game-150124.
2. Uncheck Block all public access and acknowledge then click create bucket.
3. Go to properties sectin and Enable Static Website Hosting and add index.html click save changes.
4.Go to persmission click edit bucket policy and add below policy copy paste it in bucket policy
```
{
    "Version": "2012-10-17",
    "Statement": [
    	{
        	"Sid": "PublicReadGetObject",
        	"Effect": "Allow",
        	"Principal": "*",
        	"Action": [
            	"s3:GetObject"
        	],
        	"Resource": [
                "arn:aws:s3:::my-meme-game-150124/*"
        	]
    	}
    ]
}
``` 

# The Deployment Pipiline
The pipeline is created using AWS Code Pipeline. The pipeline pulls the code from GitHub, and deploys it to S3 whenever a change is detected in the code.
# Setup Aws codepipeline
1. Click create codepile give the pieline name meme-pipeline.
2.Select pipeline type v1 and select new service role click next.

3.select service provider Github (Version 2) and connect with codepipeline.

4.Click on the connection github give name meme-github-pipeline and click connect with Github.

5.log in your github account then click Authorize AWS Connector for
GitHub.

6. Click Install a new app it will bring your github profile dropdown select repository and click save.

7. Click connect now connection is ready you to select latest created connection and select repository name.

8. In pipeline trigger select push in a branch also select Branch name main and In Output artifact format select Codepipeline default click next.

9. Build provider click on skipbuild and next.

10. Select deploy stage Amazon S3,select bucket name, click check box Extract file before deploy next and review everything and Click create pipeline. 

11. After Successfully deploy pipeline, In S3 bucket go to properties now you can see pipile generated project endpoint.

12. Click the link and open in browser.

# Output:



