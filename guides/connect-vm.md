# Connect a VM to Rehost Console

<i>Last Updated: 8th August, 2022.</i>

## Prerequisites
* You have a live cloud virtual machine (VM). Here are some helpful blogs for popular hosting providers:
  * [How to create a VM using Google Cloud](https://www.techrepublic.com/article/how-to-create-a-virtual-machine-in-google-cloud-platform/)
  * [How to create a VM using AWS](https://medium.com/edureka/aws-ec2-tutorial-16583cc7798e](https://medium.com/edureka/aws-ec2-tutorial-16583cc7798e)
  * [How to create a VM using Microsoft Azure](https://medium.com/@ramdhanrizki11/how-to-easily-create-virtual-machine-on-microsoft-azure-eae9202878e7)
  * [How to create a VM using Digital Ocean](https://docs.digitalocean.com/products/droplets/how-to/create/)

* You have `ssh` access to your VM
* You have created a [Rehost Team](#)

## Step 1: Install Rehost CLI
`ssh` into your VM and install Rehost CLI. Please refer to [CLI Installation page](/guides/installation.md "Installation | Rehost CLI") for instructions on installing the Rehost CLI. Linux, Mac and Windows images are supported.

## Step 2: Establish connection

<div class="container-fluid">
  <div class="row justify-content-center">
    <div class="col-12 col-lg-8 p-0 p-lg-5">
      <img class="img-fluid" src="images/rh-machine-up.png">
    </div>
  </div>
</div>
<br/>
* Make sure that the local port `7500` is free.
* Run `rh login` to authenticate your with your credentials
* Run `rh machine up` to turn on your machine in the network. It will prompt you to enter machine label. Enter a label that you have not used for any other existing machines in the form: `<username>/<team_label>/<machine_label>`. Refer to [Naming Conventions](/guides/ecosystem?id=naming-conventions) for more information on machine naming conventions.
* Wait for a few seconds until it says `Status: UP`.

Leave this process running and close the SSH connection.

If you have the `ssh` session open, you can press `Ctrl+C` to stop exit the process and run `rh machine down` to properly close the connection with Rehost Servers.

Otherwise, you can directly run `rh machine down` to close the connection.

## Next Steps

* [Deploy an App](/guides/deploy-app)

<i>Last Updated: 8th August, 2022.</i>