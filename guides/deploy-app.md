# Connect a VM to Rehost Console

<i>Last Updated: 8th August, 2022.</i>

## Prerequisites
* You have created a [Rehost Team](#)
* You have [connected a VM](/guides/connect-vm)

There are 2 methods to deploy an app, using the [Console](/guides/deploy-app?id=deploy-using-the-console) and the [CLI](/guides/deploy-app?id=deploy-using-rehost-cli).

## Deploy using the Console

In this case, you do not need to modify anything in your code. Zip your app files and upload it. Currently, Rehost only supports `docker-compose` apps. You must zip your files such that `docker-compose.yml` file is in the root directory of the zip file.

<div class="container-fluid">
  <div class="row justify-content-center">
    <div class="col-12 p-0 p-lg-5">
      <img class="img-fluid" src="images/create-app-annotated.png">
    </div>
  </div>
</div>
<br/>

Rehost CLI manages connects the local ports you want to public URLs and generates a URL automatically on deployment. Next, Provide the zip files and the machine label. Hit deploy and wait for the app to be deployed.

What's next? You can monitor all of your app logs in 1 place.

<div class="container-fluid">
  <div class="row justify-content-center">
    <div class="col-12 p-0 p-lg-5">
      <img class="img-fluid" src="images/manage-app-annotated.png">
    </div>
  </div>
</div>
<br/>

## Deploy using Rehost CLI

### Step 1: Install Rehost CLI

Please refer to [CLI Installation page](/guides/installation.md "Installation | Rehost CLI") for instructions on installing the Rehost CLI. Linux, Mac and Windows images are supported.

### Step 2: Create configuration file

In the root of your project, create a file `rehostapp.yml` with the following content:

```
label: '<username>/<team_name>/startup-app'
urls:
  - "my-product-name:3000"
app_type: 'docker-compose'
machines:
  - "<username>/<team_name>/gcp"
```

Here, `<team_name>` would be the one you have created earlier.

Currently, Rehost supports only Dockerized apps that have `docker-compose.yml` defined.

`urls` is a list of strings in the format: `<subdomain>:<port>`. In the given example, Rehost will generate a url `https://my-product-name.rehost.in` that will serve the app running at local port `3000` on the VM. If you have more apps running on some other ports that you want to be served publiclly, you can more strings to the `urls` list.


### Step 3: Deploy App

* Run `rh login` to authenticate your with your credentials
* Run `rh app deploy` in the directory where the `rehostapp.yml` file is present.
That's all. Your app should be live in a few minutes. Hop on to the Rehost Console to monitor your app logs.


<i>Last Updated: 8th August, 2022.</i>