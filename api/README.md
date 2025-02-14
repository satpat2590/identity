# Dummies Guide to SQLite

This guide will allow you to understand how to use SQLite locally on your machine. 

2024 is a solo entrepreneur's wet dream, and the need to understand proper system design is more of a necessity with each growing day. 
Hopefully this guide will be a decent start for anyone interested in building applications. 

This course will use C/C++ as an interface with SQLite, but will be more focused on showcasing the capabilities of SQLite. 
We will also cover using the SQLite CLI to manage your databases and also how to create backups. 

The "final project" of this guide will be a simple task manager application in which you can use the terminal as a shoddy GUI for you to enter task metadata
which will be used as new entries within tables in the database.


Each part of this guide will be steps for you to follow on your own machine in order to create this application from scratch. 
The goal is to allow you to become familiar with the setup process in a hands-on fashion in order to enhance your understanding. 

This repository will also hold the end result in case you wanted to see the finale before playing. 
In order to understand how to run the application, please go to the section titled: <b>Run the Application</b> 

## Part 1: Basic Installation

First thing you need to do is go on the following site: https://www.sqlite.org/download.html 

This will list out all of the various distributions of SQLite for various operating systems and frameworks.

Since we're using a Linux-based distribution, we can go ahead and install the precompiled binaries for Linux. 
The zip file should have the following naming convention (as of Nov 24, 2024): sqlite-tools-linux-x64-*.zip.

Once downloaded, please go ahead and extract the zip file and store the extracted folder somewhere you remember (I would store it in $HOME for easy access in shell).

After the precompiled binaries are downloaded, you have the installation for the SQLite CLI, which is used to create databases and maintain them. 
However, if you needed to create an application, then you would need to use a programming language (or use SQL as a language!) to create an interface with the database. 

In our case, we will be using the C/C++ language, which will require the implementation (sqlite3.c) and abstraction (sqlite3.h) files. 

Go back to the https://www.sqlite.org/download.html page and then download the <b>sqlite-amalgamation-*.zip</b> file from the <i>Source Code</i> section.
This zip file contains the .c and .h files needed for your own custom C/C++ program. 

Extract it and store it in a secure location, preferably in the same location as the application binaries. 



## Part 2: Set Up Repository

The directory is structured like the following:

sqlite/

- bin/
    - main
- build/
    - *.o
- lib/
    - cJSON.h
    - libcjson.so.1
    - libsqlite3.so
    - sqlite3.c
    - sqlite3.h
- src/
    - api.c
    - api.h
    - sql.c
    - sql.h
- bootup.sql
- build.sh
- main.c
- Makefile
- README.md
- run.sh
- taskm.db


Descriptions of each folder/file: 

The bin/ folder holds the main executable program

The build/ folder contains the intermediary files during program compilation

The lib/ folder contains shared object files used to link to the compiled object files

The src/ folder contains the local source code for the application

The bootup.sql file runs an SQL script which creates the initial state of the database

The build.sh script runs the bootup.sql file and then ensures that the tables are set up properly

The main.c file is the main entryway into the application

The Makefile defines steps to build the main executable

The README.md is what you're currently reading right now!

The run.sh script compiles the main program and then runs it 

The taskm.db database file contains the stored information as defined by bootup.sql

## Project Details

This project is aimed to be a first stab at trying to visualize the progress that species make based on their day-to-day experiences. It is designed
to make users reflect on their identity and carve their own path forward. It also aids in helping users develop better habits in their lives in order to 
lead a more fulfilled life. 

So far, here is the rough outline of the various components that incorporate the backend of this system I liked to call, Identity: 

### Task Manager

The road to being the person you want to be is riddled with informational barriers and lack of experience. In our modern age, we have such
short term attention spans that we barely find time to focus on idealizing our identities, let alone realizing it. 

To fix this, a task manager is needed. There needs to be a way where you get to perform tasks which lead you to developing abilities across different domains 

## Run the Application

There are two ways to run this application. The first is the easiest way, in which you simply run the build script I so graciously provided:

This will set up the sqlite database in your local directory.

```bash
./build.sh
```

This will compile the main application and then run it.

```bash
./run.sh
```

### Manual Steps

From this very repository, please go ahead and run the following commands:

```bash
make
```

This should perform the following steps...
1. Create the shared object file using the sqlite3 C implementation/header files
2. Compile the main.c file into an object file
3. Link the object file into an executable file

The executable file will be named <b><i>main</i></b>

```bash
./main
```

This command will run the main application and allow you to essentially manage your task manager. 

Once you're done using the application, and you feel like you want to make some adjustments, then you certainly can! 

Change the main application or any dependencies as needed (without breaking it, of course!) depending on your use case. 


Then, you can run the following command to clean up the repository by removing the executable and shared object files. 

```bash
make clean
```
