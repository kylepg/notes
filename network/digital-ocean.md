## DigitalOcean

So far we have two instances of our `hello-world` application:

* One on our local machines
* One on Github.com

The third and final piece of the puzzle we need to complete your workflow is a production server where you can publish your work online so that it's available for the world to see.

The server platform we'll use in this course is **DigitalOcean** which offers virtual private servers (VPS) of [varying sizes and specs](https://www.digitalocean.com/pricing/).

To get started, head over to <https://digitalocean.com> and create a new account. Setting up your account will be free; it's once you're set up and start creating _Droplets_ that pricing will come into play; more on that later.

## SSH Key: Your computer <-> DigitalOcean

After setting up your account, the first thing you'll want to do is **set up a SSH key**. This will prevent you from having to enter your password every time you communicate with DigitalOcean from command line.

For this course, you can use the same `id_rsa.pub` key you created when you configured Github. Use the `cat` command to open this file, then copy its contents.

Mac:

```bash
$ cat ~/.ssh/id_rsa.pub
```

Windows:

```bash
$ cat %home%/.ssh/id_rsa.pub
```

Back in DigitalOcean, click the Gear icon (top right) then go to _Settings_ and then _Security_.

Within _Security_ find the **SSH Keys** section and the blue button to **Add SSH Key**.

Paste in the contents of the `id_rsa.pub` file you copied above, and give the key a descriptive name.

<img src='https://s3.amazonaws.com/making-the-internet/vc-do-ssh-key@2x.png' style='max-width:888px; width:100%' alt='New SSH key on DigitalOcean'>

That's it for the SSH key for now. In a few steps, we'll test to confirm it's working.

<small>
Note: Instead of using your Github key, you could have generated a unique one for DigitalOcean. This latter technique is more secure and suggested for projects beyond the scope of this class.
</small>

## Droplet Pricing

With some initial DigitalOcean configurations behind you, it's time to create your first _Droplet_.

DigitalOcean calls their virtual servers **Droplets**; each Droplet that you spin up is a new virtual server for your personal use.

In this course, you'll use **one single Droplet** to host all of your class projects.

The base plan which costs $5/month should be enough to serve your needs for this course. For the duration of the semester (4 months), your total cost will be $20.

(If you want to save some money, see [dwa15.com > Software & Services](https://dwa15.com/software) for details on getting a free DigitalOcean credit via Github Education's Student Developer Pack.)

## New Droplet

From your DigitalOcean dashboard, find the big green button labeled _Create Droplet_ to initiate a new Droplet.

On the screen that follows, make your Droplet settings match the following options:

<img src='https://s3.amazonaws.com/making-the-internet/vc-digital-ocean-new-droplet@2x.png' style='max-width:1031px; width:100%' alt='New Droplet at Digital Ocean'>

## Log in to your new server droplet via SSH

Once your Droplet is created, make note if its IP address:

<img src='https://s3.amazonaws.com/making-the-internet/vc-do-new-ip-address@2x.png' style='max-width:835px; width:100%' alt='New IP address on Droplet'>

From your local command line, SSH into your DigitalOcean droplet using the username `root` and the IP address:

```bash
$ ssh root@your-digital-ocean-ip-address
```

When you first connect, you'll see the following message indicating it's a connection your computer does not recognize. Type `yes` and hit _Enter_ to confirm the connection.

```xml
The authenticity of host '104.236.13.65 (104.236.13.65)' can't be established.
RSA key fingerprint is 4a:6e:8b:f2:39:27:ec:05:e1:46:e2:a6:80:e4:e9:d3.
Are you sure you want to continue connecting (yes/no)? yes
```

After you hit enter, if your SSH key is set up properly, you should be logged into your server. You should _not_ be prompted for a password (the SSH key is your security credential for connecting, so no password is required).

## SSH Key: DigitalOcean <-> Github.com

In order to communicate between your DigitalOcean droplet and Github, you need to set up _another_ SSH key.

While still SSH'd in to your DigitalOcean droplet, generate a new SSH key:

```xml
$ ssh-keygen -t rsa -C "your@email.com"
```

Press enter:

```xml
$ Enter file in which to save the key (/root/.ssh/id_rsa):
```

Press enter:

```xml
$ Enter passphrase (empty for no passphrase):
```

Press enter:

```xml
$ Enter same passphrase again:
```

You'll now have two new files in `/root/.ssh/`:

* `id_rsa`
* `id_rsa.pub`

Run the `cat` command to view the contents of the `id_rsa.pub` file.

```xml
$ cat /root/.ssh/id_rsa.pub
```

Copy the contents of `id_rsa.pub`

Add this new key via [Github.com SSH settings](https://github.com/settings/ssh).

Finally, test that the SSH keys work by running this command:

```xml
$ ssh -T git@github.com
```

If all went well, you should see a message like this:

```
Hi susanBuck! You've successfully authenticated, but GitHub does not provide shell access.
```

## Explore your new server

Set up of your new server is complete, so lets take a look around and see what files you have to start with.

First, change into your document root which is located at `/var/www/html/`:

```bash
$ cd /var/www/html
$ ls
```

You should see two files:

* `index.html`
* `info.php`

If you access your site in the browser (via the IP address DigitalOcean gives you), you should see the default contents of `index.html` which looks like this:

<img src='https://s3.amazonaws.com/making-the-internet/vc-digital-ocean-default-index@2x.png' class='' style='max-width:642px; width:100%' alt=''>

## Clone a repository

Now that you've set up your server and established the document root is at `/var/www/html/`, your next step is to clone your `hello-world` repository there.

```bash
$ cd /var/www/html/
$ git clone git@github.com:username/hello-world.git
```

Your directory structure on DigitalOcean should now look like this:

* `/var/www/html`
  * `hello-world/`
  * `index.html`
  * `info.php`

Don't worry right now about previewing the _hello-world_ app in the browser&mdash; we'll cover that in the next note set.

## Moving forward...

Deployment is the process of moving changes from your local server to production.

Once your repository is cloned from Github.com to DigitalOcean, the steps for deploying changes looks like this:

1. SSH in to your Droplet
2. Change directories into your project
3. Run `git pull origin master` to sync any new changes

So a typical workflow might look like this:

1. Sit down for the afternoon to work on your project. Make lots of changes to your local files, testing the changes on your local server.
2. After a couple hours, you're done for the day, so you want to check in your latest changes and update your live server.
3. You stage, commit and push all your local changes to your remote repository at Github.
4. Finally, you SSH into your Droplet and pull the latest changes.

## Tips/Notes

### File location

Apache error and configuration files on DigitalOcean:

* Apache error log: `/var/log/apache2/error.log`
* Apache configuration: `/etc/apache2/httpd.conf`

### Permission denied (publickey)

If you are unable to SSH into your server and receive the following message:

```xml
Permission denied (publickey)
```

...read [these instructions](/servers-and-git/permission-denied-public-key.md).
