# aws-encryption-sdk-test-vectors

Contained here are known-good static test files for testing compatibility across AWS Encryption
DK clients.

Test files are arranged as so:
```
manifests/ciphertext.manifest
manifests/test_case.manifest
plaintext/<text size name>
ciphertext/<algorithm ID (hex string)>/<text size name>/<frame length (0 == non-framed)>/<test case uuid>
```

The Test Case manifest is provided for informational purposes, and describes all test cases
used to generate all static test data.

The Ciphertext manifest describes all static test cases contained herein.  It provides the
necessary information to set up each test case and locate the associated plaintext and ciphertext
files relative to the `aws_encryption_sdk_resources` root directory.  The implied information
in the ciphertext filepath is not necessary in order to run the test case; the ciphertext
files are broken up simply to ease any necessary human interaction and to guard against possible
filesystem limits.
