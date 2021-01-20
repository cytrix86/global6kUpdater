#!/bin/sh
# A quick way to create Update Media for the Bombardier Global 6000
red=`tput setaf 1`
reset=`tput sgr0`

# Provide Help
if [ ${#@} -ne 0 ] && [ "${@#"--help"}" = "" ]; then
  printf -- '...help...\n';
  exit 0;
fi;


while getopts s:d: flag 
do
    case "${flag}" in
        s) source=${OPTARG};;
        d) destination=${OPTARG};;
    esac
done
printf -- '\033[33m WARNING: hmm \033[0m\n';
# If -d is *required*
if [ ! -d "$source" ]; then
    echo 'Option -s missing or designates non-directory' >&2
    exit 1
fi
if [ ! -d "$destination" ]; then
    echo 'Option -d missing or designates non-directory' >&2
    exit 1
fi

echo "${red}This process will delete all Data in the destination \n$destination \nAre you sure you want to continue?${reset}"
select yn in "Yes" "No"; do
    case $yn in
        Yes ) break;;
        No ) exit;;
    esac
done

echo "Cleaning destination"
# Turn on dotglob (set) #
shopt -s dotglob
rm -rf $destination/*
# Turn off dotglob (unset) #
shopt -u dotglob

echo "Scanning for Files"
for filepath in $source/*.exe; do
    filename=$(basename -- "$filepath")
    echo "Unpacking $filename"
    filename="${filename%.*}"
    unzip $filepath -d $destination/$filename | pv -l -s $(unzip -Z -1 $filepath | wc -l) > /dev/null;
done