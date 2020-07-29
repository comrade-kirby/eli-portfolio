## Setup
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

## Run project locally
1. `cd Desktop/websitematerial/eli-portfolio` to move into the project folder
2. `git checkout eli` to switch to your branch
3. `git pull` to pull any changes from github
4. `npm install` to install any new dependencies
5. `npm run dev` to start a local server running the project
6. in a web browser go to `http://localhost:5000/` to view the project

> to quit press `ctrl` + `c`

## To Edit

#### Run project locally (same as above)
#### Opening the project
1. `cd Desktop/websitematerial/eli-portfolio` to move into the project folder
2. `code .` to open the project in VSCode 

> or open from VSCode

#### Adding files to the `/public/project_content` folder
There is a folder for each project in the `/project_content` folder. To add a files for a new project, add a new folder.
Each folder should include a folder `/home` and `/project`
- `/home`: splash image and sticker for home page
- `/project`: any number of images or gifs to display in the project page carousel

To add images, drag and drop files into the correct folders

Project folders and files should be named with underscores (`_`) instead of spaces. 
> right click the file and select rename

#### Editing `projects.json`
all projects should have the following format:
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

- name: header text on project page
- homePrimary: splash image on homepage
- homeSecondary: sticker image on homepage
- projectCopy: comma separated list of quoted text for display on project page
- projectMediae: comma separated list of media objects for display in project carousel
  - url: path to file saved in `/public/project_content`
  - altText: text to be read by screen readers or displayed in case of faulty file url

> any quotes in text should be escaped with a backslash (`\`) before each quote

#### Pushing changes to github
1. confirm you are in the branch `eli` (branch name is displayed at the bottom left corner of VSCode)
2. `view > SCM` open the "Source Control" pane in VSCode 
3. review the files listed under "Changes" in the left pane
4. Click the `+` icon for each file after reviewing
5. Write a short message to describe the changes in the "Message" input at the top of the pane.
6. Press `command` + `Enter` to commit changes
7. Select "push" from the `...` dropdown at the top of the pane to push changes to github.
