# Proxy-jump
Access one system through other system

Right now i can only access server with name `four` and unable to access server `three` directly. 

So now i will do proxy jump from server four to access server three and access server three directly using single command

# On your local system:

## Edit your SSH config file:

Open or create the SSH config file in your local machine:

```bash
vim ~/.ssh/config
```

## Add the following configuration:

```bash
Host four
    HostName 10.8.0.34
    User four

Host three
    HostName 192.168.1.185
    User three
    ProxyJump four
```

Save and close the file.

## SSH directly to three:
Now, you can SSH directly to three using the following command:

```bash
ssh three
```

This will first SSH into `four@10.8.0.34` and then from there, it will SSH into `three@192.168.1.185`, all in a single command.
