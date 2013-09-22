Play nice
---------

How to write reusable apps

use model inheritance and make sure you display your models properly

.. code-block:: python

    def render(obj, template_name, ...):
        template_list = (
          '%s/%s' % (obj._meta, template_name),
          template_name
        )

* ``pip install app_data``
* ``app_data.AppDataField`` - json, register namespaces in json dicts
* ``app_data.MultiForm``, ``app_data`` ...

keep defaults sane
