# License List Data

## To add new custom licenses
1. Initialize custom json file:
```
python update_license_json.py -s SHORTNAME init_custom {exc, lic} 
```
Fill in the short name of the license, and choose between "license"("lic") or "exception"("exc")
2. Go to `json/SHORTNAME/` to see all the fields to fill in:\
   For license:\
   `name`: full name of the license (**required**)\
   `licenseText`: license text\
   `standardLicenseHeader`: license header text\
   `standardLicenseTemplate`: license template (**required**)\
   `standardLicenseHeaderTemplate`: license header template\
   `seeAlso`: reference websites\
   \
   for exceptions:\
   `name`: full name of the license\
   `licenseExceptionText`: exception text\
   `licenseExceptionTemplate`: exception template\
   `seeAlso`: reference websites
   
***Note***: LID only reads `name`, `standardLicenseTemplate`, `licenseExceptionTemplate` and `seeAlso`.
For header templates only `name` and `standardLicenseTemplate` are filled.

3. After filling in all the fields, add custom json file:
```
python update_license_json.py -s SHORTNAME add_custom
```
Or you can update all added custom files at once:
```
python update_license_json.py add_custom
```

## To make adaptions to licenses:
1. Initialize adaption json file:
```
python update_license_json.py -s SHORTNAME init_adaption {exc, lic} [-E -T -H -L -T -S -N]
```
Fill in the short name of the license, and choose between "license"("lic") or "exception"("exc").
Optional arguments are:\
For license:\
   `-L`: `licenseText`: license text\
   `-H`: `standardLicenseHeader`: license header text\
   `-T`: `standardLicenseTemplate`: license template\
   `-N`: `standardLicenseHeaderTemplate`: license header template\
   `-S`: `seeAlso`: reference websites\
You can choose the fields that you want to make adaptions to.
example usage:
```
python update_license_json.py -s SHORTNAME init_adaption lic -LHTNS
```
```
python update_license_json.py -s SHORTNAME init_adaption lic -T
```
   for exceptions:\
   `-E`: `licenseExceptionText`: exception text\
   `-T`: `licenseExceptionTemplate`: exception template\
   `-S`: `seeAlso`: reference websites\
You can choose the fields that you want to make adaptions to.
example usage:
```
python update_license_json.py -s SHORTNAME init_adaption exc -ETS
```
```
python update_license_json.py -s SHORTNAME init_adaption exc -T
```
***Note***: `standardLicenseTemplate` or `licenseExceptionTemplate` will be forced to be initiated.

2. After filling in all the fields, add adaption json file. Include the message for updating:
```
python update_license_json.py -s SHORTNAME add_adaption NOTE
```


Old SPDX README
==========================
Please do not submit pull requests or issues against this generated data repository.  We appreciate all contributions, see [the contributing document](CONTRIBUTING.md) for information on requesting new licenses, reporting issues or contributing pull requests related to this repository.

## Preview of License List Data

An HTML website containing the of the contents of this repository is available at https://spdx.github.io/license-list-data/.

## Data Formats

