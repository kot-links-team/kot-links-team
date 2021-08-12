- 👋 Hi, I’m @kot-links-team
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
kot-links-team/kot-links-team is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

Slam Tg Mirror Bot is a multipurpose Telegram Bot writen in Python for mirroring files on the Internet to our beloved Google Drive.

Features supported:
Click Here For More Details
How to deploy?
Deploying is pretty much straight forward and is divided into several steps as follows:

Installing requirements
Clone this repo:
git clone https://github.com/breakdowns/slam-tg-mirror-bot mirrorbot/
cd mirrorbot
Install requirements For Debian based distros
sudo apt install python3
Install Docker by following the official Docker docs

For Arch and it's derivatives:
sudo pacman -S docker python
Install dependencies for running setup scripts:
pip3 install -r requirements-cli.txt
Generate Database
Click Here For More Details
Setting up config file
Click Here For More Details
Getting Google OAuth API credential file
Visit the Google Cloud Console
Go to the OAuth Consent tab, fill it, and save.
Go to the Credentials tab and click Create Credentials -> OAuth Client ID
Choose Desktop and Create.
Use the download button to download your credentials.
Move that file to the root of mirrorbot, and rename it to credentials.json
Visit Google API page
Search for Drive and enable it if it is disabled
Finally, run the script to generate token.pickle file for Google Drive:
pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
python3 generate_drive_token.py
Deploying
Start Docker daemon (skip if already running):
sudo dockerd
Build Docker image:
docker build . --rm --force-rm --compress --no-cache=true --pull --file Dockerfile -t mirrorbot
Run the image:
sudo docker run mirrorbot
Deploying on Heroku
Give stars and Fork this repo then upload token.pickle to your forks, or you can upload your token.pickle to your Index and put your token.pickle link to TOKEN_PICKLE_URL (NOTE: If you didn't upload token.pickle uploading will not work). How to generate token.pickle? Read here
Hit the DEPLOY TO HEROKU button and follow the further instructions in the screen (NOTE: If vars not coming, just change deploy link to your fork, Example: https://dashboard.heroku.com/new?template=https://github.com/yourgithubname/slam-tg-mirror-bot)
Recommended to use 1 App in 1 Heroku accounts
 

Deploying on Heroku with heroku-cli and Goorm IDE
 

Using Service Accounts for uploading to avoid user rate limit
For Service Account to work, you must set USE_SERVICE_ACCOUNTS="True" in config file or environment variables, Many thanks to AutoRClone for the scripts. NOTE: Using Service Accounts is only recommended while uploading to a Team Drive.

Generate Service Accounts. What is Service Account
Click Here For More Details
Add all the Service Accounts to the Team Drive
Run:
python3 add_to_team_drive.py -d SharedTeamDriveSrcID
Youtube-dl authentication using .netrc file
For using your premium accounts in Youtube-dl or for protected Index Links, edit the netrc file according to following format:

machine host login username password my_youtube_password
For Index Link with only password without username, even http auth will not work, so this is the solution.

machine example.workers.dev password index_password
Where host is the name of extractor (eg. Youtube, Twitch). Multiple accounts of different hosts can be added each separated by a new line.
