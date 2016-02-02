# Unix-Installation-Scripts

Automation of Unix installation can be accomplished with record and replay operation or by using the silent installation script.

The install.sh script allows a user to install ITX with Command Server, ITX with Launcher, ITX for Integration Servers, ITX for Application Programming and ITX Launcher Studio in non-interactive mode (silent mode). The script is supported on all Unix-based platforms

##Automated Installs - Record & Replay

Options passed to DTXINST

    -r  - Run the install interactively to record a response file
  
    -s  - Run the install non-interactively using a prerecorded response file
  
    -l  - Path to LogFile where the results of the install are logged
  
  
## examples

###Automated Installs – Unix – Recording

./DTXINST -r $MYDIR/install_prompts -l $MYDIR/install_log.wsdtxcs

###Automated Installs – Unix – Playback (Silent Install)

./DTXINST -s $MYDIR/install_prompts -l $MYDIR/install_log.wsdtxcs


##Automated Installs - Silent install

Primary script file is install.sh. The following steps and environment variables need to be set for installing the product

### Step 1 : 

 create a user. ITX installs can not be installed under root.  The below commands should be running under the user...
 
### Step 2 : export the following variables


export  VRMFNUM=9000

export  BITTYPE=64

export  BVTDIR= /path/bvt9000_64

export TXINSTALLS_CORE=value (possible values are wsdtxcs wsdtxl wsdtxis wsdtxapi wsdtxls)

export  TXINSTALLS_DK=none

export  TXINSTALLS_INTERIMFIX=none

export  TXINSTALLS_NOENABLEGPFS=1


Values Definition : 

wsdtxcs - ITX with Command Server

wsdtxl - ITX with Launcher

wsdtxis - ITX for Integration Servers

wsdtxapi - ITX for Application Programming

wsdtxls - ITX Launcher Studio


###Step3 create the following directory structure

a) create a directory /path/bvt9000_64

b) cerate a directory /path/bvt9000_64/installs

c) copy the install tar image to /path/bvt9000_64/installs

     Example tar image nomenclature: wsdtxcs_9000_linux_64.tar
     
d) invoke install.sh
