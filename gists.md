
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
