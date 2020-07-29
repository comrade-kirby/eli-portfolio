### Setup
#### VSCode
1. Download [VSCode](https://code.visualstudio.com/Download)
2. Launch VSCode
3. press `⇧⌘P` while in the app
4. Type `shell command` in the prompt and select the first item to install 'code'

#### Terminal 
1. `cd Desktop/websitematerial` to move to your documents folder
2. `git clone git@github.com:OppNHeimer/eli-portfolio.git` to download the project folder
3 `git checkout eli` to switch to your branch
4. `npm install` to install dependencies
5. `code .` to open the project in VSCode

### Run project locally
1. `cd Desktop/websitematerial/eli-portfolio` to move into the project folder
3. `npm install` to install dependencies
2. `npm run dev` to start a local server running the project
3. in a web browser go to `http://localhost:5000/` to view the project
4 to quit controlc
### To Edit
#### Opening the project
1. `cd Desktop/websitematerial/eli-portfolio` to move into the project folder
2 `git checkout eli` to switch to your branch
3 `git pull` to pull any changes from github
4. `npm install` to install any new dependencies
3. `code .` to open the project in VSCode
5. `npm run dev` to start the local server

#### Editing `projects.json`
all projects should have the format:
```
"2020_calendar": {
  "name": "2020 CALENDAR",
  "homePrimary": "/project_content/2020_calendar/home/2020-cal-gif.gif",
  "homeSecondary": "/project_content/2020_calendar/home/2020.png",
  "projectCopy": ["paragraph 1 text", "paragraph 2 text", "...."],
  "projectMediae": [
    { 
      "url": "/project_content/16_on_center/project/IG_SLA-We're-Hiring.gif",
      "altText": "insert some text here"
    },
    { 
      "url": "/project_content/16_on_center/project/IGS_Bite_Weekly_Specials.mp4",
      "altText": "insert some text here"
    }
  ]
}
```

any quotes should be escaped with a \
#### Adding files

#### Pushing changes
commit and push
