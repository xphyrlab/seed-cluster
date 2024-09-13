# Installing Seed Cluster in OpenShift
## This guide outlines the steps for installing a Seed Cluster in OpenShift.


### Directory Structure:
 1. Create a directory named openshift under your desired installation directory. This will hold your machine configuration file.
 2. Inside the openshift directory, create a machine configuration file (e.g., machine-config.yaml).
    Ensure the file specifies a partition named varlibcontainers with at least 522,240 MiB size and starting after 133,120 MiB (accounting for a 120 GB pre-allocated space).

    Note: On the virtual machine (VM) where you plan to install the Seed Cluster, set the disk.enableUUID parameter to TRUE.

Image Creation:

    Create Installation Image:

        Open a terminal and navigate to the install directory which contains the following files:
        a) agent-config.yaml
        b) install-config.yaml
        c) openshift/machine-config.yaml
        Run the following command to create the installation:
        openshift-install --dir install agent create image


Generating a seed image with the Lifecycle Agent
    1. Set the AUTHFILE environment variable to point to the location of your container authentication file:
    $export AUTHFILE=${XDG_RUNTIME_DIR}/containers/auth.json
    
    2. Set the rhcosLiveIso environment variable:
    $export rhcosLiveIso="https://mirror.openshift.com/pub/openshift-v4/amd64/dependencies/rhcos/latest/rhcos-live.x86_64.iso"
