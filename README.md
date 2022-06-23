# Lesson3
This repository contains vagrantfile, which configures two virtual machines with debian 11, clones branch "vagrant" from Lesson2 and runs script on every machine, but with differences.  
On first machine, called "host01", script installs and configures MySQL server.  
On second machine, called "host02", script installs and configures PHP and PHPMyAdmin.  
All necessary variables vagrant takes from .env file, which must be in the same directory with vagranfile. You can make your own .env file with renaming env.exaple file to .env. 
