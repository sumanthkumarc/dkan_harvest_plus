# dkan_harvest_plus
DKAN harvest plus module, which helps inharvesting the data endpoints which doesn't follow POD format and endpoint is a direct source of data, without any metadata. Currently supports XML data, harvesting from JSON endpoint should be easy with little extra coding.

More documentation for creating custom Harvest is at http://docs.getdkan.com/en/stable/components/harvest.html#define-a-new-harvest-source-type

This Module does the following:
1. Getting the data from remote source.
2. Converting it into csv file and save it under public://dkan-plus-dataset
   directory with the identifier name as csv filename.
3. This file path is used as "downloadURL" in json schema file and with appropriate
   "mediaType" and "type" values.
4. The schema templates are stored under "dataset_templates" directory in this
   module. This template should have same name as $identifier in the code which
   is machine name of the source with a json extension.
5. This template has all the metadata for creating dataset since only data is
   provided by the endpoint. So new template needs to be created for every dataset.
6. We get this template , replace all placeholders and write back all the json
   data to Harvest cache directory "dkan-harvest-cache".
