# Branding UCSB Dataverse

This project is inspired by the [LibraData - Dataverse](https://github.com/shlake/LibraDataHomepage) and [Harvard Dataverse customizations](https://github.com/IQSS/dataverse.harvard.edu/tree/master/customization). Follows the [Branding your Installation](https://guides.dataverse.org/en/6.3/installation/config.html#branding-your-installation) guidelines provided by the Dataverse team for its version 6.3.

## Project Structure

This project has two main components:

- HTML files with custom footer and content homepage.
- Set of assets used in the HTML files.

Assets are organized as usual convention for type (`css`, `js`, `images`).

## Proposed workflow to add branding to a Dataverse instance

1. Files can be located anywhere, but it is recommended to clone this repository in the `/var/www/html/` or a non-root `/home/foo/` directory.
2. Logo must be added using the `admin` API endpoint ([see API docs](https://guides.dataverse.org/en/6.3/api/index.html)).

```bash
curl -X PUT -H "X-Dataverse-key: $API_TOKEN" -d 'assets/imgs/UCSB-Dataverse-logo-transparent.png' http://localhost:8080/api/admin/settings/:LogoCustomizationFile
```

To revert to the original logo, use the following command:

```bash
curl -X DELETE -H "X-Dataverse-key: $API_TOKEN" http://localhost:8080/api/admin/settings/:LogoCustomizationFile
```





