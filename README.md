# node-caldav-server
This is a CalDav server written by express.js with babel, using pure ES6 features to develop

## Features
- support multiple users with sqlite database
- much faster than radicale
- offer additional APIs for microservice
- easy to implement authentication
- easy to migrate to any other database  
- friendly with developer because of ES6 features thanks to babel
- detailed documents for both deployment and use

## Deployment
node-caldav-server relys on node-gyp, which does not work perfect on Windows

Therefore, *nux is the best deployment platform.

### Config
Open the `conf/config.js`, you can see the following statements
```
module.exports = {
    db:{
        databaseType: 'sqlite',         // database type
        databaseName: 'caldav',         // database name
        databaseFile: 'caldav.db',      // sqlite only,the storage file path
        shouldTruncateAllTables: false, // true will drop the table if it already exists when server is starting
    },
    mountedPath:{
        calDavPath: '/cal',     // the root path for caldav service
        principalPath: '/p',    // the root path for principal service
    }
}
```

Feel free to modify the config, then run the following command

```
npm install
npm start
```

The server is now running at localhost:3000


## Usage
### CalDav URL
>localhost:3000/cal/:user_name/:calendar_name

please replace the `:user_name` with your own name first.

Then, replace the `calendar_name` with a calendar name. If the calendar isn't exists, we will create it.

Therefore, the URL example can be: 
>localhost:3000/cal/demo/demo

Finally, you will be asked to provide an account with password to login node-caldav-server.

Don't worry about the account, if it isn't exists, we will create it, too.


### CalDav client
node-caldav-server is still in developing.

After developing, we will test every CalDav client listed here.

It won't be long, which we think is less than a month   

### Client Being tested
- [x] Mozilla Lightning
- [x] SOL Calendar
- [ ] IPHONE & IPAD Calendars
- [ ] OSX Calendars
- [ ] CalendarSync
- [ ] ContactSync
- [ ] CalDav-Sync
- [ ] DAVdroid
- [ ] ACAL

### Mozilla Lightning
Mozilla Lightning is a plugin for Mozilla Thunderbird to add the CalDav support

- click on File and New Calendar
- first window:
    - choose a calendar On the Network
- next window:
    - choose protocol as CalDav
    - location: see the Usage part
    - disable the offline support
- final window:
    - you can set whatever you want , since settings of final window is only used by Mozzila Lightning rather than CalDav server.

You can now add events and tasks to your calendar. 

### SOL Calendar
SOL Calendar is an wonderful Android app , which focus on Calendar including CalDav

- open Settings
- click on Add other calendar account
- click on Custom
- Upcoming window:
    - CalDav Root URL: see the CalDav URL part
    - ID, your username of account
    - Password, your password of account

You can now add events and tasks to your calendar. 

