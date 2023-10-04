# esgf-flow
Multi-facility ESGF analysis via Globus Flows

This repo shows how Globus Flows and Globus Compute can be used to run ESGF workloads. The repo requires you to start a Globus Compute endpoint on a device before you can run the associated notebook. Instructions to setup a Compute endpoint are given below.

To run this notebook you will need to install packages on the client side.:
> `pip install globus-compute-sdk globus-automate-client jupyter`

Note: It is best to use the same Python version across the entire deployment. There are serialization and runtime issues if a function is registered by a client and interpreted by an endpoint with different Python versions. I recommend using python 3.10 across all environments.


## Setting up a Globus Compute endpoint
You can start an endpoint on a remote resource to perform functions on-demand. While endpoints are typically configured to use a batch scheduler to acquire compute nodes to perform tasks, the default configuration just deploys an endpoint to run tasks on the local host. In this local configuration, the endpoint's workers will inherit the python environment the endpoint is started in. Therefore, it is best if you create a python env for the endpoint and install the dependencies.

To configure and start an endpoint you can use the `globus-compute-endpoint` CLI. This will start an endpoint that uses local processes to perform functions:
- `globus-compute-endpoint configure esgf`
- `globus-compute-endpoint start esgf`
  - This will prompt you to login. You need to click the URL, authenticate in the browser, and grant permission. You can then copy the token back into the console to register the endpoint as your user.

An endpoint uuid will then be printed to the console. You can also retrieve this via `globus-compute-endpoint list`.

The endpoint will log information to ~/.globus\_compute/esgf/endpoint.log.



