
## My Gists

original PATH  /root/go/bin:/usr/local/go/bin:/root/.local/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


while :

do
 timestamp=`date +%s`
    echo start $timestamp >> result
        tail -n 1 -f result
    echo end $timestamp >> result
#       ((i--))
done

echo "out of loop"

if [ -z ${DISPLAY:=""} ]; then
    DISPLAY=$(who am i)
    DISPLAY=${DISPLAY%%\!*}
    if [ -n "$DISPLAY" ]; then
        export DISPLAY=$DISPLAY:0.0
    else
        export DISPLAY=":0.0"  # fallback
    fi
fi

# small program to stop duplicating path varaibles
case ":$PATH:" in
  *":$new_entry:"*) :;; # already there
  *) PATH="$new_entry:$PATH";; # or PATH="$PATH:$new_entry"
esac

################################################################
to list the contents of a directory containing txt files

find . -type f | sort | while read file; do echo "#### $file" ; cat $file; done | less
or
find -type f -printf "--< %f >----\n" -exec cat {} \; | less
##############################################################
colors super seeded on .env

export CLEAR=$(tput clear)
   export DOWN=$(tput cud1)
   export BLACK=$(tput setaf 0)
   export RED=$(tput setaf 1)
   export GREEN=$(tput setaf 2)
   export YELLOW=$(tput setaf 3)
   export LIME_YELLOW=$(tput setaf 190)
   export POWDER_BLUE=$(tput setaf 153)
   export BLUE=$(tput setaf 4)
   export MAGENTA=$(tput setaf 5)
   export CYAN=$(tput setaf 6)
   export WHITE=$(tput setaf 7)
   export BRIGHT=$(tput bold)
   export NORMAL=$(tput sgr0)
   export BLINK=$(tput blink)
   export UNDERLINE=$(tput smul)

#####################################################################
