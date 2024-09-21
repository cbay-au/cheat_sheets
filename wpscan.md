
**Enumeration Modes**

    passive
    aggressive
    mixed
    
**Enumeration Options**

To use WPScan's enumeration capabilities supply the -e option.
The following enumeration options exist:

    vp (Vulnerable plugins)
    ap (All plugins)
    p (Popular plugins)
    vt (Vulnerable themes)
    at (All themes)
    t (Popular themes)
    tt (Timthumbs)
    cb (Config backups)
    dbe (Db exports)
    u (User IDs range. e.g: u1-5)
    m (Media IDs range. e.g m1-15)

If no option is supplied to the -e flag, then the default will be: vp,vt,tt,cb,dbe,u,m

Here we have put together a bunch of common commands that will help you get started quickly.

NOTE: Get your API token from wpscan.com if you also want the vulnerabilities associated with the detected plugin displaying.
Enumerate all plugins with known vulnerabilities

wpscan --url example.com -e vp --plugins-detection mixed --api-token YOUR_TOKEN
Enumerate all plugins in our database (could take a very long time)

wpscan --url example.com -e ap --plugins-detection mixed --api-token YOUR_TOKEN
Password brute force attack

wpscan --url example.com -e u --passwords /path/to/password_file.txt
The remote website is up, but does not seem to be running WordPress

If you get the Scan Aborted: The remote website is up, but does not seem to be running WordPress. error, it means that for some reason WPScan did not think that the site you are trying to scan is actually WordPress. If you think WPScan is wrong, you can supply the --force option to force WPScan to scan the site regardless. You may also need to set other options in this case, such as --wp-content-dir and --wp-plugins-dir.
Redirects

By default WPScan will follow in scope redirects, unless the --ignore-main-redirect option is given.

**Bypassing Simple WAFs**
To bypass some simple WAFs you can try the --random-user-agent option.

To update database to the lastest version, run

wpscan --update
Scan installed plugins

wpscan --url http(s)://your-domain.com --enumerate p
Scan vulnerable plugins

wpscan --url http(s)://your-domain.com --enumerate vp
Scan installed themes

wpscan --url http(s)://your-domain.com --enumerate t
Scan vulnerable themes

wpscan --url http(s)://your-domain.com --enumerate vt
Scan user accounts:

wpscan --url http(s)://your-domain.com --enumerate u
Scan vulnerable timthumb files:

wpscan --url http(s)://your-domain.com --enumerate tt
Please note that scanning other’s websites is illegal. Do it only on your own website.

Using WPVulnDB API
By default, WPScan only tells you if there’s vulnerabilities found, but doesn’t show the details of vulnerabilities. You can get a free API token with 50 daily requests by registering a>
Once you have created account, you can save the API token in a file. Run the following command to create WPScan configruation file.

nano ~/.wpscan/scan.yml
Put the following lines in the file.

cli_options:
    api_token: YOUR_API_TOKEN 
