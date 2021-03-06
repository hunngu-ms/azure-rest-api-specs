## Python

These settings apply only when `--python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.
Use `--python-mode=update` if you already have a setup.py and just want to update the code itself.

``` yaml $(python) && !$(track2)
python-mode: create
python:
  azure-arm: true
  license-header: MICROSOFT_MIT_NO_VERSION
  payload-flattening-threshold: 2
  namespace: azure.mgmt.recoveryservicesbackup
  package-name: azure-mgmt-recoveryservicesbackup
  package-version: 0.1.0
  clear-output-folder: true
```
``` yaml $(python) && $(track2)
python-mode: create
azure-arm: true
license-header: MICROSOFT_MIT_NO_VERSION
namespace: azure.mgmt.recoveryservicesbackup
package-name: azure-mgmt-recoveryservicesbackup
package-version: 1.0.0b1
clear-output-folder: true
modelerfour:
  lenient-model-deduplication: true
```
``` yaml $(python) && $(python-mode) == 'update' && !$(track2)
python:
  no-namespace-folders: true
  output-folder: $(python-sdks-folder)/recoveryservices/azure-mgmt-recoveryservicesbackup/azure/mgmt/recoveryservicesbackup
```
``` yaml $(python) && $(python-mode) == 'create' && !$(track2)
python:
  basic-setup-py: true
  output-folder: $(python-sdks-folder)/recoveryservices/azure-mgmt-recoveryservicesbackup
```
``` yaml $(python) && $(python-mode) == 'update' && $(track2)
no-namespace-folders: true
output-folder: $(python-sdks-folder)/recoveryservices/azure-mgmt-recoveryservicesbackup/azure/mgmt/recoveryservicesbackup
```
``` yaml $(python) && $(python-mode) == 'create' && $(track2)
basic-setup-py: true
output-folder: $(python-sdks-folder)/recoveryservices/azure-mgmt-recoveryservicesbackup
```

``` yaml $(python) && $(track2)
directive:
  - from: swagger-document
    where: $.definitions.ProtectionIntent
    transform: >
        $['required'] = ['protectionIntentItemType'];
  - from: swagger-document
    where: $.definitions.FeatureSupportRequest
    transform: >
        $['required'] = ['featureType'];


```