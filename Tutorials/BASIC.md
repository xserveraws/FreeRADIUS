# **THIS PROJECT IS STILL IN THE WORKS!**
## **Sources Used**
- **[Documentation](https://freeradius.org/documentation/)**
  - **[Quick Start Guide](https://wiki.freeradius.org/guide/Getting%20Started)**
  - **[FreeRADIUS Techinal Guide PDF](http://networkradius.com/doc/FreeRADIUS%20Technical%20Guide.pdf)**


# **On  Raspbian**

### Step 1: Update Lists 
```
$ sudo apt-get update
```

### Step 2: Install FreeRADIUS
```
$ sudo apt-get install freeradius
```
### Step 3: Install Dependencies
##### Because we are running on Rapsbian, the list is not proper for freeradius, therefore, we have to install the dependencies manually.
### **InstallJava JDK**
```
$ sudo apt-get purge openjdk-8-jre-headless
$ sudo apt-get install openjdk-8-jre-headless
$ sudo apt-get install openjdk-8-jre
```

### Step 4: Edit IP Table for Ports 1812 and 1813
```
$ sudo iptables -A INPUT -p udp --dport 1812 -j ACCEPT
$ sudo iptables -A INPUT -p udp --dport 1813 -j ACCEPT
```

### Step 5: Verify IP Tables
```
$ iptables -L -n | grep 181
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1812
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1813
```

### Step 6: Edit the Clients File
```
$ cd /etc/freeradius/3.0
$ sudo leafpad clients.conf
```
#### Example
![](./Screenshots/CCF01.png)
### Step 7: Edit the Users File
#### Example
```
```## Username Auth Password
testuser Cleartext-Password := "testpassword"
```
