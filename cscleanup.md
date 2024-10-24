


Ref:- https://stackoverflow.com/questions/11793942/delete-lines-before-and-after-a-match-in-bash-with-sed-or-awk
# delete two lines either side of a pattern match from a file full of transactions. 
# Ie. find the match then delete two lines before it, then delete two lines after it and then delete the match.
awk '/Scan Aborted/ {print NR-2 "," NR+2 "d"}' input_filename \
    | sed -f - input_filename > output_filename
=========================================================================

remove  ^[[37m and ^[[0m from test file
sed -e 's/\x1b\[[0-9;]*m//g'
explanation:-

    \x1b (or \x1B) is the escape special character
    (GNU sed does not support alternatives \e and \033)
    \[ is the second character of the escape sequence
    [0-9;]* is the color value(s) regex
    m is the last character of the escape sequence
==============================================================================

combining the above two gives:-
awk '/Scan Aborted/ {print NR-2 "," NR+2 "d"}' input_filename | sed -f - input_filename | sed -e 's/\x1b\[[0-9;]*m//g' > output_filename

# gthis is now incorporated in function wpcleanup

==============================================================================

Ref:- https://unix.stackexchange.com/questions/180663/how-to-select-first-occurrence-between-two-patterns-including-them
sed -n '/P1/,/P2/p; /P2/q'

    -n suppresses the default printing, and you print lines between the matching address ranges using the p command.
    Normally this would match both the sections, so you quit (q) when the first P2 matches.

This will fail if a P2 comes before P1. To handle that case, try:

sed -n '/P1/,/P2/{p; /P2/q}'

cat delete_output3 | sed -n '/TARGET NAME/,/Elapsed time/{p; /Elapsed time/q}' > delete9

========================================================================================
(?<=    (?<!

cat delete1 | sed 's/TARGET.*$/&\n==============/' >> delete2

sed -n "/TARGET NAME/,/$1/{p; /$1/q}"

sed 'H;/{\TARGET$/h;/^}/x;/{\n.*PATTERN/!d'

sed 'H;/TARGET/h;/^Elapsed/x;/TARGET\n.*6.2.2/!d'

sed '/6.2.2.*\n/p;//g;/TARGET/,/Elapsed}/H;//x;D'
