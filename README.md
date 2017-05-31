PHPCap
==========================================================================

Developers: [Jim Mullen](https://github.com/mullen2); [Andy Arenson](https://github.com/aarenson), aarenson@iu.edu

PHPCap is a PHP API (Application Programming Interface) for REDCap.

PHPCap makes accessing REDCap from a PHP program easier by providing:
* a high-level interface
* improved error checking

REDCap is a web application for building and managing online surveys and databases. For information about REDCap, please see http://www.project-redcap.org.

Requirements
--------------------------
To use PHPCap, you need to have:
* A computer with PHP 5.6 or later installed, and PHP needs to have cURL and OpenSSL enabled.
* An account on a REDCap site.
* API token(s) for the project(s) you want to access. API tokens need to be requested within the REDCap system.


Example
--------------------------

```php
<?php
require_once('PHPCap/autoloader.php');

use IU\PHPCap\RedCapProject;

$apiUrl = 'https://redcap.someplace.edu/api/';
$apiToken  = '273424CC67263B849E41CCD2134F37C3';

$project = new RedCapProject($apiUrl, $apiToken);

# Print the project title
$projectInfo = $project->exportProjectInfo();
print "project title: ".$projectInfo['project_title']."\n";

# Print the first and last names for all records
$records = $project->exportRecords();
foreach ($records as $record) {
    print $record['first_name']." ".$record['last_name']."\n";
}
?>
```


Documentation
----------------------------
For more information, see the PHPCap documentation: https://aarenson.github.io/PHPCap/



