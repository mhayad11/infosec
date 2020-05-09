Peace, mercy and blessings of God 
today we are going to solve an interesting ctf from nakerah nakerha.com
 our goal is to read root's flag file 
 expolit will be devided into two categories first deserilization attack then ret2libc
 so with all that being said; let's right jump in !!
 first we have that static page 
 looking aroung source code nothing interested there so let's nmap it
 as we see we have some other ports 
 22 ssh we dont have any creds and it seems to be updated
 25 smtp is filtered so we maybe come back to it later
 80 http we already checked it
 so lets visit port 8080 and see what behind the scene
 just another blank page (: i got bored so let's gobuster it :XD
 
 so we have /backup file seems to be interesting let's dump it
 
 after downloading the file it's php code so let's analyze it
 class exCommand{
        public function __destruct(){
            system($this->command);
        }
    }
here it creates a exCommand class and use a magic method __destruct
Destructor is automatically called and allows you to perform some operations before destroying an object which will be our attack vector
class Hello{
        private $name;
        private $role;
        private $isSet;
        public function check(){
           $this->isSet=isset($_COOKIE['name']);
        }
        
        }
    }
here creating class Hekko with some private vars and check function to verify if there's a cookie name name 
public function printHello(){
            if($this->isSet){
                echo "<br >" . $_COOKIE['name']."<br /><br /><br />";
                echo "Hello " . $this->name . "<br>";
                echo "your role is " . $this->role . "\n";
                echo "<br ><br ><br >";
            }else{
                echo "good";
            }
another function printHello fisrt verify if there's a var isSet it will print our cookie, say hello to our cookie name and print our role but if not it will just print good

$obj = unserialize($_COOKIE['name']);
$obj->check();
$obj->printHello();
at last here it create an var, assign it's value to our deserialized_cookie passing it to check and printHello functions

so to stay focus here it's deserilization attack and we need to pass our command to exCommand funcion which has that magic method

 
 
