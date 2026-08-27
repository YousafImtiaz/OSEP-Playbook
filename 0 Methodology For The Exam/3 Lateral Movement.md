Rely on bloodhound as much as possible to find lateral movement methods. If you have tried everything in bloodhound and you cant find a path then it might be a linux target. 

You can also run bloodhound on every new rooted machine so gain further insight which may help.

Always dump the hash of a user and administrator on the machine and try to pass it to see if it might be reusable across the domain. Make sure to try all domains if there is a trust and also with and without local auth.

Its also worth logging in as a compromised user to quickly check their directories to see if there may be anything of use.

Machine names also give clues as to what might be the privesc vector as well so keep that in mind.