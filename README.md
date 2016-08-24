# Amazon Web Services EC2

![Image](http://cdn2.itpro.co.uk/sites/itpro/files/server_room.jpg)

**What is it?**

- Amazon Web Services (AWS) EC2 is a service provided by Amazon that allows you to easily create server instances.
- These servers can be used to host/run basically anything. For example you can use EC2 instances to host/run your Rails apps or Node.js apps.

**Why AWS EC2?**

- EC2 makes scaling your application and service very easy. Amazon makes this super simple with auto scaling groups and load balancers.
- Amazon has a **TON** of resources.
- AWS has a lot more features and services to help make your app even better. S3, DynamoDB, CodeDeploy, CloudWatch, Lambda are just a few of the many services AWS provides to help make deployment easier.

**Setup**

- We will be setting up the server using the online AWS console
- Once that is complete we will be using SSH to connect to our EC2 server and run terminal commands on the server

**Steps/Commands**

- Create server using Amazon Web Services EC2 Management Console
  - Log into [AWS](http://aws.amazon.com)
  - Open EC2 Console
  - Click Launch Instance
  - Choose Amazon Machine Image (AMI)/OS
  - Choose instance type (make sure to look at EC2 pricing)
  - On step 4 you can choose how much storage your instance will have
  - Step 5 you will be able to name your instance to easily track later on
  - Step 6 you will be able to configure your security group
    - For most web instances you will probably want to open HTTP (port 80) everywhere
    - If you are using SSL or HTTPS (port 443) you will probably want to open that everywhere
    - For SSH you might just want to open that for your specific IP so only people on your IP address can SSH into your server
  - Launch the instance
- Select your new instance in the Instance tab in the EC2 Dashboard
- Note the Public IP address in the details menu at the bottom of the screen for your instance
- Click connect to get the details on how to connect to your instance
- SSH into instance `ssh URLHERE` **NOTE** you must include the `-i` tag and a link to your private key unless you setup that key to be universal on your computer
- Install Node on EC2 instance

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

- Get code on server ([SCP](http://www.hypexr.org/linux_scp_help.php), Git Pull, FTP, [AWS CodeDeploy](https://aws.amazon.com/codedeploy/), etc.)
- [Map port 3000 to port 80](http://stackoverflow.com/questions/16573668/best-practices-when-running-node-js-with-port-80-ubuntu-linode) `sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000`
- `node server.js`
- Open server IP in browser

**Important Notes**

- Running `node server.js` will only run in that single SSH instance. So when you quit terminal your app will no longer be live. [PM2](https://github.com/Unitech/pm2) is a great Node package to run server even after quitting terminal or SSH.
- Be sure to think about what happens if you server or app crashes. Always make sure to have backup systems in place as best as you can.
- Remember you can also map the IP address of your EC2 instance to your domain DNS so you can type in your domain name instead of IP address to view your website.
- Don't forget to look at the [pricing](https://aws.amazon.com/ec2/pricing/) for EC2 instances 
- We just talked about the very basics about getting a basic Node/Express app running on an EC2 instance. The possibilities are infinite and there is **SO** much more you can do with EC2.
