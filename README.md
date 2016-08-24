# Amazon Web Services EC2

![Image](http://cdn2.itpro.co.uk/sites/itpro/files/server_room.jpg)

**What is it?**

- Amazon Web Services (AWS) EC2 is a service provided by Amazon that allows you to easily create server instances.
- These servers can be used to run Node.js apps, Rails apps, or many other things.

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

- Get code on server (SCP, Git Pull, FTP)
- [Map port 3000 to port 80](http://stackoverflow.com/questions/16573668/best-practices-when-running-node-js-with-port-80-ubuntu-linode) `sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000`
- `node server.js`
- Open server IP in browser
