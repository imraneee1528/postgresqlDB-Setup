# Now Install Postgresql Database Server Ubuntu 20.04:
  
   sudo apt-get install wget ca-certificates

   wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc |   sudo apt-key add -

   sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ focal-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

   sudo  apt update

   sudo  apt list --upgradable
   
   sudo apt -y install  postgresql-13-postgis-3
  
   sudo pg_ctlcluster 13 main start


# Now user and database create and Grant permission:

   sudo -u postgres psql -c "CREATE USER kobo WITH PASSWORD 'user@321';"
   
   sudo -u postgres psql -c "create database xyz;"
  
   sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE xyz to kobo;"
  
   sudo -u postgres psql  -c "CREATE EXTENSION IF NOT EXISTS postgis;" -d xyz
   
   sudo -u postgres psql  -c "CREATE EXTENSION IF NOT EXISTS postgis_topology;" -d xyz

# Now Datbase Store Postgresql

   cd $sql_dump_file_path
 
   sudo su postgres

   psql xyz < xyz.sql 
