Putting Django on the Map
=========================

GeoDjango

- Gareth Lloyd
- @godawful
- glloyd@gmail.com

*"Everything is related to everything else, but near things are more related than distant things."* - Tobler's first law of geography

- GeoDjango gives a nice interface to 2 C++ libs, GDAL and GEOS
- GDAL is used for getting data in and out
- GEOS manipuates spatial data
- KML/GeoJSON
- have model fields for Point and Polygon

Example app - 3sqaure

- install PostGIS http://postgis.net/install , install libs

  - MySQL and SpatiaLite have some support, but much less than Postgres

- add django.contrib.gis to INSTALLED_APPS

.. code-block:: python

    from django.contrib.gis.db import models

    class xyz(models.Model):
        # ...
        location = models.PointField()

        objects = models.GeoManager

Create objects with shapes and points.  Then can do stuff with querysets like:

.. code-block:: python

    Place.objects.filter(locations__within=london.shape).count()
    gps_reading = Point(...)
    Place.objects.all().distance(gps_reading).order_by('distance')
    Place.objects.all().distance(gps_reading).order_by('distance')[0].geojson()

Many operations on shape - spacial relationships stuff.

Play with open datasets:

- ordinance survey
- data.gov.uk
- https://www.sharegeo.ac.uk/
- http://openstreetmap.org
- https://github.com/gareth-lloyd/postcode_latlng - convert PO database from weird format to usable format
