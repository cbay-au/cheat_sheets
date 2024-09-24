original string
013-01-10 16:21:59,911 SECURE POST Data (examplesite.com):
session%5Busername_or_email%5D=user1%40example.com&session%5Bpassword%5D=examplepass&scribe_log=&redirect_after_login=%2F&authenticity_token=4d27cf47496ec391e055eb78a6f4fa50a5a87e5b

required
Examplesite.com
Username = user1%40example.com
Password = examplepass

solution
awk -F'[ |=]' ' \
 {
   for(i=1;i<=NF;i++)
   {
     if($i ~ /^\(/)
     {
       site=$i; gsub(/\(/,"",site); gsub(/\)/,"",site); gsub(":","",site);
     }
     if($i ~ /username/)
     {
       user=$(i+1); gsub(/\&.*/,"",user);
     }
     if($i ~ /password/)
     {
       pass=$(i+1); gsub(/\&.*/,"",pass);
     }
   }
 }
END {
   printf "%s\nUsername = %s\nPassword = %s\n", site, user, pass;
} ' filename

solution - explanation
awk -F'[ =&]' '                               # set field separator to " ", "=", or "&" single char at which the line is broken into fields
     {for(i=1;i<=NF;i++)                      # check field one to last (NF is no. of fields)
       {if ($i ~ /^\(/)     {site=$i;         # parentheses enclose the site name ( in this case, but this is not necessarily an unambiguous identifier...)
                             gsub(/\(|\)|:/,"",site)}    # gsub removes them
        if ($i ~ /username/) user=$(++i)      # if field contains "username" string, the next field will hold the actual username
        if ($i ~ /password/) pass=$(++i)      # same - ++i is a bit safer than i+1 as it will increment i and thus skip the next field and not evaluate
       }
     }
     END {printf "%s\nUsername = %s\nPassword = %s\n", site, user, pass;}
    ' file
