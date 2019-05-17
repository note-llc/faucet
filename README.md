Cryptocurrency-faucet-script
============================

I DO NOT GIVE INSTALLATION SUPPORT.  

Faucet features:

- Supports standard Bitcoin JSON RPC API commands
- Minimum and maximum payouts
- Payment system for staged, timed or direct payouts
- Recaptcha integrated (http://www.google.com/recaptcha/) 
  IMPORTANT: Please note that Recaptcha2 can be set within the config file.
- Proxies filter option
- Promocodes for extra payouts
- Useable with encrypted wallets
- Easy editable template system

Installation:

1. Download or clone this repository
2. Upload the files to your ftp folder
3. Create a database and import faucet.sql
4. Open the config.php and edit all the settings within to suit your needs
5. Create cronjob(s):

If you set "stage_payments" => true and "staged_payment_cron_only" => true (you did that on step 4), you will need to create a cronjob for /cron/run.php and /lib/proxy_filter/cron/tor.php

If you set "stage_payments" => true and "staged_payment_cron_only" => false you just have to create a cronjob for /lib/proxy_filter/cron/tor.php

IMPORTANT: The tor proxy list gets downloaded from https://www.dan.me.uk/torlist/ - He only allows to download once a hour! Please note that you will be banned from the service if you exceed this quota! Create a .htaccess and .htpasswd for the cronjob folder and /lib/proxy_filter/cron/ to secure them.

How to add promo codes:

Go to your database and find the "sf_promo_codes table". Add a new line and set your code, minimum_payout, maximum_payout and uses.

- uses = 0 // Promo code disabled
- uses = -1 // No limit on using this code
- uses = 50 // The code counts down until 0 and works e.g. 50 times
