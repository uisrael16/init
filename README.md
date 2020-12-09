# init

network commands:
           step 1: ifconfig -l
                   this command gets the list of network interfaces of the machine
                   without displaying any detail for these interfaces.
                   Only the list of names.The -l flag may be used to list all available 
                   interfaces on the system, with no other additional information.
                   Use of this flag is mutually exclusive with all other flags
                   and commands, except for -d (only list interfaces that are down) 
                   and -u (only list interfaces that are up). available from the link below:
                   https://superuser.com/questions/203272/list-only-the-device-names-of-all-available-network-interfaces
                  
           step 2a: ifconfig en0 | grep broadcast | awk '{ print $6 }' 
                    this is the original command but I had to change it to 
                    ifconfig en1 | grep broadcast | awk '{ print $6 }' reason being
                    interface en0 does not exist. available from the link below:
                    https://apple.stackexchange.com/questions/314898/find-ip-address-of-ethernet-printer-when-location-is-home
                    by the way this command Identify broadcast address
                  
           step 2b: arp -a
                     by typing arp -a you display all the MAC addresses of recently resolved IP addresses.
                    https://networkencyclopedia.com/arp-command/
                    
           step 3: ifconfig en1 | awk '/ether/{print $2}'
                   ifconfig en1 gets the interface details for wifi,
                   the mac is on a line starting with ether, 
                   and is the second word on that line so:
                   available from the link below:
                   https://stackoverflow.com/questions/28685156/shell-command-for-getting-mac-address-in-os-x
                   
          step 4: route -n get default | grep 'gateway' | awk '{print $2}'
                  this is how I managed to get default gateway in Mac OSX
                  available from the link below:
                  https://stackoverflow.com/questions/6782658/how-to-get-default-gateway-in-mac-osx
                  
          step 5: dig slash16.org | grep SERVER | awk '{print $3}' | awk -F '[()]' '{print $2}' 
                  Identify the IP address of the DNS that responds to the following url: slash16.org
