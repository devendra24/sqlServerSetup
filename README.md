## SQL Server Docker Setup

This project uses Docker Compose to set up and run a Microsoft SQL Server container. It allows you to quickly deploy SQL Server with persistent data storage, using environment variables stored in a .env file.

### Prerequisites

Ensure you have the following installed:
- Docker (with Docker Compose)
- Git

### Getting Started

Follow these steps to set up and run the SQL Server container.

1. Clone the Repository

Clone this repository to your local machine:

git clone <repository_url>
cd <repository_name>

2. Set Up the .env File

Copy the .env.example file to a new .env file:

cp .env.example .env

Edit the .env file to set the following values:
- MSSQL_SA_PASSWORD: Your desired SA password for SQL Server.
- SQL_HOSTNAME: The hostname for the SQL Server container (optional, but you can set it for better clarity).

Example .env:

MSSQL_SA_PASSWORD=YourStrongPasswordHere
SQL_HOSTNAME=sql1

3. Start the SQL Server Container

Run the following Docker Compose command to start the SQL Server container:

docker-compose up -d

This will:
- Start the SQL Server container in detached mode.
- Bind port 1433 from the container to port 1433 on your host machine.
- Store SQL Server data in the sql_data/ directory on your local machine to persist data between container restarts.

4. Access the SQL Server Container

You can connect to the SQL Server instance using any SQL Server client (e.g., SQL Server Management Studio, Azure Data Studio) with the following credentials:

- Hostname: localhost
- Port: 1433
- Username: sa
- Password: The password you set in the .env file (MSSQL_SA_PASSWORD).

5. Stop the Container

When you're done, you can stop the container by running:

docker-compose down

This will stop and remove the container, but your data in the sql_data/ directory will persist.

### File Structure

.
├── docker-compose.yml       # Docker Compose configuration
├── .env                     # Environment variables (not tracked by Git)
├── .gitignore               # Git ignore file to exclude sensitive files
├── README.md                # This file
└── sql_data/                # Local directory for SQL Server data (not tracked by Git)

### Git Ignore

The .gitignore file ensures that sensitive and unnecessary files (like .env and sql_data/) are not tracked by Git.

### Notes

- Security: Ensure your MSSQL_SA_PASSWORD is strong and not easily guessable.
- Volume Persistence: The sql_data/ folder is mounted as a local volume, so database data is persisted between container restarts.
