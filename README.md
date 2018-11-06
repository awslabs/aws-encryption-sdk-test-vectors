# Test Vectors for the AWS Encryption SDK

This repository contains known-good static test files for testing compatibility of AWS Encryption
SDK clients.

# Test Vectors

The `vectors` directory contains known good test vectors for full message decryption (the test vectors 
for full message encryption will be added at a later stage). These test vectors are contained in zip files 
that identify the aws encryption sdk client and version that were used to generate them. 

The zip filename format used is `IMPLEMENTATION-VERSION.zip`. For example, a zip file containing test vectors
 generated using version 1.3.5 of the AWS Encryption SDK for Python would be named:  `python-1.3.5.zip`.

The contents of `vectors/full-message-decrypt` conform to the new test vector framework specification.
(NOTE: This README will be updated with links to the specification once it is made avaialable) and were generated 
from this [implementation](https://github.com/aws/aws-encryption-sdk-python/tree/master/test_vector_handlers) in 
the AWS Encryption SDK for Python.

The contents of each zip file follow the below format:
```
plaintext/<text size name>
ciphertext/<test case uuid>
<manifests>
```

# Legacy Vectors

The following vectors are recognized to be used for legacy purporses only:
- python-1.3.0.zip

Note: The legacy vectors donot follow the new test vector framework specification and instead follows the old 
format/rules for the test vector manifests. 

The contents of the python-1.3.0.zip file follow the below format:
```
manifests/ciphertext.manifest
manifests/test_case.manifest
plaintext/<text size name>
ciphertext/<algorithm ID (hex string)>/<text size name>/<frame length (0 == non-framed)>/<test case uuid>
```

The `Ciphertext manifest` describes all static test cases contained in the zip.  It provides
the necessary information to set up each test case and locate the associated plaintext and
ciphertext files relative to the zip file root.  The implied information in the ciphertext
filepath is not necessary in order to run the test case. The ciphertext files are broken
up simply to ease any necessary human interaction and to guard against possible filesystem
limits.

The `Test Case manifest` is provided for informational purposes and describes all test cases
used to generate the included test vectors.
