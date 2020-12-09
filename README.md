# init

network commands:
           step 1: ifconfig -l
                   this command gets the list of network interfaces of the machine
                   without displaying any detail for these interfaces.
                   Only the list of names.The -l flag may be used to list all available 
                   interfaces on the system, with no other additional information.
                   Use of this flag is mutually exclusive with all other flags
                   and commands, except for -d (only list interfaces that are down) 
                   and -u (only list interfaces that are up). link is avaible below:
                   https://superuser.com/questions/203272/list-only-the-device-names-of-all-available-network-interfaces
                  
           step 2a: ifconfig en0 | grep broadcast | awk '{ print $6 }' 
                    this is the original command but I had to change it to 
                    ifconfig en1 | grep broadcast | awk '{ print $6 }' reason being
                    interface en0 does not exist. link is avaible below:
                    https://apple.stackexchange.com/questions/314898/find-ip-address-of-ethernet-printer-when-location-is-home
                    by the way this command Identify broadcast address
                  
          step 2b:
