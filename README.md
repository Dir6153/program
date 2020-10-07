import java.time.Instant;
import java.time.temporal.ChronoUnit;
import java.util.ArrayList;
public class Users {
  String firstname;
  String lastname;
  int age;
  String email;
  String status;
  Instant timestamp;

  public Users(String name, String lastn,int old,String mail, String stat, Instant time) {
    firstname = name;
    lastname = lastn;
    age = old;
    email = mail;
    status = stat;
    timestamp = time;
  }

  public static void main(String[] args) {
    Instant timestamp = Instant.now();
    ArrayList<Users> userList = new ArrayList<Users>();
    userList.add(new Users("Ion","Musteata",16,"example@example.md","NEW",timestamp));
    userList.add(new Users("Alexei","White",18,"example@example.md","ACTIVE",timestamp));
    userList.add(new Users("Sandu","Alexandru",20,"example@example.md","ACTIVE",timestamp));
    userList.add(new Users("Mihai","Frunza",21,"example@example.md","NEW",timestamp));
    userList.add(new Users("Cristi","Tataru",17,"example@example.md","INACTIVE",timestamp));
    userList.add(new Users("Anatol","Negara",25,"example@example.md","NEW",timestamp));
   // System.out.println(userList.get(0).firstname);
    for(int i = 0;i<userList.size();i++)
    {
        if(userList.get(i).timestamp.isBefore(timestamp.minus(1, ChronoUnit.DAYS)))
        {
            userList.get(i).status = "ACTIVE";
        }
        else if(userList.get(i).timestamp.isBefore(timestamp.minus(31, ChronoUnit.DAYS)))
        {
            userList.get(i).status = "BLOCKED";
        }
    System.out.println(userList.get(i).firstname + " " +  userList.get(i).lastname + " " +  userList.get(i).age + " " +  userList.get(i).email);
    }
    
    
  }
}
