# Little lifesavers

A growing collection of personal hacks for everyday work as a programmer.
Probably not that interesting to others...

## Unix

Disable linebreaks in the terminal emulator:

    printf %b '\033[?7l'

Enable linebreaks again:

    printf %b '\033[?7h'
	
Combine `find` + `grep` on specific files:

    ack println --type scala
	
Replace everything in all files of a specific pattern:

    perl -pi -e 's/<old>/<new>/g;' *.htm
	
Find and replace Unicode characters on the command line:

    LC_CTYPE=C sed 's/\x9c/ae/g' $filename > $outfilename
	
## NVIDIA drivers

Oftentimes, the proprietary NVIDIA drivers fail to load, and oftentimes
the reason is a failed installation, in that accidentally packages for
more than one graphics card were installed that conflict one another.

A complete purge and reinstall is often the way to go:

    apt-get purge nvidia?
	
Then reinstall of the appropriate package:

    apt-get install nvidia-legacy-304xx-driver --no-install-recommends
	
To check what kernel modules are currently available, e.g., to check if a 
purge was successful:

    dpkg -l | grep nvidia | grep 340
	
