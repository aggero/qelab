# qelab
lab equipment built on qemu machines (pronounced K-Lab)

\<*in development*\>

### Why not run qemu natively with multiple machines?
* Docker provides additional isolation mechanisms that qemu does not.
* Docker provides a more consistent (ie portable) environment for these qemu machines in which to behave themselves (because often, they don't behave otherwise).
* You can if you want--pull the script out of the machines folder and run them locally!

## Project Structure
```
:::::::::::::::    ::::::::::::::    ::::::::    :::::::::::
: x D    8022 : -- : Deb-Buster : -- : qemu : -- :  ARM32  :
: 8 o H       :    ::::::::::::::    ::::::::    :::::::::::
: 6 c o       :
: _ k s       :    ::::::::::::::    ::::::::    :::::::::::
: 6 e t  8122 : -- : Deb-Buster : -- : qemu : -- : AArch64 :
: 4 r    8180 : -- :            : -- :      : -- :         :
:::::::::::::::    ::::::::::::::    ::::::::    :::::::::::
```

Machines given interconnect IDs available to the host starting with 80xx, 81xx, 82xx, etc.

Typically standard ports open where available:
* 22 for machines with serial ports
* 80 for machines with web-capable services

Script creates project directories for separating unbuilt Dockerfiles from the manipulated Docker Compose files. Projects default to being identified by the creation date and a random 'word' (EG: 210329-Gabera)

## Current Machine Support
arm32-raspi2 headless machine providing SSH access
```
~/qelab$ ./build -p a32rpi arm32-raspi2 arm32-raspi2
Did not find workspace. Creating projects/.
Creating project: a32rpi
Machines (2):
        arm32-raspi2
        arm32-raspi2
~/qelab$ ./start a32rpi
Starting project: a32rpi/
Creating network "a32rpi_default" with the default driver
Creating a32rpi_arm32-raspi2_81_1 ... done
Creating a32rpi_arm32-raspi2_80_1 ... done
~/qelab$ projects/a32rpi/arm32-raspi2_80.ssh
Warning: Permanently added '[localhost]:8022' (ECDSA) to the list of known hosts.
pi@localhost's password: 
(...)
pi@raspberrypi:~ $ exit
~/qelab$ projects/a32rpi/arm32-raspi2_81.ssh
Warning: Permanently added '[localhost]:8122' (ECDSA) to the list of known hosts.
pi@localhost's password: 
(...)
pi@raspberrypi:~ $
```
