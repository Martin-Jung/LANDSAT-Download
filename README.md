LANDSAT-Download
================

The routine provided below enables to automatically download LANDSAT data, using the current (April 2014) version of EarthExplorer system. This new version (2014-08-19) does not need to provide the exact overpass date anymore, I have reused here an idea of my colleague Michel Le Page at CESBIO (Thanks Michel !), though implemented differently.

It works for LANDSAT 8 and LANDSAT 5&7, but needs that the data be already online. It was true for LANDSAT 8 until September 2014, but after that date, to avoid increasing the on-line data volume indefinitly, USGS started to clean out older data to replace them by the new ones. It is also the caser for the older LANDSAT satellites. Depending on the products you need, it may be necessary to first order for the production of L1T products, on the earthexplorer site http://earthexplorer.usgs.gov. And of course, you will need to have an account and password on the Earthexplorer website, to store it on the usgs.txt file. If you have an access through a proxy, you might try the -p option. it works through CNES proxy at least but was only tested there.

This routine may be used in two ways :

- by providing the WRS-2 coordinates of the LANDSAT scene, for instance, (198,030) for Toulouse (-s option), , the start date (-d option), and the end date (-f option). If the end date is not provided, it is replaced by today's date by default. Example:

`       download_landsat_scene.py -o scene -d 20130127  -s 181025 -u usgs.txt -p proxy.txt --output /mnt/data/LANDSAT8/N0/`

- by providing a list of products to download, as in the example below:

`       python download_landsat_scene.py -o liste -l list2_landsat8.txt -u usgs.txt --output /mnt/data/LANDSAT8/N0/`

with a file list2_landsat8.txt as provide below (the landsat references must exist in the earthexplorer catalog) :

`       Tunisie LC81910352013160LGN00`

`       Tunisie LC81910362013160LGN00`

The usgs.txt must contain your username and password on the same line separated by a blank.

If you do not use the --ouput option, the files will be downloaded to /tmp/Landsat (provided it exists)

To see all the options : 
`       download_landsat_scene.py -h`

The nice progress bar was provided by Jake Brinkmann ( Thanks Jake !)

