# Hot-Reload an App

<i>Last Updated: 8th August, 2022.</i>

> Hot-Reload is intentionally designed for development servers and static websites.

## Prerequisites
* You have [deployed an App](/guides/deploy-app)

<div class="container-fluid">
  <div class="row justify-content-center">
    <div class="col-12 p-0 p-lg-5">
      <img class="img-fluid" src="images/rh-app-hot-reload.png">
    </div>
  </div>
</div>
<br/>

To Hot-Reload a live app, run `rh app hot-reload` in the root directory of the app files(where `rehostapp.yml` is located).

Next, make any change to a file locally and it will be reflected on the remote machine within 3s.
In the temrinal session where the hot-reload session is running, you can further use the following commands to send specific changes to the running app:

```
shift+r: Soft-Reload. This will reload the app without rebuilding the app. Any changes to environment or dependencies will not be picked up.
ctrl+r: Hard-Reload. This rebuilds the app and all changes in environment and package dependencies are picked up.
```

**Note:** Only 1 user can use hot-reload at a time for a given deployment.

Here are some hot-reload templates for popular web technologies:
* [Static Site Hot-Reload Template](https://github.com/Rehost-Startup/template-static-site)
* [React Hot-Reload Template](https://github.com/Rehost-Startup/template-react)
* [Angular Hot-Reload Template](https://github.com/Rehost-Startup/template-angular)
* [Vue Hot-Reload Template](https://github.com/Rehost-Startup/template-vue)
* [Node.js Hot-Reload Template](https://github.com/Rehost-Startup/template-nodejs)
* [Node.js (Typescript) Hot-Reload Template](https://github.com/Rehost-Startup/nodejs-ts)


<i>Last Updated: 8th August, 2022.</i>