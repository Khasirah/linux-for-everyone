# ⚙️ Repository and Installation in Linux🐧
## Know the Concept of Repository
Repository Linux is place where you can update, install, package or application that you use.
Every repository is collection of software hosted in server.
When you use `sudo apt update` or `sudo apt install {appName}`, indirectly you are accessing the repository.

You can view repository that you are using at
```bash
cat /etc/apt/sources.list 
```
will print contents of sources.list as follows.

> deb http://id.archive.ubuntu.com/ubuntu/ jammy universe
> 
> deb http://id.archive.ubuntu.com/ubuntu/ jammy-updates universe

> **explanation**:
> 
> 1. *Archive type* 
>     - **deb** or **deb-src**, indicates the type of archive. **Deb** indicates that the archive contains binary package (deb), the pre-compiled package that we normally use. **Deb-src** indicates source package, which are the original program sources plus the Debian control file (.dsc) and the diff.gz containing the changes needed for packaging the program 
> 2. *Repository URL*
>     - The next entry on the line is a URL to the repository that you want to download the package from.
> 3. *Distribution*
>     - the 'distributin' can be either the release code name / alias (strecth, buster, bullseye, bookworm, sid) or the release class (oldoldstable, oldstable, stable, testing, unstable) respectively. if you mean to be tracking a release class than use the class name, if you want to track a Debian point release, use the code name. **Avoid** using stable in your sources.list as that results in nasty surprises and broken systems when the next release is made; upgrading to a new release should be a deliberate, careful action and editing a file once every two years is not a burden.
>     - For example, if you always want to help the testing release, use 'testing'. If you are tracking bookworm and want to stay with it from testing to end of life, use 'bookworm'.
> 4. *Component*
>     - ***main*** consits of **DFSG**-compliant package, which do not rely on software outside this area to operate. These are the only packages considered part of the Debian distributin.
>     - ***contrib*** package contain DFSG-compliant software, but have dependencies not in main (possibly packaged for Debian in non-free)
>     - ***non-free*** contains software that does not comply with the DFSG

**Example**

## Setup Repository From Internet / Network
### 1. Setup Mirror Keyring
In easy way keyring is needed for authenticate the repository software is real from debian distributin or version of debian distributin.

```bash
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B4FE6ACC0B21F32
mkdir -p /var/data/mirrorkeyring
gpg --no-default-keyring --keyring /var/data/mirrorkeyring/trustedkeys.gpg --import /usr/share/keyrings/ubuntu-archive-keyring.gpg
gpg --no-default-keyring --keyring /var/data/mirrorkeyring/trustedkeys.gpg --import /etc/apt/trusted.gpg
```
### 2. Add the Repository To sources.list
for example:
```bash
deb http://id.archive.ubuntu.com/ubuntu/ jammy universe
```
you can add the repository from other source like usb, ftp, your own server

## Installation Repository From USB
## Use of apt-get install
## Use of apt-get remove
