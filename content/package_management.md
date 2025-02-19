### Package Management Systems
The core parts of a Linux distribution and most of its add-on software are installed via the Package Management System. Each package contains the files and other instructions needed to make one software component work on the system. Packages can depend on each other. There are two broad families of package managers: those based on **dpkg** and those which use **rpm** as their low-level package manager. The two systems are incompatible, but provide the same features at a broad level.

**Package Management Systems**

| High Level Tool | Low Level Tool | Family     |
|-----------------|----------------|------------|
| apt             | dpkg           | Debian     |
| zypper          | rpm            | SUSE       |
| yum             | rpm            | Red Hat    |
| pacman          | pacman         | Arch Linux |

Both package management systems provide two tool levels: a low-level tool (such as ``dpkg`` or ``rpm``), takes care of the details of unpacking individual packages, running scripts, getting the software installed correctly, while a high-level tool (such as ``apt-get``, ``yum``, or ``zypper``) works with groups of packages, downloads packages from the vendor, and figures out dependencies. Most of the time users need work only with the high-level tool, which will take care of calling the low-level tool as needed. Dependency tracking is a particularly important feature of the high-level tool, as it handles the details of finding and installing each dependency for you. Be careful, however, as installing a single package could result in many dozens or even hundreds of dependent packages being installed.

| Operation                                                  | RPM                | Debian                 | Arch Linux        |
|------------------------------------------------------------|--------------------|------------------------|-------------------|
| Install a package                                          | rpm –i foo.rpm     | dpkg --install foo.deb | pacman -U foo.pkg |
| Install a package with dependencies from repository        | yum install foo    | apt-get install foo    | pacman -S foo     |
| Remove a package                                           | rpm –e foo.rpm     | dpkg --remove foo.deb  | pacman -R foo     |
| Remove a package and dependencies using repository         | yum remove foo     | apt-get remove foo     | pacman -R foo     |
| Update package to a newer version                          | rpm –U foo.rpm     | dpkg --install foo.deb | pacman -U foo     |
| Update package using repository and resolving dependencies | yum update foo     | apt-get upgrade foo    | pacman -S foo     |
| Update entire system                                       | yum update         | apt-get dist-upgrade   | pacman -Syu       |
| Show all installed packages                                | yum list installed | dpkg --list            | pacman -Q         |
| Get information about an installed package including files | rpm –qil foo       | dpkg --listfiles foo   | pacman -Ql foo    |
| Show available package with "foo" in name                  | yum list foo       | apt-cache search foo   | pacman -Ss foo    |
| Show all available packages                                | yum list           | apt-cache dumpavail    | pacman -Sl        |
| Show packages a file belong to                             | rpm –qf file       | dpkg --search file     | pacman -Qo file   |
