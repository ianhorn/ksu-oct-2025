# Microsoft Planetary Computer (MPC)

The Microsoft Planetary Computer [Data Catalog](https://planetarycomputer.microsoft.com/catalog) is an excellent resource for accessing STAC Catalogs.  This page is for introduction only to expose you to more STAC resources.*\*

*\**At the moment, access and download is free, but Microsoft has indicated they will start charging for egress charges ($0.03 - $0.05 per unit).*

If you are part of an organization with access to Azure, checkout [Configure Arcgis for Microsoft Planetary Computer](https://doc.arcgis.com/en/microsoft-planetary-computer/latest/get-started/configure-arcgis-for-microsoft-planetary-computer.htm).

## Set up a STAC Connection to one of the MPC Catalogs

1. On the Data Catalog page, click *Sentinel 1 Level-1 Ground Range Detected (GRD)*.  
2. Under *STAC Collection*, click on the STAC Catalog link.
3. Scroll to the bottom until you see a section that looks like this:

```json
  "stac_version": "1.0.0",
  "msft:group_id": "sentinel-1",
  "msft:container": "s1-grd",
  "stac_extensions": [
    "https://stac-extensions.github.io/sar/v1.0.0/schema.json",
    "https://stac-extensions.github.io/sat/v1.0.0/schema.json",
    "https://stac-extensions.github.io/item-assets/v1.0.0/schema.json",
    "https://stac-extensions.github.io/table/v1.2.0/schema.json"
  ],
  "msft:storage_account": "sentinel1euwest",
  "msft:short_description": "Sentinel-1 Level-1 Ground Range Detected (GRD) products consist of focused SAR data that has been detected, multi-looked and projected to ground range using an Earth ellipsoid model.",
  "msft:region": "westeurope"
```

4. Keep this information handy.  You will need the *"msft:container*, *msft:container", and *msft:region* information.
5. In ArcGIS Pro, create a *Cloud Storage Connection.

| Json Value                  | ACS Value                    |
| --------------------------- | ---------------------------  |
| msft:storage_account        | Access Key ID (Account Name) |
| msft:container              | bucket                       |
| msft:region                 | region                       | 
| Name                        | Value                        |
| ARC_TOKEN_OPTION NAME       | AZURE_STORAGE_SAS_TOKEN      |
| ARC_TOKEN_SERVICE_API       | see #6                       |      
| ARC_DEEP_CRAWL              | NO                           |

6. ARC_TOKEN_SERVICE_API
    - https://planetarycomputer.microsoft.com/api/sas/v1/token/{storage_account}/{container}  

7. Click ok.  If it doesn't work, we can still set up the Connection and Search for items.

## Create STAC Connection

1. Insert a *New STAC Connnection*
2. Call in *MS-Planetary-Computer
3. API URL: `https://planetarycomputer.microsoft.com/api/stac/v1/`
4. Search for data by date and area of interest.

## Leveraging Radiant Earth's Stac-Browser

1. Go to the Stac-browser: `https://radienteaerth.github.io/stac-browser/#`
2. Paste in the STAC Collection URL we got from the Planetary Computer Sentinel-1 GRD overview page.
3. Grab the ID from ArcGIS Pro to use to search for the item.
4. Download