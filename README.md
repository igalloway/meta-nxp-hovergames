i.MX Linux Yocto Project BSP for HoverGames
===========================================

Install the `repo` utility
--------------------------

To get the BSP you need to have `repo` installed.

```
$ mkdir ~/bin
$ curl https://storage.googleapis.com/git-repo-downloads/repo  > ~/bin/repo
$ chmod a+x ~/bin/repo
$ PATH=${PATH}:~/bin
```

Download the Yocto Project BSP
------------------------------

```
$ mkdir hovergames
$ cd hovergames
$ repo init -u ssh://bitbucket.sw.nxp.com/imx/imx-manifest -b linux-zeus-internal -m int-5.4.24-2.1.0_hovergames-standard.xml
$ repo sync
```

Create a _new_ build folder
---------------------------

If you want to create a _new_ build folder:

```
$ DISTRO=fsl-imx-xwayland MACHINE=imx8mmnavq source setup-hovergames -b build
```

Use an _existing_ build folder
----------------------------

If you want to build in an _existing_ build folder:

```
$ cd hovergames
$ source setup-environment build
```

Build the image
---------------

There is a regular image and a minimal image. The minimal image excludes
build-on-target support and the weston desktop.

```
$ bitbake imx-image-hovergames
$ bitbake imx-image-hovergames-minimal
```
