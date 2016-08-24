# Amazon Web Services EC2

![Image](http://cdn2.itpro.co.uk/sites/itpro/files/server_room.jpg)

**What is it?**

- Amazon Web Services (AWS) EC2 is a service provided by Amazon that allows you to easily create server instances.
- These servers can be used to run Node.js apps, Rails apps, or many other things.

**Why AWS EC2?**

- EC2 makes scaling your application and service very easy. Amazon makes this super simple with auto scaling groups and load balancers.
- Amazon has a **TON** of resources.
- AWS has a lot more features and services to help make your app even better.

**Setup**

- We will be setting up the server using the online AWS console
- Once that is complete we will be using SSH to connect to our EC2 server and run terminal commands on the server

**Steps/Commands**

- Create server using Amazon Web Services EC2 Management Console
- SSH into server `ssh URLHERE`
- Install Node on EC2 instance

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

- Get code on server (SCP, Git Pull, FTP, etc.)
- [Map port 3000 to port 80](http://stackoverflow.com/questions/16573668/best-practices-when-running-node-js-with-port-80-ubuntu-linode) `sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000`
- `node server.js`
- Open server IP in browser

**Important Notes**

- Running `node server.js` will only run in that single SSH instance. So when you quit terminal your app will no longer be live. [PM2](https://github.com/Unitech/pm2) is a great Node package to run server even after quitting terminal or SSH.
- Be sure to think about what happens if you server or app crashes. Always make sure to have backup systems in place as best as you can.
- Remember you can also map the IP address of your EC2 instance to your domain DNS so you can type in your domain name instead of IP address to view your website.
- Don't forget to look at the [pricing](https://aws.amazon.com/ec2/pricing/) for EC2 instances 
- We just talked about the very basics about getting a basic Node/Express app running on an EC2 instance. The possibilities are infinite and there is SO much more you can do with EC2.
