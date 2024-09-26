- ### check the volume of a file
`du -hs <path to the file>`

- ### check the ip
`hostname -I`

- ### access logs
`docker logs -f --tail 1200 <container_name>`

- ### check the health of the macine
`sudo pip3 install bpytop`
`bpytop`

- ### Use of grep command
1. You can use `grep` to search for multiple patterns in a directory by using the `-e` option followed by the pattern you want to search for. Here's an example of how to use `grep` to search for two different values in a directory, This command will search for the occurrences of "pattern1" and "pattern2" in all the files in the directory '/path/to/directory'.
	```
	grep -e "pattern1" -e "pattern2" /path/to/directory/*
	```

2. You can also use the `-E` option to specify that the patterns are regular expressions.
	This command will search for the occurrences of "pattern1" or "pattern2" in all the files in the directory '/path/to/directory' using regular expression pattern.
	```
	grep -E 'pattern1|pattern2' /path/to/directory/*
	```

3. Alternatively you can use `-f` option which allow you to read patterns from a file, one per line, with each line specifying a separate search pattern.
	```
	grep -f /path/to/pattern-file /path/to/directory/*
	```