This repository contains various generated data formats for the [SPDX License List](http://spdx.org/licenses/) including RDFa, HTML, Text, and JSON. The source of the license list which generates these data files can be found at https://github.com/spdx/license-list-XML.  Please note that the format for the license-list-XML repository is internal to the SPDX legal team and is subject to change.

See the file accessingLicenses.md for a description on how to programmatically access the SPDX license list.

The following directories contain the license list in the format specified:

* `html` - Simple HTML format of the files. (*Note:* These pages are not complete and valid HTML files, but simply HTML snippets for the license text.)
* `json` - JSON format for the license list.  The exceptions.json file contains summary information for all exceptions.  The licenses.json file contains summary information for all licenses.  The exceptions directory contains one file per exception named by ID containing all exception details.  The license directory contains one file per license named by ID containing all license details.
* `jsonld` - JSON-LD format for the license list.  The directory contains a file licenses.jsonld which contains all licenses and exceptions as well as single files (one per license or exception) containing data for a single file or exception named by ID.
* `rdfa` - RDFa/HTML format for the license list.  The index.html file contains summary information for all licenses.  The exceptions-index.html file contains summary information for all exceptions.  The directory also contains well as single files (one per license or exception) containing data for a single file or exception named by ID.
* `rdfnt` - RDF NT format for the license list.  The directory contains a file licenses.nt which contains all licenses and exceptions as well as single files (one per license or exception) containing data for a single file or exception named by ID.
* `rdfturtle` - RDF turtle format for the license list.  The directory contains a file licenses.turtle which contains all licenses and exceptions as well as single files (one per license or exception) containing data for a single file or exception named by ID.
* `rdfxml` - RDF/XML format for the license list.  The directory contains a file licenses.rdf which contains all licenses and exceptions as well as single files (one per license or exception) containing data for a single file or exception named by ID.
* `template` - SPDX template files per the license templates specified in the SPDX 2.0 specification appendix.  Deprecated licenses start with "deprecated_".
* `text` - Simple text files.  Deprecated licenses start with "deprecated_".
* `website` - HTML generated for the http://spdx.org/ website.

The file licenses.md is a table of contents for the generated licenses.  The links for the files point to the text for the license.

## Repository Tags and Versions

The repository is tagged with a version `vX.Y.Z` where `vX.Y` matches the version of the [SPDX License List](http://spdx.org/licenses/) and `Z` represents the patch level for any changes to the license list data between releases of the license list.  The repository is tagged whenever the [SPDX License List](http://spdx.org/licenses/) is updated.  Patches may include formatting changes which are not represented in the [license list source XML](https://github.com/spdx/license-list-XML).  

## Reporting Issues

As far as the output *format* or the *generation* of the output files is concerned, any [issues](https://github.com/spdx/LicenseListPublisher/issues) or [pull requests](https://github.com/spdx/LicenseListPublisher/pulls) should be logged at the [License LIst Publisher](http://github.com/spdx/LicenseListPublisher) project.

As far as the *content* of the license information is concerned, see [the license-list-XML contributing document](https://github.com/spdx/license-list-XML/blob/master/CONTRIBUTING.md) for information on how to report issues, request new licenses, or contribute changes.

## License List Data Build Process

The license list data in this repository is automatically built on commits to the master branch of the [license list source](https://github.com/spdx/license-list-XML) by the [Travis-ci script](https://github.com/spdx/license-list-XML/blob/master/.travis.yml).  The commit message generated by the script includes short form of the commit hash from the license list source.  If the license list source has been tagged for release, a tag will also be generated for the license-list-data repository.

The script that publishes the license list data can be found in the .travis directory in the license list source.

The script uses the SPDX tools LicenseRDFaGenerator command to generate the data files.

Source code for the LicenseRDFaGenerator can be found in the [SPDX tools](http://github.com/spdx/tools) repository.  

The main entrypoint for the command is [LicenseRDFaGenerator.java](https://github.com/spdx/LicenseListPublisher/blob/a29a0939a19522f9e3a3b1be6e5f4926c6368435/src/org/spdx/licenselistpublisher/LicenseRDFAGenerator.java#L122)

The basic flow of the program is LicenseRDFaGenerator -> Translate XML to the license objects (including the license text) -> Translate the license into various output files (including the text and template files).

The code that translates the license XML into the license template text is [LicenseXmlHelper.getLicenseTemplate](https://github.com/spdx/tools/blob/4c9054942fd8ba1fb691de8950aeeca3fdf4addf/src/org/spdx/licensexml/LicenseXmlHelper.java#L498) and the code that translates the license XML into text is [LicenseXmlHelper.getLicenseText](https://github.com/spdx/tools/blob/4c9054942fd8ba1fb691de8950aeeca3fdf4addf/src/org/spdx/licensexml/LicenseXmlHelper.java#L523).

## Licensing Information

Other than the README and related documentation, all data in this repository is generated.  The source of the data is the [license list XML Repository](https://github.com/spdx/license-list-XML).  [LicenseListPublisher](https://github.com/spdx/LicenseListPublisher) is the tool used to publish the data.  Please see the respective repositories for licensing information.
