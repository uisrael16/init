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
                  
          step 6: /var/run/resolv.conf
                  this is how i get the complete path of the file that contains the IP address of the DNS server you’re using
                  
          step 7: nslookup slash16.org 8.8.8.8
                  Query an external DNS server on the slash16.org domain name (ie. : google 8.8.8.8)
                  https://quizlet.com/355888462/ft_init-flash-cards/

          step 8: whois slash16.org | grep "Name Server"
                  Find the provider of slash16.org
                  
          step 9: nslookup 42.fr 8.8.8.8
                  Find the external IP of 42.fr
                  https://quizlet.com/355888462/ft_init-flash-cards/
                  
           step 10: traceroute slash16.org
                    Identify the network devices between y our computer and the slash16.org domain
                    avaible from the link below:
                    https://quizlet.com/355888462/ft_init-flash-cards/
                   
           step 11:
                   
           step 12: ipconfig getpacket en1 | grep server_identifier
                    Find the IP that was assigned to you by dhcp server
                    
           step 13:
                    
           step 14: /etc/hosts
                    The /etc/hosts file (or equivalent) configures local host name to IP address mappings typically taking precedence over DNS resolution.                                                                                                                                                                                                          
                    If this file is maliciously modified,
                    it could cause the failure or compromise of security functions requiring name resolution, 
                    such as time synchronization, centralized authentication, and remote system logging.
                    avaible from the link below:
                    https://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap9sec95.html
                   
           step 15:
                    
