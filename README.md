```
   |   |
   |   +-------------------------+             a1 - Solenoid valve
   |    Rain Water               |             s1 - ultrasonic range finder
   +--------------------------+  |  
                              |  |  
                +--------+    |  |  
                |        |    |  |  
         +----------+  _ |___ |  |_ 
         |controller| |  |    |  | |
         -------+---+ |  s1   |  | |
                |     |       |  | |
--------------+-+-+---+            |
  city water  |a1 |                |
--------------+---+---+            |
                      |    Rain    |
                      |   Barrel   +---+-------------+---------------------
                      |                | 30 psi pump | To drip irrigation
                      |            +---+------+------+---------------------
                      |            |          |
                      +------------+   +------+------+
                                       | WiFi Outlet |
                                       +-------------+
```

It's a rainbarrel get it?

# Building Controller Software

```
git clone http://git.buildroot.net/git/buildroot.git
git@github.com:driechers/Rainbarrel.git
cd buildroot
git checkout 2023.02
make BR2_EXTERNAL=../Rainbarrel/ O=../build_rain raspberrypi4_64_rain_defconfig
cd ../build_rain/
make
```
