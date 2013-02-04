Jett Mail for Elgg
==================
>A robust mail framework for the elgg platform

Jett Mail takes elgg email notifications to the next level, allowing deep integration with email clients.

 - plaintext / html support
 - mail process forking
 - daily digest capability
 - reply to notifications directly from email
 - status updates from email
 - beautiful email template

**Please note this code is in alpha and is currently being developed. Use at your own risk.**

## Server Configuration (Unix-based)
 1. Get your server to forward email to the JettMail terminal plugin script
> Most hosts provide control panel that you can do this easily. If you do not have access to such luxury edit **/etc/aliases** in your favorite editor and add the following line

    elggmail: "|/usr/bin/php -q /full/path/to/elgg/mod/JettMail2/terminal/handle_email.php"
> After this is complete type **newaliases** to rebuild the email aliases.




 2. Create a symbolic link in **/etc/smrsh** so sendmail will know about our script. *If you don't do this then sendmail will spit out the wholly ugly error message Service unavailable, and smrsh: "php" not available for sendmail programs (stat failed).*

    cd /etc/smrsh;
    ln -s /usr/bin/php ./php

 3. Edit **/etc/mail/sendmail.mc** file and add the following

    define(\`LUSER_RELAY',\`local:elggmail')dnl

    > This will tell sendmail to route all messages to the elggmail account
which are destined for a user which doesn't exist on our server.

