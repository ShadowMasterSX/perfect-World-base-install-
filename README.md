# Perfect World Server Installation Guide (v1.1.x - 1.7.8)
*Note: Version 1.8.0 is not supported.*

## Supported Operating Systems

- Debian 12 (64-bit)  
- Ubuntu 25 (64-bit)  

---

## Base System Installation

```sh
dpkg --add-architecture i386
apt update && apt upgrade -y
apt install -y default-jdk apache2 mariadb-server phpmyadmin php-mbstring php-zip php-gd php-json php-curl
apt install -y libstdc++6:i386 libxml2:i386
```

---

## Database Server Setup

```sh
mysql_secure_installation
```

---

## Perfect World Server Setup

1. **Download the required server files** and place them in your `/home` directory.

2. **Edit the following file:**
   ```
   /home/auth/table.xml
   ```

3. **Copy shared object (.so) files:**
   ```sh
   cp /home/gamed/*.so /usr/lib/
   ```

4. **Edit your hosts file:**
   ```sh
   nano /etc/hosts
   ```
   Add the required entries (to be provided).

5. **Set permissions for the home directory:**
   ```sh
   chmod -R 777 /home/*
   ```

6. **Copy game configuration files to `/home/gamed/config/`:**
   - `task.data`
   - `elements.data`
   - `gshopserv.data`
   - (Include version-specific `gshopserv.data` files if needed)

---

## Final Steps

### Reboot the Server

```sh
init 6
```

### Start the Server (Minimal)

```sh
/home/start.sh
```

### Start the Server (All Maps)

```sh
/home/start_max.sh
```

### Stop the Server

```sh
/home/stop.sh
```
