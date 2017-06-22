# Porthole

Porthole allows you to configure and build simple automated reports.

## Features

* Easily connect to and query a database.
* Convert query results into Excel workbooks
* Send reports by email

## Getting Started

These instructions will allow you to install and configure your environment. You will be running your first reports after just a couple of steps:

1. Install Porthole.
2. Configure your database connection(s) and other important settings.
3. Run setup scripts (requires database write privileges).
4. Start creating reports.

#### Prerequisites

You must have first installed Python 3. It is recommended but not required to use an environment/package manager such as Anaconda. For more information, see the "Install Conda" section below. At the very least, if you are using a Mac, please do NOT use the "system" Python.

You must also have access to a compatible database (at time of writing, this includes MySQL and SQLite) and have CRUD privileges.

### Step 1 - Install Porthole

Use pip to install Porthole from your command prompt or terminal window:

`pip install porthole`

Porthole will be installed, along with its dependencies, using your default Python or whichever virtual environment you have chosen.

### Step 2 - Configuration

From your terminal window, cd to your project directory. From the Python interpreter, execute the following:

```python
import porthole
porthole.new_config()
```

This function will create a new directory called "config" (if it does not already exist), with a file inside called `config.ini`. This is a blank configuration template containing the basic information necessary to get started. The values defined in this file will be used for any connections you'll make to databases, email servers, and to your file system. The values defined in this section are required for correct functionality.

##### Default

This section currently assumes that you are using OS X but will be updated with instructions for Windows, where relevant.

Required values:
* base_file_path - The default location for saving files. You must define the full, absolute path. The path must include a trailing slash.
* query_path - The default location for reading .sql files. This path should be relative to your project directory. THe path must include a trailing slash.
* database - The name of the default database connection you'd like to use. This should be the section title from a database connection (defined in the next section below).

##### Database Connections

Since any database connection requires several parameters, database configs are defined as their own sections. The parameters required in a given section depend on which RDBMS is being defined. The full list of parameters is as follows:

* Section header - e.g. [Production] - This is a descriptive label which will identify a given connection.
* rdbms - The type of RDBMS. Currently supported options include mysql and sqlite.
* host - The connection string or endpoint. For sqlite, this is the database file name.
* port - Usually defaults to 3306 for mysql. Not used for sqlite but set to 0 by default.
* user - The account name for the database user.
* password - The user's password.
* schema - The default schema or database name. You should have permissions to create and update tables in this schema.

### Step 3 - Create database tables

Porthole uses several database tables for report definition and recipient management. It is therefore necessary to create these tables before using the package.

Execute the following:

```python
import porthole
porthole.setup_tables()
```
### Step 4 - Create reports

Coming soon.



##### Setting up your development environment

The information in this section is not necessary for end users. Instead, it is intended to facilitate setup of a development environment for contribution to the Porthole project.s

##### Install Conda

Anaconda (commonly shortened to "Conda") is a widely used environment and package manager for Python. Among other useful features, it makes it easy to setup and install prerequisite Python packages (that is, to setup and configure a development environment). It is recommended to install "Miniconda", which installs only the required packages.

###### OS X Installation Instructions

Full instructions can be found here: [https://conda.io](https://conda.io/docs/install/quick.html).

1. Open a terminal session (go to spotlight, type ‘terminal’ and hit enter).
2. Download the 64-bit bash installer for OS X. Make sure to select Python 3.6.
3. Either move the download to your login directory or cd into your Downloads folder.
  * If you don’t know what your login directory is, type the command `cd` followed by `pwd`.
  * If instead you want to cd into your Downloads folder, use the command `cd ~/Downloads`.
4. Enter the following command: `bash Miniconda3-latest-MacOSX-x86_64.sh`
5. Follow the on-screen instructions. Note that you will have to hold the Enter key in order to scroll through the EULA.
6. The installer will ask you where miniconda should be installed, defaulting to your home directory - type “yes” to confirm.
7. The installer will ask whether you’d like to add your selected directory to your bash profile PATH - type “yes” to confirm.

###### Windows Installation Instructions

Coming soon.


##### Create virtual environment

After Conda is installed, use it to create a virtual environment. The required packages (dependencies) are defined in the environment.yml file. Execute the following command from the terminal:

`conda env create -f environment.yml`

To activate your new environment, execute the following command:

`source activate porthole`

## Running the tests

Execute the command `python run_tests.py`.


## Authors

* **Billy McMonagle** - *Initial work* - [GitHub](https://github.com/speedyturkey)
