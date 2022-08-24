# Dockerized Metabase with PostgreSQL backend

> Then Jesus went about all cities and villages, teaching in their synagogues, preaching the gospel of the kingdom, healing every sickness and every disease among the people. 
>
> But when He saw the multitudes, He was moved with compassion for them, because they were weary and scattered, like sheep having no shepherd. 
>
> -- [Matthew 9: 35-36](https://www.bible.com/en-GB/bible/114/MAT.9.NKJV)


[Metabase](https://www.metabase.com/) is an open-source java-based software that enables users to analyse data from a range of data sources including relational databases (e.g. Postgresql, MySQL etc.), NoSql databases etc.

It can be quite helpful when one has a data science question that could easily be answered by data analysis.

By default, it stores application-specific data e.g. users, stored queries, configurations etc. on an H2 database on the same file system where it is installed.

However, it is difficult to retrieve this data once the application crushes (which it might do if you write a wrong sql query for it to run on your data). It is therefore usually better to have the application save the data in a postgreSQL database such that it recovers its original state after any crush.

## Technology used

| Technology | Usage |
| --- | --- |
|[Docker](https://docs.docker.com/) | metabase and postgres run in different Docker containers|
|[Docker Compose](https://docs.docker.com/compose/) | Docker compose netwroks the different Docker containers to allow them  work together as dependent services |
|[Metabase](https://www.metabase.com/)| SQL based Analysis and Visualization program for any database |
| [Postgres](https://www.postgresql.org/) | A database engine that stores relational data in a persistent way |

## How to run

This assumes the local machine is running on Ubuntu

1. Ensure docker is installed. If it is not installed, install it. Here are [the instructions](https://docs.docker.com/install/linux/docker-ce/ubuntu/).
2. Ensure docker compose is installed on your system. If it is not installed, install it. Here are [the instructions](https://docs.docker.com/compose/install/).
3. Clone this git repository

    ```bash
      git clone https://github.com/Tinitto/compose-postgres-metabase.git
    ```

4. Enter the compose-postgres-metabase folder

    ```bash
      cd compose-postgres-metabase
    ```

5. Convert ```config/metabase_database.env.example``` to ```config/metabase_database.env```.
6. Update the environment variables ```MB_DB_PASS```, ```MB_DB_HOST```, ```MB_ENCRYPTION_SECRET_KEY``` and save.

    ```bash
    ENV MB_DB_PASS=<put_here_the_password_for_the_metabase_user>
    # Make sure the firewall at the database server allows connections to port 54320
    ENV MB_DB_HOST=<put here the IP address for the Metabase database server e.g. 00.000.000.00>
    ENV MB_ENCRYPTION_SECRET_KEY=<Add a random string here as the secret>
    ```

7. Convert ```config/postgres.env.example``` to ```config/postgres.env```.
8. Update the environment variables ```POSTGRES_PASSWORD```, ```METABASE_PASSWORD``` and save.

    ```bash
    # Add the password for the postgres user
    POSTGRES_PASSWORD=<put here the_password for the postgres user>
    # Add the password for the metabase user
    METABASE_PASSWORD=<put here the password for the metabase user>
    ```

9. Start the docker compose services

    ```bash
      sudo docker-compose up -d
    ```

10. Set up your metabase instance by visiting the [local metabase start URL](http://localhost:3000)
If you are on a server, use ```http://<server IP>:3000```.

## Service - Port Mappings

| Service | Port |
| --- | --- |
| Metabase | 3000 |
| Postgres | 54320 |

## Acknowledgement

Some of the configuration was learnt from the [Beyond Jupyter](https://github.com/jgoerner/beyond-jupyter) talk by [Joshua Gorner](https://github.com/jgoerner)
