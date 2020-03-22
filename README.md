
# ImageUp
Image hosting and sharing web application. Uploaded images recieve a unique link for ease of sharing.

## Build & Run (ubuntu)
Install NodeJS
```bash
curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Download project files
```bash
git clone https://github.com/Onusai/ImageUp.git
```

### Build static front-end files
Install frontend dependenices
```bash
cd ImageUp/client
sudo npm i -g @vue/cli
npm install
```
Build
```bash
npm run build
```
The files will output into `ImageUp/server/public`
### Backend setup
Install backend dependencies
```bash
cd ImageUp/server
npm install
```
Edit and configure the `.env` file. (`ImageUp/.env`).  

`NODE_ENV` - Can be set to either `development` or `production`  
- When set to developoment, only the back-end API will be served  
- When set to production, the static front-end files located in `ImageUp/server/public`  will be served along with the back-end API  

`PORT` - The port on which the API will be served (and front-end if NODE_ENV is set to production)  

`UPLOAD_DIR` - Directory where uploaded images will be stored. Keep in mind that ANY files in this directory will publicly available.  

`DB_HOST` - URL to a Mariadb server  
`DB_USER` - DB Username  
`DB_PASSWORD` - DB Password  
`DB_DATABSE` - DB Name  

### Database
This application requires a connection to a Mariadb server. You must manually create a database in it before starting the application.
```sql
CREATE DATABASE imageup;
```
The name can be anything, but it must match the name in your `.env` file.

## Running the server
If `NODE_ENV` is set to `production`
```bash
npm run start
```
The application should now be up and running.


If `NODE_ENV` is set to `development` then you must also simultaneously host the front-end in another terminal session
```bash
cd ImageUp/client
npm run serve
```
