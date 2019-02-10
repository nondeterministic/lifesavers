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
	
