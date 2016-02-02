# Unix-Installation-Scripts

Automation of unix installation can be accomplished with by record and replay operation or using the silent installation script.

The install.sh script allows to install ITX command server, ITX for Launcher , ITX for Integration Servers and ITX for Application programming
in non interactive mode (silent mode).  The scrips is support on all unix based platforms

##Automated Installs - Record & Replay

Options passed to DTXINST:
  -r:  Run the install interactively to record a response file
  -s:  Run the install non-interactively using a prerecorded response file
  -l <LogFile>:  Path to <LogFile> where the results of the install are logged
  
## examples

###Automated Installs – Unix – Recording

./DTXINST -r $MYDIR/install_prompts -l $MYDIR/install_log.wsdtxcs

###Automated Installs – Unix – Playback (Silent Install)

./DTXINST -s $MYDIR/install_prompts -l $MYDIR/install_log.wsdtxcs


##Automated Installs - Silent install

Primary script file is install.sh. The following steps and environment variables need to be set for installing the product

### Step 1 : 

 create a user. ITX installs can not be installed under root.  The below command should be running under the user...
 
### Step 2 : export the following variables

export  VRMFNUM=9000
export  BITTYPE=64
export  BVTDIR= /path/bvt<VRMFNUM>_64
export  TXINSTALLS_CORE=value (possible values are wsdtxcs wsdtxl wsdtxis wsdtxls)
export  TXINSTALLS_DK=none
export  TXINSTALLS_INTERIMFIX=none
export  TXINSTALLS_NOENABLEGPFS=1

Values Definition : 
wsdtxcs - ITX command server
wsdtxl -  ITX Launcher 
wsdtxls  - ITX Launcher Tools
wsdtxis  - ITX Integration Servers


###Step3 create the following directory structure

a) create a directory /path/bvt<VRMFNUM>_64

b) cerate a directory /path/bvt<VRMFNUM>_64/installs

c) copy the install tar image to /path/bvt<VRMFNUM>_64/installs
     example tar image nomencleature wsdtxcs_9000_linux_64.tar
     
d) invoke install.sh
