# Apache2

## Create sites

All available sites are defined in configuration files at `/etc/apache2/sites-available/`.

## Enable or disable site

All enabled sites have a junction link in the directory `/etc/apache2/sites-enabled/` pointing to the folder which was defined in the configuration file in 'sites-available'.

To enable a site:

```text
a2ensite [sitename]
```

To disable a site:

```text
a2dissite [sitename]
```

## Adding listening ports

Add "Listen 8080" to `/etc/apache2/ports.conf`

## Block search engines from reading page

One way to prevent indexing is to add the header X-Robots-Tag = "noindex, nofollow". For Linux Apache, you can do the following:

1. Apache must have the `header` module installed. Install by typing `a2enmod headers` then `service apache2 restart`.
2. Open the config file for your page, usually `/etc/apache2/sites-available/site-name`\) and append the following:

```bash
    <Directory /var/www/[siteroot]>:
        Header append X-Robots-Tag "noindex, nofollow"
```

