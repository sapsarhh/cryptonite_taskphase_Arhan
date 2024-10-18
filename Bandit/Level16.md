# Level 16
In this level there were a number of servers in the range of 31000 and 32000 which could be one of the servers which I had to port into.
firstly I had to check out which server was in the listening state.
didnt know how to do this so I referred to this website https://runcloud.io/blog/check-tcp-port-linux from which I learnt about the netstat command which if used alone gives me a list of open sockets, but if the -a argument is used then boom you also receieve the state of the servers along side with the server port so I used that command.
