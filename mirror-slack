#!/bin/bash

declare -a failures

verify_dir() {
	for pkg in $1/*.t?z
	do
		echo -n "Checking $pkg ... "
		if gpg --verify ${pkg}.asc $pkg &>/dev/null
		then
			echo -e "\033[32mOK\033[0m"
		else
			echo -e "\033[31mNOT OK\033[0m"
			failures[${#failures[*]}]=$pkg
		fi
	done
}

for dir in a ap d e f k kde kdei l n t tcl x xap xfce y
do
	verify_dir "$1/$dir"
done

if [ ${#failures[*]} -gt 0 ]
then
	echo; echo "----------------";
	echo "Failures:"
	for fail in ${failures[@]}
	do
		echo $fail
	done
fi

