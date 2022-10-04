# ChiNOG 10 NetDevOps Example

## Requirements

To run this example you need the following:

- Cisco Modeling Labs 2.3 or higher.
- More than one IP address available on the same subnet on which CML is deployed.

## Steps Prior to Starting the Example

1. Edit the file `helper-files/Devbox.yaml` and replace `%%DEV_IP_ADDRESS%%` with an available IP address (and prefix length) on the same subnet on which CML is deployed.
2. Replace `%%DEV_GATEWAY%%` with the default gateway for the CML subnet.
3. Edit `init/virlrc` and change `%%CML_IP_ADDRESS%%` to the IP address of your CML server.
4. Change `%%CML_USERNAME%%` to your CML username.
5. Change `%%CML_PASSWORD%%` to your CML password.
6. Edit `gitlab/setup.sh` and `gitlab/docker-compose.yml` and change `%%DEV_IP_ADDRESS%%` to the same IP address as in step 1 (there are multiple locations).
7. Import the `Devbox.yaml` file into CML.
8. Start the lab in CML.
9. Once the _Devbox_ node is fully started, login to it with the credentials developer / Chinog12345.
10. Clone this repo onto the devbox:

    ```sh
    git clone https://github.com/xorrkaz/chinog-devops
    ```

11. Change directory to `chinog-devops` and run `sh start`.

## Using the Example

After running through the steps above, you will have an Ubuntu server running GitLab within a Docker container.  Within the _developer_ user's home directory on the devbox will be a `cml-iac` directory that contains the example VLAN fabric, Ansible playbook, and test scripts.  You can login to GitLab as root / Chinog12345 at <http://DEV_IP_ADDRESS>.

Add the cml-iac directory as a new repo in GitLab, and then create branches in it to test changes to the VLAN fabric.  See how those changes deployed and tested.  When you merge back to the main branch, the CI/CD pipeline will push to the "production" network that was deployed in CML as well.
