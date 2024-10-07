

!-2			run the second to last command from history
!!			rn the last command from historr
!???			search history for the last ??? command
^original^replacement^	previous command replace parts of command
!!:1			same as !1
history 5		truncates output to the last 5 command
!$			returns the last argument used

!!: Expand to the last command
!n: Expand the command with history number “n”.
!-n: Expand to the command that was “n” number of commands before the current command in history.

Here Docs
	cat > afile.txt << 'END'
	a file contents
	END


Word Designators
After event designators, you can add a colon (:) followed by a word designator to select a portion of the matched command.

It does this by dividing the command into “words”, which are defined as any chunk separated by whitespace. This allows you some interesting opportunities to interact with your command parameters.

The word numbering starts at the initial command as “0”, the first argument as “1”, and continues on from there.

For instance, you could list the contents of a directory and then decide you want to navigate into that same directory. You could do so by running the following operations back to back:

ls /usr/share/common-licenses
cd !!:1
In cases like this where you are operating on the last command, you can shorten this by removing the second ! as well as the colon:

cd !1
This will operate in the same way.

You can refer to the first argument with a caret (^) and the final argument with a dollar sign ($) if that makes sense for your purposes. These are more helpful when using ranges instead of specific numbers. For instance, you have three ways you can get all of the arguments from a previous command into a new command:

!!:1*
!!:1-$
!!:*
The lone * expands to all portions of the command being recalled other than the initial command. Similarly, you can use a number followed by * to mean that everything after the specified word should be included.

Modifiers
Another thing you can do to augment the behavior of the history line you’re recalling is to modify the behavior of the recall to manipulate the text itself. To do this, you can add modifiers after a colon (:) character at the end of an expansion.

For instance, you can chop off the path leading up to a file by using the h modifier (it stands for “head”), which removes the path up until the final slash (/) character. Be aware that this won’t work the way you want it to if you are using this to truncate a directory path and the path ends with a trailing slash.

A common use case for this is if you are modifying a file and realize you’d like to change to the file’s directory to do operations on related files.

For instance, say you run this command to print the contents of an open-source software license to your output:

cat /usr/share/common-licenses/Apache-2.0
After being satisfied that the license suits your needs, you may want to change into the directory where it’s held. You can do this by calling the cd command on the argument chain and chopping off the filename at the end:

cd !!:$:h
If you run pwd, which prints your current working directory, you’ll find that you’ve navigated to the directory included in the previous command:

pwd
Output
/usr/share/common-licenses
Once you’re there, you may want to open that license file again to double check, this time in a pager like less.

To do this, you could perform the reverse of the previous manipulation by chopping off the path and using only the filename with the t modifier, which stands for “tail”. You can search for your last cat operation and use the t flag to pass only the file name:

less !cat:$:t
You could just as easily keep the full absolute path name and this command would work correctly in this instance. However, there may be other times when this isn’t true. For instance, you could be looking at a file nested within a few subdirectories below your current working directory using a relative path and then change to the subdirectory using the “h” modifier. In this case, you wouldn’t be able to rely on the relative path name to reach the file any more.

Another extremely helpful modifier is the r modifier which strips the trailing extension. This could be useful if you are using tar to extract a file and want to change into the resulting directory afterwards. Assuming the directory produced is the same name as the file, you could do something like:

tar xzvf long-project-name.tgz
cd !!:$:r
If your tarball uses the tar.gz extension instead of tgz, you can just pass the modifier twice:

tar xzvf long-project-name.tgz
cd !!:$:r:r
A similar modifier, e, removes everything besides the trailing extension.

If you do not want to execute the command that you are recalling and only want to find it, you can use the p modifier to have bash echo the command instead of executing it.

This is useful if you are unsure of if you’re selecting the correct piece. This not only prints it, but also puts it into your history for further editing if you’d like to modify it.

For instance, imagine you ran a find command on your home directory and then realized that you wanted to run it from the root (/) directory. You could check that you’re making the correct substitutions like this (assuming the original command is associated with the number 119 in your history):

find ~ -name "file1"
!119:0:p / !119:2*:p
Output
find / -name "file1"
If the returned command is correct, you can execute it with the CTRL + P key combination.

You can also make substitutions in your command by using the s/original/new/ syntax.

For instance, you could have accomplished that by typing:

!119:s/~/\//
This will substitute the first instance of the search pattern (~).

You can substitute every match by also passing the g flag with the s. For instance, if you want to create files named file1, file2, and file3, and then want to create directories called dir1, dir2, dir3, you could do this:

touch file1 file2 file3
mkdir !!:*:gs/file/dir/
Of course, it may be more intuitive to just run mkdir dir1 dir2 dir3 in this case. However, as you become comfortable using modifiers and the other bash history expansion tools, you can greatly expand your capabilities and productivity on the command line.

Conclusion

