If you encounter the following error when uploading files:


This means NGINX is blocking the upload because the client body (file upload) exceeds the configured size limit. Follow the steps below to fix it.

---

## Step 1 — Open the Configuration File

By default, the main NGINX configuration file is located at:

```
/etc/nginx/nginx.conf
```

Open this file using the **nano** command:

```bash
sudo nano /etc/nginx/nginx.conf
```
client_max_body_size 1000M;

![Alt Text](https://weblutions.com/i/NWXTc.png)

This increases the upload size limit to 1 GB (measured in megabytes).

If you want to disable the limit entirely, use this line instead:
```
client_max_body_size 0;
```
Make sure this line is inside the http { ... } block  placing it elsewhere will cause errors.

Once added, save and close the file:

In nano, press CTRL + O to save, then CTRL + X to exit.

Step 3 — Verify Configuration Syntax

Before restarting NGINX, always test your configuration to ensure it’s valid:
```
sudo nginx -t
```

Expected output:
```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
Step 4 — Restart NGINX

Once the syntax check passes, restart NGINX to apply your changes:
```
sudo systemctl restart nginx
```

(Older guides may mention service nginx restart, but systemctl is the correct method for Ubuntu 24.04.)

Step 5 — Verify the Fix

Try your upload again. If it succeeds without error, the new upload limit is active.

Summary
Action	Command or Setting
Edit config	sudo nano /etc/nginx/nginx.conf
Increase limit	client_max_body_size 1000M;
Disable limit	client_max_body_size 0;
Test syntax	sudo nginx -t
Restart service	sudo systemctl restart nginx
