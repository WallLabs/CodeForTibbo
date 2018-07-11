# Tibbo C JSON Parser
This library was constructed to allow for easier JSON use on Tibbo C devices.
Whilst the EM2000W was the targeted device for this library, the library will function on any Tibbo emebedded module.

# Set-up
In order to use this library in your own projects, first clone this repo or download <json.tc> and <json.th>

- Now that you have the source files, add them to your project directory.

- Once added, make sure to place a reference to the header with <#include "json.th";>, usually in <global.th>.

# Use Instructions
This library only supports the generation of the <type>:<value> JSON markup, object notation must be added manually.

To serialize a given type value pair into a string run the following command:
	
	json_stringify(type, value);
	json_stringfy_float("floatTest", 1.34, 3);

To deserialize a value from a JSON string run the following command:

	string value = extract_json_parameter(jsonString, type);

# Example
The following code showcases a typical use case for this library:
	
Code:

	sys.debugprint("String: " + json_stringify("stringTest", "Some Text") + "\n");
	sys.debugprint("Number: " + json_stringify_number("numberTest", 1) + "\n");
	sys.debugprint("Float: " + json_stringify_float("floatTest", 1.54, 3) + "\n");
	sys.debugprint("Boolean: " + json_stringify_bool("boolTest", true) + "\n");
	
	string TEST_JSON_STRING = "{\"stringTest\":\"test123\"}";
	string TEST_JSON_NUMBER = "{\"numberTest\":101}";

	sys.debugprint("\n");
	sys.debugprint("Extract String from " + TEST_JSON_STRING + ": " + extract_json_parameter(TEST_JSON_STRING, "stringTest") + "\n");
	sys.debugprint("Extract Number " + TEST_JSON_NUMBER + ": " + extract_json_parameter(TEST_JSON_NUMBER, "numberTest") + "\n");

Output:

	EM2000W>> String: "stringTest":"Some Text"
	EM2000W>> Number: "numberTest":1
	EM2000W>> Float: "floatTest":1.54
	EM2000W>> Boolean: "boolTest":1

	EM2000W>> Extract String from {"stringTest":"test123"}: test123
	EM2000W>> Extract Number {"numberTest":101}: 101

# Arrays
To handle array types first extract the array value using the previous commands. 
Once you have the json string representation of the array use the following commands to access the members:
	
	string value = extract_json_array_member(json_array, index);

# Example
The following code showcases an example of using json arrays in this library:

Code:
	
	string TEST_JSON_ARRAY = "[1,2]";
	string TEST_JSON_ARRAY_SINGLE = "[SINGLE]";	
	
	sys.debugprint("Extract Array " + TEST_JSON_ARRAY + ":\n\t" 
		+ extract_json_array_member(TEST_JSON_ARRAY, 0) + "\n\t" + extract_json_array_member(TEST_JSON_ARRAY, 1) + "\n");
	sys.debugprint("Extract Single From Array " + TEST_JSON_ARRAY_SINGLE + ": " + extract_json_array_member(TEST_JSON_ARRAY_SINGLE, 0) + "\n");

Output:

	EM2000W>> Extract Array [1,2]:
	EM2000W>> 	1
	EM2000W>> 	2
	EM2000W>> Extract Single From Array [SINGLE]: SINGLE	