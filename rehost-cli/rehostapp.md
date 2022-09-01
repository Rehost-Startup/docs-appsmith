# rehostapp.yml

This is a configuration file used to save compute machine on Rehost Servers. Once it is saved on the server, any app can deployed on this machine using the CLI.

**Note:** This file must be placed in the root (`/`) directory of your app.

Here's what it looks like:

```
label: 'john/personal/startup-app'
urls:
  - "app:80"
  - "auth:3006"
app_type: 'docker-compose'
machines:
  - "john/personal/gcp"

```

* `label (required)`: It is used to give a **unique identifier** to the app. The label must follow the following syntax:

```
<username>/<teamname>/<label>
```
Please refer to [Rehost Naming Conventions](/guides/ecosystem?id=naming-conventions) for complete information.

The complete label must be unique in the system, ie, two teams can have an app with the same label since team names are different.

**Example:**
```
label: 'john/personal/startup-app'
```

* `app_type (required)`: This is used to identify the type of app running and is restricted to the following values:

  * `docker-compose`
**Example:**
```
app_type: 'docker-compose'
```
* `machines (optional)`: This is a list of labels of [Rehost Machines](/rehost-cli/rehostmachine.md) where this app will be deployed. You can update the target machines later too.
**Example:**
```
machines: 
  - 'john/personal/gcp'
  - 'john/personal/ec2'
```

* `urls (optional)`: This is a list of subdomains mapped to port numbers of the running app. 
 It exepects a list of strings that are in the following format:
 ```
<subdomain>:<number>
```

And using this, Rehost will generate a URL(s) in the format:

```
https://<subdomain>.rehost.in
```
**Note**: Deeper or nested subdomains are not allowed. For example, you can not have subdomain like `admin.myproduct` as it will generate a subdomain, `https://admin.myproduct.rehost.in`. It is a safe practise to format the subdomain in the format: `<username>-<teamname>.<applabel>` to avoid conflicting subdomains.

**Example:**
```
urls: 
  - 'myapp:80'
  - 'admin-myapp:3600'

This will generate the URLS:
- `https://myapp.rehost.in` that serves app running at local port 80
- `https://admin-myapp.rehost.in` that serves app running at local port 3600
```

* `vars (optional)`: A var is a `string` in your project files that you want to be dynamic and change easily. It could be considered as a handy configuration point for your app. For example, you have defined SQL table name or MongoDB collection in a file `/src/config/db.js` as "AdminUsers" that you wish to change to "Users". You can update this through the console or the CLI without having to touch your codebase by defining a variable `AdminUsers` and setting is value as `Users`. Rehost will search for `AdminUsers` in all the files requested in `files` field that is described below.

**Example:**
```
vars:
  - AdminUsers: 'Users'
  - DB_PORT: '27017'
```

* `files (optional)`: This is a list of files where Rehost will search for strings that match with variables defined in `vars` field. For example, if you have a string named `AdminUsers` in your file `/src/config/db.js`, you need to have an entry `/src/config/db.js` in `files` and respective variable `vars` field. Rehost will search for `AdminUsers` in all the files requested in `files` at the time of deployment.

**Example:**
```
vars:
  - '/src/config/db.js'
  - '/.env'
```
