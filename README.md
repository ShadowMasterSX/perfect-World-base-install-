# Perfect World Server Installation Guide (v1.1.x - 1.7.8)
*Note: Version 1.8.0 is not supported.*

## Supported Operating Systems

- Debian 12 (64-bit)  
- Ubuntu 25 (64-bit)  

---

## Base System Installation

```sh
dpkg --add-architecture i386
```
```sh 
apt update && apt upgrade -y
```
```sh
apt install -y default-jdk apache2 mariadb-server libmariadb-dev-compat libmariadb-dev php-mbstring php-zip php-gd php-json php-curl libstdc++6:i386 libxml2:i386
```

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
sudo bash -c 'cat << EOF >> /etc/hosts
127.0.0.1 gm_server
127.0.0.1 PW-Server
127.0.0.1 aumanager
127.0.0.1 manager
127.0.0.1 link1
127.0.0.1 link2
127.0.0.1 link3
127.0.0.1 link4
127.0.0.1 game1
127.0.0.1 game2
127.0.0.1 delivery
127.0.0.1 database
127.0.0.1 backup
127.0.0.1 auth
127.0.0.1 audb
127.0.0.1 gmserver
127.0.0.1 LogServer
127.0.0.1 AUDATA
EOF'
```

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
