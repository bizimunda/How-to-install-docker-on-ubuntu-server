## How to install docker on Ubuntu 22.4

1 First update

    sudo apt update

2 Next, install a few prerequisite packages which let apt use packages over HTTPS:

    sudo apt install apt-transport-https ca-certificates curl software-properties-common

3 Then add the GPG key for the official Docker repository to your system:

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

4 mAdd the Docker repository to APT sources:

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

5 Update your existing list of packages again for the addition to be recognized:

    sudo apt update

6 Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:

    apt-cache policy docker-ce


7 You’ll see output like this, although the version number for Docker may be different:

    docker-ce:
    Installed: (none)
    Candidate: 5:20.10.14~3-0~ubuntu-jammy
    Version table:
     5:20.10.14~3-0~ubuntu-jammy 500
        500 https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
     5:20.10.13~3-0~ubuntu-jammy 500
        500 https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages

8 Finally, install Docker:

    sudo apt install docker-ce

9 Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:

    sudo systemctl status docker

10 If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:

    sudo usermod -aG docker ${USER}

11 To apply the new group membership, log out of the server and back in, or type the following:

    su - ${USER}

12 Confirm that your user is now added to the docker group by typing:

    groups


