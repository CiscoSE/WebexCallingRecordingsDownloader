Simple application to collect all Webex Calling recordingIds and associated ownerEmails (hostEmails) and then download all call recordings and transcripts for those calls locally. This is meant to demonstrate the code logic for bulk downloading Webex Calling recordings using the REST APIs.

This sample is a variant of this Webex Recordings Downloader sample code:
https://github.com/WebexSamples/WebexRecordingsDownloader

It is a two step process which requires the app to be ran twice.

On first run choose option 1 and provide your Webex site URL, for example _sitename.webex.com_, and enter the number of weeks you want to pull recordings for.

- This collects all recordingIds and hostEmails and stores them in the recordings.csv file.
- The app will terminate itself after completion.

Run the app again choose option 2.

- This will download all recordings and transcripts that were retrived from step 1 and save them to the "Downloaded-Recordings" folder.

---

**Install and Run**

Clone project:

- `git clone https://github.com/CiscoSE/WebexCallingRecordingsDownloader.git`

Install dependencies:

- `pip install -r requirements.txt`

Run app:

- `python recordings.py`

---

**Setup**

This sample requires that the user credentials or integration you use have the spark-compliance:recordings_read scope

Option 1:

- Login to the developer portal using the credentials of the Compliance Officer account for your organization and copy the personal access token from https://developer.webex.com/docs/getting-started.
- When you first run the app it will ask you to provide the token you copied from the above page.
- This will allow the app to run for 12 hours as that is how long the personal access token is only valid for. You would need to login to the developer portal again to get a new personal access token for the Compliance Officer account if the current one has expired.

Option 2(this will allow the app to handle token refreshes):

- Create an [Integration](https://developer.webex.com/docs/integrations) or [Service App](https://developer.webex.com/docs/service-apps) with the admin and compliance related recording scopes.
- Generate your access and refresh tokens
- Rename the [.env.local](.env.local) file to .env. And add .env to the .gitignore file
- Add your Client ID, Client Secret and Refresh Token to the .env file.
- You can also add your Access Token to the [token.json](token.json) file but the app will also ask you to enter one at first run if you haven't added it to the token.json file.
