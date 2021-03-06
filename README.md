## AWS CDK & AWS Cloudformation unit testing framework for Python

### Description
AWS CDK is natively implemented using [AWS JSII](https://github.com/aws/jsii) which is a mainly implemented in TypeScript and using the JSII, it is translated into language specific packages for Python or any other supported language. AWS CDK provides a comprehensive unit testing package in Typescript only that is not exported to Python or any other language.
This repo extends an open source unit testing framework for Python [expects](https://expects.readthedocs.io/en/stable/) by adding a custom matcher to match against AWS Cloudforation json templates generated by AWS CDK or even natively implemented. You can simply expect the CloudFormation template to contain/not contain specific resources, parameters or outputs with specific configuration properties.

### Business use case
This unit testing framework allows you to implement unit ot integration testing on your AWS infrastructure before they are created. This allows AWS customers and partners to write their own professional unit test cases using native Python tools.
This package integrates natively with pytest and can be integrated with any other existing testing suites.

### How to use?
This package is published into PyPi and can be used as a dependency into your AWS CDK project or any other python package as a regular dependency into your setup.py or requirements file. The package is to be installed using pip.

### Code Example
```python
    def test_kms_key_rotation_enabled(self):
        """
            Test KMS key rotation is enabled for all KMS keys
        """
        expect(self.cfn_template).to(have_resource("AWS::KMS::Key", {
            "EnableKeyRotation": True
        }))
```

### Prerequisites
Python 3.6+
