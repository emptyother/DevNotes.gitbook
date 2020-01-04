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

En måte å hindre indeksering på testmaskinene er å legge til headeren X-Robots-Tag = "noindex, nofollow". For Linux Apache så kan en gjøre følgende:

1. Apache må ha header modulen installert. Installer ved å skrive "a2enmod

   headers" også "service apache2 restart".

2. Åpne config-filen for siden \(vanligvis

   `/etc/apache2/sites-available/site-name`\) og legg inn følgende setning under

```text
    <Directory /var/www/[siteroot]>:
        Header append X-Robots-Tag "noindex, nofollow"
```

**For Windows IIS så kan en gjøre følgende:** Under IIS Manager finn "HTTP Response Headers" \(enten i server-rooten eller under en av sitene\) og legg til headeren "X-Robots-Tag" med verdien "noindex, nofollow".

