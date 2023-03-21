
#### This is true for Matlab version before Matlab 2019a 

You could change it permanently if you have a copy of Matlab on your local machine (i.e. it's not a server version Matlab).

Locate file: default_getDatatipText.m

in the directory:

\toolbox\matlab\graphics\@graphics\@datacursor

change the line defining number of display digits to higher:

DEFAULT_DIGITS = N;  % Display N digits of x,y position as you wish

Save the update, quit the current Matlab instance, restart, done!
