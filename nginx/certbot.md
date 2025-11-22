

To issue our SSL certificate we want to run the below command and replace the domain name to ours.
```
sudo certbot --nginx -d example.com
```
You may be asked for some details like an email (this doesn't get used publicly).

When directed for a redirect method select the 2 option.

Now our certificate is issued we want to make sure it renews itself. Run the renew command to do so.
```
sudo certbot renew --dry-run
```
