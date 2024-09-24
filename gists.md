
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
