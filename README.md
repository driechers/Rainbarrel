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

# Resources

Outlet api docs: https://shelly-api-docs.shelly.cloud/gen1/#shelly-family-overview
Buildroot manual: https://buildroot.org/downloads/manual/manual.html

# Soil Sensor

I got it working by adding to config.txt:
```
dtparam=i2c1=on
dtparam=i2c_arm=on
```

and running:
```
modprobe i2c-bcm2835
modprobe i2c-dev
```

I read moisture with:
```
i2ctransfer -y 1 w2@0x36 0xf 0x10 r2@0x36
```
