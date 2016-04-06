############################################
# required software and packages
############################################
metagenemark
make the metagenemark executive by 
sudo chmod+x MetaGeneMark_linux64/gmhmmp

hmmer 3.1b
add hmmer to system PATH

ppsp
download ppsp database for it

R 3.0.1 or higher
R packages
seqinr
genoPlotR
plyr
foreach
doParallel
grDevices

#############################################
# installation
#############################################

#### hmmer 3.1b installation ####
# download the suitable source from ftp at:
http://hmmer.janelia.org/software

# Briefly, to compile from source:
   % tar zxf hmmer-3.1b2.tar.gz
   % cd hmmer-3.1b2
   % ./configure
   % make
   % make check
#NOTICE: by default, hmmscan should be automatically add to system PATH after installation

##### ppsp installation #####
###install packages
#add below line to /etc/apt/souce.list
deb http://ftp.hk.debian.org/debian squeeze main 

sudo apt-get update && sudo apt-get install sqlite3 libsqlite3-dev libsqlite3-ruby1.8 p7zip-full vim ruby1.8 rubygems

sudo gem install ruby-sqlite3 
#NOTICE:the sqlite3-ruby listed in the tutorial.pdf cannot be installed by apt-get install, but could use this one instead

### install PPSP locally now 
sudo mkdir /mnt/host_shared
sudo mkdir /apps/pps
sudo ln -s /apps /mnt/apps
cp ./pps/* /apps/pps

# add permission to the folders created
sudo chmod -R 777 /mnt/hot_shared
sudo chmod -R 777 /apps/pps

#Setup PATH and PYTHONPATH:
export PATH=/apps/pps/sys:/apps/pps/tools:$PATH	  
export PYTHONPATH=/apps/pps/sys:/apps/pps/tools/ppsplus:/apps/pps/tools/ppsplus/algbioi/:$PYTHONPATH	
# update software and download database
update -s
update -t 
update -r NCBI20140513	# this database 58G after decompression

#### R and packages installation ####
#install R in Ubuntu
sudo apt-get install r-base r-base-dev
#in R
install.packages("seqinr","plyr","genoPlotR","foreach","doParallel","grDevices")

######## usage #######################
#put contig.arg.sh in the same directory with MetaGeneMark_linux64/ , pps/ and database/

#run with only one argument like:
bash contig.arg.sh contig.fa 1>contig.fa.log

# NOTICE: "sh contig.arg.sh contig.fa" may not work, make sure use the bash promt not sh




