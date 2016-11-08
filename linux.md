# Linux

Find big directories
    du -a /home | sort -n -r | head -n 5

Truncate a file

    truncate -s 0 stacktrace.log
    or 
    echo "" > stacktrace.log

Find all the processes using pe -ef and dig out the pids and kill them
using xargs kill

    ps -ef | grep node | tr -s ' ' | cut -d ' ' -f 3
    ps -ef | grep node | tr -s ' ' | cut -d ' ' -f 3 | xargs kill -9