# Frogger-race
Java code simulator a race between 2 frogs with different characteristics

import java.util.Random;
public class FroggerJoe
{
  int maxJumps;
  double maxJumpDistance;
  //double startPosition;
  //double position;
  int jumpAbility;
  double jumpangle;   
  double pointingAngle;
  double frogpositionx;   
  double frogpositiony;
  double distance;
  Random random = new Random();
  
  public FroggerJoe()
  {
    System.out.println(" Frogger");
  }
   
   
  public FroggerJoe(int maxJ, double maxJumpD, double start, int ability)
  {
    System.out.println("ready-to-jump Frogger");
    maxJumps = maxJ;
    maxJumpDistance = maxJumpD;
    double frogpositionx;
    double frogpositiony;
    jumpAbility = ability;
    
    
  }
  
  public String toString()
  {
     String output = "maxJumps " + maxJumps + "\n";
     output += "maxJumpDistance " + maxJumpDistance + "\n";
     output += "startPostition " + maxJumpDistance + "\n";
     output += "frogxposition " + frogpositionx + "\n";
     output += "frogyposition " + frogpositiony + "\n";
     output += "jumpAbility " + jumpAbility + "\n";
     output += "distance " + distance + "\n";
     return output;
  }
  
  public void distFormula()
  {
      distance = Math.sqrt(Math.pow(frogpositionx, 2) + Math.pow(frogpositiony, 2));
  }
  
    public void jump()
  {
      
      jumpangle = -(random.nextInt(180)) - 90;
      //jumpangle = 45;
      frogpositionx = (int)distance;
      frogpositiony = (int)distance;
      double jumpDistance = maxJumpDistance * Math.random();
      //jumpDistance = 1;
      frogpositionx += jumpDistance * Math.cos(jumpangle*Math.PI/180);
      frogpositiony += jumpDistance * Math.sin(jumpangle*Math.PI/180);
      pointingAngle += jumpangle;   // good
  }
  
  public void race()
  {
    while (maxJumps > 0)
    {
      maxJumps--;
      jump();  
    }
     distFormula(); 
  }
 
   public boolean winner(FroggerJoe other)
  {   
            
   if (distance > other.distance)    
   {
     System.out.println("Frog 1 wins!");
     return true;
   }
   
  
   
   else
   {     
     System.out.println("Frog 2 wins!");
     return false;
   }
     
  } 
  
  public static void main(String [] args)
  {
    FroggerJoe frog1 = new FroggerJoe(11, 4, 1, 3);
    FroggerJoe frog2 = new FroggerJoe(10, 5, 0, 1);
    frog1.race();
    frog2.race();
    System.out.println("frog1 " + frog1);    
    System.out.println("frog2 " + frog2);    
    frog1.winner(frog2);
  }
}
