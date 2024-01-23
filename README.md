
# Continuous Deployment using AWS Code Pipeline and S3

Code for a game is hosted in GitHub. We create an S3 bucket for static website hosting, then create a continuous deployment pipeline (using AWS Code Pipeline) to deploy the code whenever changes are made automatically.

# The Game
A simple memory-matching game. The user clicks two cards (images of memes) to try to match them. If there's a match, the cards disappear from the board. If there's no match, the cards are flipped back to their blank side so the user can try again.
The game consists of HTML, CSS, and JavaScript.

# The Deployment Environment
The code will be deployed and hosted in S3.
1. Create a bucket and give the unique name my-meme-game-150124.
2. Uncheck Block all public access and acknowledge then click Create bucket.
3. Go to the properties section Enable Static Website Hosting and add index.html click save changes.
4. Go to permission click edit bucket policy and add the below policy copy and paste it into bucket policy.
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

# The Deployment Pipeline
The pipeline is created using AWS Code Pipeline. The pipeline pulls the code from GitHub and deploys it to S3 whenever a change is detected in the code.
# Setup Aws code pipeline
1. Click Create code pile and give the pipeline name meme-pipeline.
2. Select pipeline type v1 select new service role and click next.

3. select service provider Github (Version 2) and connect with the code pipeline.

4. Click on the connection Github give the name meme-github-pipeline and click connect with Github.

5. log in to your GitHub account then click Authorize AWS Connector for
GitHub.

6. Click Install a new app it will bring your GitHub profile dropdown select repository and click save.

7. Click Connect Now. The connection is ready you to select the latest created connection and select repository name.

8. In the pipeline trigger select push in a branch also select Branch name main In Output artifact format select Codepipeline default and click next.

9. Build provider click on skipbuild and next.

10. Select deploy stage Amazon S3, select bucket name, click check box Extract file before deploying next review everything, and Click create a pipeline. 

11. After Successfully deploying the pipeline, In the S3 bucket go to properties now you can see the generated project endpoint.

12. Click the link and open it in the browser.

# Output:


![Screenshot (26)](https://github.com/dharmaraj257/AWS-codepipeline/assets/100831265/143dcaff-d2f8-4925-bd32-503c10d7f21b)

