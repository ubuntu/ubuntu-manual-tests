This will test that you can bootstrap a Juju environment using a MAAS server. In order to test this, you will need to have 2 nodes deployed in maas for juju, plus as many additional nodes as needed for the services you will deploy using juju. 

Bootstrap a new environment using juju pointing to a MAAS server. **NOTE: You can use[this guide for specifics on setting up your environment](<>)**
    Juju is setup properly and bootstrapped
Run juju status
    Can you use juju status and see the available nodes?
This will test that you can successfully deploy to MAAS nodes using Juju 

Bootstrap a new environment using juju pointing to a MAAS server.
Run juju deploy $someservice
    Can you use juju deploy $someservice and have it deployed in the MAAS node?
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result**. 
