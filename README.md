# simple-superset-compose-used-for-embedding

This is a minimal [Superset](https://superset.apache.org/) + Docker Compose set up with superset_config.py . It's intended to simplify the process of trying out Superset.

:warning: **Not suitable for production-used.**

## Usage

1. Determine if you need to make any changes to `superset_config.py` (more info [here](https://superset.apache.org/docs/installation/configuring-superset)). If you ever make any changes to `superset_config.py`, make sure to rebuild the docker images (`docker compose build`).

2. Create a local `.env.` file based on `.env.exp`, and fill out PostgreSQL database connection. 
3. Create schema `superset` in this database.
4. Run `docker compose up`. If it is logging errors about creating a database, the permissions of the new `superset_home` folder may be too restrictive (i.e. `chmod 777 superset_home`).
5. Run the `setup.bat` file, which initializes an account named `admin` with the password `admin`.
6. Visit [http://localhost:8080](http://localhost:8080).
7. Insert data into the database via the exposed port (`5000` by default), or [via the Superset UI](https://superset.apache.org/docs/creating-charts-dashboards/exploring-data/).
8. Try Superset.

## Notes

Apache Superset comes with a default Docker Compose setup but often exclude superset_config.py which makes the entire web-app-embedded seems difficult.