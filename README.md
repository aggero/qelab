
# QEMotes
Qemu-Motes (intended pronounciation q-e-motes)
*Emulating small devices in the cloud for investigation*

~qemu frontend for docker on x86_64 hosts for emulating non-x86_64 machines in containers.

### Why not run qemu natively with multiple machines?
* Docker provides additional isolation mechanisms that qemu does not.
* Docker provides a more consistent (ie portable) environment for these qemu machines in which to behave themselves (because often, they don't behave otherwise).
* You can if you want--pull the script out of the machines folder and run them locally!

## Project Structure
:::::::::::::    ::::::::::::::    ::::::::    :::::::::
: D    8022 : -- : Deb-Buster : -- : qemu : -- : ARM32 :
: o H       :    ::::::::::::::    ::::::::    :::::::::
: c o       :
: k s       :    ::::::::::::::    ::::::::    :::::::::::
: e t  8122 : -- : Deb-Buster : -- : qemu : -- : AArch64 :
: r    8180 : -- :            : -- :      : -- :         :
:::::::::::::    ::::::::::::::    ::::::::    :::::::::::

Machines given interconnect IDs available to the host starting with 80xx, 81xx, 82xx, etc.

Typically standard ports open where available:
* 22 for machines with serial ports
* 80 for machines with web-capable services

Script creates project directories for separating unbuilt Dockerfiles from the manipulated Docker Compose files. Projects default to being identified by the creation date and a random 'word' (EG: 210329-Gabera)
