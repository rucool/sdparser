# sdparser: Parse Slocum glider surface dialog files

Deployed Slocum gliders periodically call into the dockserver application to report current status at each surfacing. 
The dialog from each surfacing is written to a text file and contains information such as:

- Glider name
- Current time
- GPS location
- OS errors, warnings and oddities
- Sensor values
- Current waypoint

This python package contains a single class [SurfaceDialogParser](). The parser currently contains 2 parser methods:

1. parse_dialog_file(dialog_file): Parses the dialog_file and returns a list of dictionaries with one entry per parsed
    paragraph.
2. parse_dialog_sensors(dialog_file): Parses the dialog_file and returns a list of dictionaries with one entry per
    sensor.

In addition to these 2 methods, the instance also stores all information on the matches obtained by each regular expression.
The regular expressions can be found in [Regex.py](). This information can be useful for debugging the regular expressions.
See the [API documentation](https://github.com/rucool/sdparser/wiki/API) for details on the class, methods and properties.
We've also included a [Cookbook](https://github.com/rucool/sdparser/wiki/cookbook) containing use cases.

This package was written to parse glider surface dialog files and insert the parsed information into a database of your choosing.
We are using MySQL. The table schema and the MySQL Workbench model are located in [/src/db]().

The resulting database is used to display the [RU-COOL Glider Deployments](https://marine.rutgers.edu/cool/data/gliders/deployments/).
