---
layout: project
title: "LabWars"
permalink: /projects/labwars
github: https://github.com/dmfrodrigues/feup-lcom
---

<div class="scroll" markdown="1">
![labwars](https://raw.githubusercontent.com/dmfrodrigues/feup-lcom/master/proj/doc/report/images/main_menu.png)
![campaign](https://raw.githubusercontent.com/dmfrodrigues/feup-lcom/master/proj/doc/report/images/campaign01.png)
![zombies](https://raw.githubusercontent.com/dmfrodrigues/feup-lcom/master/proj/doc/report/images/zombies01.png)
![chat](https://raw.githubusercontent.com/dmfrodrigues/feup-lcom/master/proj/doc/report/images/chat02_01.png)
</div>

A top-down shooter supporting chat, zombie and multiplayer modes.
Targets the Minix operating system, which means almost everything was implemented starting from system-level I/O interfaces.

- **Environment:** Minix
- **Tools:** C low-level calls
- **Concepts:** OS interfaces

Implemented by [Diogo Rodrigues](https://github.com/dmfrodrigues) and [Telmo Baptista](https://github.com/telmooo).  

## Installing

First of all, this will only run on Minix. Besides, because it was developed as part of a university subject, the lecturers provided a special Minix OS image with custom libraries to make it easier to handle the low-level calls. This means you will need to use a special Minix image. Said Minix image is available at the [subject page](https://web.fe.up.pt/~pfs/aulas/lcom2019/index.html), more specifically [here](https://drive.google.com/open?id=1Sm7Y6thfLqpRxYSR4V_S14bK-5E7FHgN). If you fail to find the image, please use [this link from my Dropbox](https://www.dropbox.com/s/vg3xzthl3otp1mr/MINIX-LCOM.zip?dl=1).

You will have to compile from source. We advise you to set up a shared folder, clone the [repository](https://github.com/dmfrodrigues/feup-lcom.git) to that shared folder, and only then go into Minix. In Minix, run the following commands to setup and compile the project:
```sh
cd proj
./setup.sh
make
```

To run it, use
```sh
cd proj
lcom_run proj
```
