# erpnext-docker-compose
A simple docker-compose deployment steps to test and run ERPNext on your local machine (or server).

ERPNext is a free and open-source enterprise resource planning (ERP) which is build based on Frappe (python) web-framework. It's a simple yet fully functional ERP that has a lot of potential and features.

I'm using ERPNext to learn about ERP without relying on expensive tools such as SAP or Oracle.

Compared to other Open-Source ERP project, ERPNExt is much simpler and interactive (at least imo).

[Read more about ERPNext](https://github.com/frappe/erpnext)

If you want to read more about ERPNExt Docker Compose, you check it our [here](https://github.com/frappe/frappe_docker)

### Requirements:
- Docker
- Docker compose

### Steps:
1. Change environment parameters on .env file (such as app version and db password)

2. Run docker-compose.yml (add sudo as necessary)
```sh
docker-compose up -d 
```

3. Create a site with the following command:
```sh
# change 127.0.0.1 to your targeted site address (e.g. localhost)
# change mariadb password to your db password (default: 123)
# change 
docker-compose exec backend \
    bench new-site localhost \
        --mariadb-root-password dbpassword \
        --admin-password admin
docker-compose restart backend
```

3. Wait for 5 minutes for ERPNext site to be created before opening browser on port 8081 (you can change the published port on `docker-compose.yml`). 

4. Access your created site address with the following default admin, username: `Administrator`, password: `admin` (or as you set before)

5. Finish your initial setup wizard, and you're ready to explore ERPNext.

PS: This docker config doesn't include proxy (Traefik), since it was meant for testing and learning only. I will add a docker-compose production config later in the future.
