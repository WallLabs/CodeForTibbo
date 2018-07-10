# Tibbo C Base-64 Encoder
This library was constructed to allow for Base-64 encoding on Tibbo C devices.
Whilst the EM2000W was the targeted device for this library, the library will function on any Tibbo emebedded module.

# Set-up
In order to use this library in your own projects, first clone this repo or download <base64.tc> and <base64.th>

- Now that you have the source files, add them to your project directory.

- Once added, make sure to place a reference to the header with <#include "base64.th";>, usually in <global.th>.

# Use Instructions
A given string named foo can be encoded or decoded using the respective library function below:
	
	base64_encode(foo);
	base64_decode(foo);

# Example
The following code showcases a typical use case for this library:
	
Code:

	sys.debugprint("Encoded output: " + base64_encode("Man1") + "\n");
	sys.debugprint("Decoded output: " + base64_decode("TWFuMQ==") + "\n");

Output:

	EM2000W>> Encoded output: TWFuMQ==
	EM2000W>> Decoded output: Man1