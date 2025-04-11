# Setting Up SQLite in a Codespace

This guide provides step-by-step instructions for setting up and using SQLite in a GitHub Codespace environment, based on the [Datasette Codespaces tutorial](https://datasette.io/tutorials/codespaces).

## Prerequisites

- A GitHub account
- A repository to create a codespace from

## Step 1: Create a Codespace

1. Navigate to your GitHub repository
2. Click the "Code" button
3. Select the "Codespaces" tab
4. Click "Create codespace on main" to start a new codespace
5. Wait for the codespace to initialize

## Step 2: Install SQLite and Related Tools

SQLite should be available by default in most codespace environments, but you can ensure it's installed with:

```bash
# Check if SQLite is installed
sqlite3 --version

# If not installed, you can install it with:
sudo apt-get update && sudo apt-get install -y sqlite3
```

For a better experience with SQLite, install these additional tools:

```bash
# Install pipx for managing Python applications
pip install pipx
pipx ensurepath

# Install sqlite-utils for easier data import and manipulation
pipx install sqlite-utils

# Verify installation
sqlite-utils --version
```

## Step 3: Create and Use a SQLite Database

```bash
# Create a new SQLite database
sqlite3 data.db

# Basic SQLite commands inside the sqlite3 shell:
# Create a table
# CREATE TABLE users (id INTEGER PRIMARY KEY, name TEXT, email TEXT);

# Insert data
# INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com');

# Query data
# SELECT * FROM users;

# Exit SQLite shell
# .exit
```

## Step 4: Import Data from CSV Files

You can import data from CSV files into your SQLite database using sqlite-utils:

```bash
# Download a sample CSV file
wget https://example.com/sample-data.csv

# Import the CSV into a new table called 'sample'
sqlite-utils insert data.db sample sample-data.csv --csv -d

# The --csv option tells sqlite-utils to treat the file as CSV
# The -d option tells it to infer column types from the data
```

## Step 5: Access and Query Your Database

### Using the SQLite CLI

```bash
# Open the database
sqlite3 data.db

# List all tables
.tables

# Show schema for a table
.schema table_name

# Run a query
SELECT * FROM table_name LIMIT 10;

# Export results to CSV
.mode csv
.output results.csv
SELECT * FROM table_name;
.output stdout
```

### Using sqlite-utils

```bash
# List tables
sqlite-utils tables data.db

# View table schema
sqlite-utils schema data.db table_name

# Run a query and output as JSON
sqlite-utils query data.db "SELECT * FROM table_name LIMIT 10" --json
```

## Step 6: Additional SQLite Tools (Optional)

For a more visual interface, you can install and use Datasette:

```bash
# Install Datasette
pipx install datasette

# Install plugin for better Codespaces compatibility
datasette install datasette-codespaces

# Start Datasette with your database
datasette data.db
```

## Step 7: Backing Up Your Database

```bash
# Create a backup copy of your database
sqlite3 data.db .dump > backup.sql

# Restore from backup if needed
sqlite3 new_data.db < backup.sql
```

## Common SQLite Commands Reference

- `.tables` - List all tables
- `.schema table_name` - Show schema for a specific table
- `.mode column` - Set output mode to column
- `.headers on` - Turn headers on
- `.quit` or `.exit` - Exit SQLite CLI

## Tips for SQLite in Codespaces

1. Store your database files in the workspace to ensure they persist between sessions
2. Use version control for your SQL scripts
3. Consider using the `.backup` command for making quick backups
4. Make use of the `.read` command to execute SQL from script files