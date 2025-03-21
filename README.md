# Branding UCSB Dataverse

This project is inspired by the [LibraData - Dataverse](https://github.com/shlake/LibraDataHomepage) and [Harvard Dataverse customizations](https://github.com/IQSS/dataverse.harvard.edu/tree/master/customization). Follows the [Branding your Installation](https://guides.dataverse.org/en/6.3/installation/config.html#branding-your-installation) guidelines provided by the Dataverse team for its version 6.3.

## Project Structure

This project has two main components:

- HTML files with custom footer and content homepage.
- Set of assets used in the HTML files.

Assets are organized as usual convention for type (`css`, `js`, `images`).

## Proposed workflow to add branding to a Dataverse instance

1. Files can be located anywhere (except for navbar logo), but it is recommended to clone this repository in the `/var/www/html/` or another directory reachable by the Dataverse instance.
2. Logo must be added using the `admin` API endpoint ([see API docs](https://guides.dataverse.org/en/6.3/api/index.html)).

### Add navbar logo

Move the `assets/imgs/UCSB-dataverse-logo.png` file to `/usr/local/payara6/glassfish/domains/domain1/docroot/logos/navbar`. If `navbar` directory does not exist, create it. 

Add the logo to the Dataverse instance using the following command:

```bash
curl -X PUT -d '/logos/navbar/UCSB-dataverse-logo.png' http://localhost:8080/api/admin/settings/:LogoCustomizationFile
```

To revert to the original logo, use the following command:

```bash
curl -X DELETE http://localhost:8080/api/admin/settings/:LogoCustomizationFile
```

### Custom CSS

Global styles can be defined or overriden using the `assets/css/custom-stylesheet.css` file. 

The file needs to be added to the Dataverse configuration by running the following command:

```bash
curl -X PUT -d '/var/www/html/UCSB-Dataverse-branding/assets/css/custom-stylesheet.css' http://localhost:8080/api/admin/settings/:StyleCustomizationFile
```

### Custom Footer

To set the custom footer, copy the `ucsb-dataverse-footer.html` file to the `/var/www/html/` directory, and run the following command:

```bash
curl -X PUT -d '/var/www/html/UCSB-Dataverse-branding/ucsb-dataverse-footer.html' http://localhost:8080/api/admin/settings/:FooterCustomizationFile
```


