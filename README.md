# crudgen
Create, read, update, delete page generator for MySQL databases.
# It's actually easy
One file and one form to fill out. All dependancies are included, you don't need anything else.
# How do I use it?
##### 1. Copy index.php somewhere on your server that has write access. 
##### 2. Fill out the form
And that's it! You'll have a full featured C.R.U.D interface for everything in your database.
# How does it work?
Once your details have been grabbed, the script will access your information_schema table, which contains names and constraints on your tables and columns. For each table it finds, it builds a view page that uses the DataTables plugin, with inline editing, add and delete functionality. 
# What's with all the obfuscated stuff?
In order to shove everything into one file it was necessary to obfuscate it so PHP can write the files. The DateTimePicker that is used doesn't have a CDN, and there are several other files (datatables-editable and a few CSS) that required modification before they could be used properly. 
# So exactly what files are written?
In order of appearence in the index,
- jquery.datetimepicker.js
  - Taken from http://xdsoft.net/jqplugins/datetimepicker/. It isn't on a CDN so we need to recreate it locally.
- cleanup.php
  - Script to delete unnecessary files after installation.
- __globals.php
  - Contains mysqli connection data and global variables
- __generator.php
  - Builds the actual functionality and files for each table encountered. So for every table you have, this will create FOUR files. A display file [tablename].php, with create-[tablename].php, edit-[tablename].php and delete-[tablename].php.
- __layout.php
  - Contains the layout of each function page, has a bunch of inline scripts for initialising the plugins on each page.
