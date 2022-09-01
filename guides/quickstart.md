# Quickstart

> This tutorial will show you how to register a compute machine, deploy a React app and use hot-reload for development.

<i>Last Updated: 8th August, 2022.</i>


## Content
1. [Install Rehost CLI](getting-started/quickstart?id=_1-install-rehost-cli)
2. [Register Compute Machine](/guides/quickstart?id=_2-register-compute-machine)
3. [Deploy an App](/guides/quickstart?id=_3-deploy-an-app)
4. [Update App using Hot-Reload](/guides/quickstart?id=_4-use-hot-reload)

## 1. Install Rehost CLI

Please refer to the [Installation Page](/guides/installation.md) section for instructions on installing the Rehost CLI.

## 2. Connect a VM

In the shell of your VM:
* Make sure that the local port `7500` is free.
* Run `rh login` to authenticate your with your credentials.
* Run `rh machine up` to turn on your machine in the network. It will prompt you to enter machine label. Enter a label that you have not used for any other existing machines in the form: `<username>/<team_label>/<machine_label>`. Refer to [Naming Conventions](/guides/ecosystem?id=naming-conventions) for more information on machine naming conventions.
* Wait for a few seconds until it says `Status: UP`.

Leave this process running and close the SSH connection.

If you have the `ssh` session open, you can press `Ctrl+C` to stop exit the process and run `rh machine down` to properly close the connection with Rehost Servers.

Otherwise, you can directly run `rh machine down` to close the connection.

## 3. Deploy an App

1. Clone this repository

```
git clone https://github.com/Rehost-Startup/template-react.git

```
2. In the root directory of the codebase, edit `rehostapp.yml` file:

```
version: 1

label: '<username>/personal/template-react'
urls:
  - "<username>-personal-react:80"
app_type: 'docker-compose'
machines:
  - "<username>/personal/vm"

```

Here, replace `<username>` with your Rehost Username.

3. Finally, run the following command on local machine to deploy the project:

```
rh app deploy

```
You can monitor the logs of build and app in Rehost Dashboard.

## 4. Use Hot-Reload

In the parent directory of `rehostapp.yml`, run:

```
rh app hot-reload

```

Edit `/src/App.js` file and save to see the changes go live instantly.

In the temrinal session where the hot-reload session is running, you can further use the following commands to send specific changes to the running app:

```
shift+r: Soft-Reload. This will reload the app without rebuilding the app. Any changes to environment or dependencies are not be picked up.
ctrl+r: Hard-Reload. This rebuilds the app and all changes in environment and package dependencies are picked up.

```

<hr/>



If you have any feedback regarding this documentation, feel free to reach out to us on [Discord](https://discord.gg/RnkBxDJJhQ).
**Note:** Only 1 user can use hot-reload at a time for a given deployment.

<i>Last Updated: 8th August, 2022.</i>
