<title>network - ip address</title>

# IP Address

## IP

Every internet-accessible resource–web pages, FTP sites, you name it–has an IP address that serves as the resource’s network address on the internet. These addresses are numeric, in the format 123.123.123.123, and are not particularly easy to remember. Remember the last time you went to 66.220.158.68 to check up on pictures of your niece? No? Of course you don’t, because you typed facebook.com into your web browser instead of 66.220.158.68. A DNS server resolved your human-friendly request of facebook.com into a machine-friendly address that sent you, probably in a hundredth of a second or less, to Facebook.

Wouldn’t it be great if you could set up the same trick for your home network? This is where Dynamic DNS (DDNS) comes into play. It’s easy to for big companies to set up domain names like Facebook.com because the address of their web server is static (once they have the IP address it doesn’t change). Your home IP address is different though. People with residential connections get a dynamically assigned IP address. Your ISP has a big pool of addresses and they share them with everyone on an as-needed-basis.

This makes it pretty difficult to pull the same trick that is so easy for the likes of Coca-Cola because the address you have today isn’t the address you might have next week. Thankfully DDNS providers make it dead simple to assign a memorable name to your home IP address because they update automatically as your IP address changes over time.

## DHCP

The Dynamic Host Configuration Protocol (DHCP) is a network management protocol used on TCP/IP networks whereby a DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so they can communicate with other IP networks.[1] A DHCP server enables computers to request IP addresses and networking parameters automatically from the Internet service provider (ISP), reducing the need for a network administrator or a user to manually assign IP addresses to all network devices.[1] In the absence of a DHCP server, a computer or other device on the network needs to be manually assigned an IP address.

## Virtual Host

The term Virtual Host refers to the practice of running more than one web site (such as company1.example.com and company2.example.com) on a single machine. Virtual hosts can be "IP-based", meaning that you have a different IP address for every web site, or "name-based", meaning that you have multiple names running on each IP address. The fact that they are running on the same physical server is not apparent to the end user.

Apache was one of the first servers to support IP-based virtual hosts right out of the box. Versions 1.1 and later of Apache support both IP-based and name-based virtual hosts (vhosts). The latter variant of virtual hosts is sometimes also called host-based or non-IP virtual hosts.

### Local Setup

#### Step 1. Tell Apache to use the virtual hosts file

First, locate and open `httpd.conf`, your local server's Apache configuration file.

* Mac: `/Applications/MAMP/conf/apache/httpd.conf`

In the `httpd.conf` file, make sure the line including `httpd-vhosts.conf` is _not_ commented out by removing the pound sign from the start of the `Include` (if there is one):

Mac:

```txt
# Virtual hosts
Include /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf
```

#### Step 2. Virtual Host entry

Next, tell Apache on your local server how to handle requests to `http://hello-world.loc` via a Virtual Host entry.

This is done via Apache's `httpd-vhosts.conf` config file.

Mac:

```bash
$ sudo nano /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf
```

At the **bottom** of this file, add your own VirtualHost block:

Mac/MAMP users, yours will look like this:

```txt
<VirtualHost *:80>
    ServerName hello-world.loc
    DocumentRoot /Applications/MAMP/htdocs/hello-world
    <Directory /Applications/MAMP/htdocs/hello-world>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

A breakdown of the key parts of the above VirtualHost blocks:

1. `ServerName` (use `.loc` to distinguish it from the live TLD)
2. `DocumentRoot` (Points to the root of the application/project)
3. `Directory` (same as `DocumentRoot`)

Note, the above VirtualHost blocks assumes you're running on Port 80 (`*:80`). If you're running your local Apache on a different port, make that edit.

#### Step 3. Create a new host

Next, open your computer's `hosts` file. This file can be used to route domains to an IP address of your choice.

* Mac: `/private/etc/hosts`

(Note, there's no extension on this file, it's simply called `hosts`)

The hosts file is protected, so you'll need to open it with administrator privileges.

Mac:

```bash
$ sudo nano /private/etc/hosts
```

At the bottom of your hosts file, add a new host:

```txt
127.0.0.1 hello-world.loc
```

This is telling your computer that whenever you access `http://hello-world.loc` from your computer, it should map to the ip address `127.0.0.1` (the IP address of your local server).

#### Test it

**Restart your local server** and test out your local URL.

Make sure you explicitly type in `http://hello-world.loc` with `http://` at the beginning. If you don't, your browser may try and do a web search for `hello-world.loc` because it does not recognize `.loc` as a domain extension.

#### Fixing `http://localhost`

After you make the above change you'll notice that `http://localhost` no longer works as expected&mdash; instead of pointing the document root you configure in MAMP/XAMPP, it will start pointing to the first VirtualHost block in your `httpd-vhosts.conf` file.

To fix this, you can add a VirtualHost block specifically for `http://localhost`. I recommend having localhost just point to your htdocs folder.

For Mac/MAMP users:

```txt
<VirtualHost *:80>
    ServerName localhost
    DocumentRoot /Applications/MAMP/htdocs
    <Directory /Applications/MAMP/htdocs>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

Don't forget to restart your server after making these changes.

### Summary

To be repeated every time you want to add a new app:

* Add a new `<VirtualHost>` record block in MAMP/Apache's `httpd-vhosts.conf` file.
* Add a new local URL in your computer's `host` file.

Note how it's only Steps 2 and 3 above that need to be repeated for any new apps. Step 1 is a one time deal to get Virtual Hosts working.

### Troubleshooting

If you run into problems, check your Apache error log for clues:

* Mac/MAMP: `/Applications/MAMP/logs/apache_error_log`
