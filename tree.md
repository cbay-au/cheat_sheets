
## list only the directories
tree -d target_directory 

## list hidden files
tree -a target_directory

## get the path for each file
tree -f directory

tree -f "$(pwd)"

## list on levle depth
tree -L Level
tree -L 2

##  file permissions  (-h for better readability)
tree -p TargetDirectory
tree -ph MUSIC

## show you the size of each file and directory
tree --df -h TargetDirectory

## To sort files based on first modification, use the -c
## use the -D option to get the date and time of modification:
tree -cD TargetDirectory

### To sort files based on last modification, use the -cr will reverse -c option
tree -cDr TargetDirectory
