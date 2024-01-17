This project is made to determine if each line in lessons has violations based on docs daycycle, weather, minimums, and students.
The codes i write are in the auditor folder.

This project writes and reads JSON and CSV docs about students' flights information. 

For Utils.py:
The function :read_json, for example, is used to return the contents read from the CSV file filename, and to write the given data out as a CSV file filename. At the same time, there are also functions in the module to handle data in the JSON file. JSON file, such as function :read_json, which returns the contents read from the JSON file filename, and returns the datetime object for the given timestamp. 
The main purpose of this module is to convert the data stored in JSON and CSV files to Python.
Among them, in auditor are all the modules and functions I wrote, and applications, KITH 2017-2019 are Datasets.

For module pilot.py:
The module pilots.py contains functions for determining the qualifications of each student pilot in the flight school. This file will work with the data from two different files: students.csv and minimums.csv. Module determining pilot certifications, ratings, and endorsements. The restrictions that we place on a pilot depend on their qualifications.  
There are three ways to think about a pilot. (1) Certifications. These are what licenses a pilot has.  We also use these to classify where the student is in the licensing process.
(2) Ratings. These are extra add-ons that a pilot can add to a license. For this project,
the only rating is Instrument Rating, which allows a pilot to fly through adverse weather
using only instruments.
(3) Endorsements. These are permission to fly certain types of planes solo. Advanced 
allows a pilot to fly a plane with retractable landing gear. Multiengine allows a pilot
to fly a plane with more than one engine.

The module violations.py is used to check for violations in the flight course. The main violation handled by this module is the violation of weather restrictions. Weather restrictions define the minimum conditions under which a pilot is allowed to fly. So, if a pilot has a minimum altitude of 2000 feet and a cloud cover of 1500 feet, then the pilot should not fly. To understand the minimum weather conditions, I had to integrate three different files: daycycle.json (sunrise and sunset), weather.json (hourly weather observations at the airport), and minimums.csv (minimum weather conditions for the school set by agreement with the insurance agency). The data is compared to the minimums to determine if visibility exists. The entire module takes each of the parameters in the data (wind, visibility, and finally the function that violates the maximum or minimum value and finds it. It is worth mentioning that in this minimum, the function list_weather_violations analyzes a complete dataset to find weather violations. The function is given a catalog and that's it. The function then reads the files daycycle.json, students.csv, minimums.csv, weather.json, and lessons.csv to create a list of weather violations. The function will return a table listing all courses that violate the minimum weather conditions. Each row in the table is course data, plus one additional column. This column will contain the result of the function get_weather_violation (provided it is not an empty string). This is explained in more detail in the specification of list_weather_violations.


For app.py:
This module allows me to run the whole modules as an application and this module that validates the flight school's records. This is the primary module that does all of the work. It loads the files, loops through the lessons, and researches for any takeoffs that violates issurance requirements.
Function: discover_violations searches the dataset directory for any flight lessons the violation regulations. This function will call list_weather_violations() to get the list of weather violations. If list_endorsment_violations (optional) is completed, it will call that too, as well as list_inspection_violations.  It will concatenate all of these 2d lists into a single 2d list of violations (so a flight may be listed more than once for each of the three types of violations).
Function execute: This is the main application function, and Executes the application or prints an error message if executed incorrectly. The arguments to the application (EXCLUDING the application name) are provided to the list args. This list should contain either 1 or 2 elements.  If there is one element, it should be the name of the data set folder or the value '--test'.  If there are two elements, the first should be the data set folder and the second should be the name of a CSV file (for output of the results). 

Contribution guidelines
This project is only for graduate school admission purpose.
