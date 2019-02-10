# Little lifesavers

## Unix

Disable linebreaks in the terminal emulator:

    printf %b '\033[?7l'

Enable linebreaks again:

    printf %b '\033[?7h'
	
Combine `find` + `grep` on specific files:

    ack println --type scala
	
Replace everything in all files of a specific pattern:

    perl -pi -e 's/<old>/<new>/g;' *.htm
	
