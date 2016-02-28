
import java.util.*;
public class MemoryGame
{
  static Scanner input=new Scanner(System.in);
 
  public static void main(String[] args)
  {
	System.out.println("Type in the coordinates of the card you select.");
	
	
	Layout();
	
  }
  public static void Layout()
	{
		int cards [][] = new int [4][4];
		boolean check[][] = new boolean[4][4];
		
		cards = Shuffle();
		
		System.out.println("  1 2 3 4 ");
		System.out.println("___________");
		
		for(int i=0; i<4; ++i)
		{
			System.out.print(" " + (i+1));
			for(int j=0; j<4; ++j)
			{
				System.out.print("*");
				check[i][j] = false;	
			}
			System.out.println();
		}
		System.out.println();
		BeginGame(check,cards);
		
	}
	
  public static int[][] Shuffle()
	{
		int initial[] = {1, 2, 3, 4, 5, 6, 7, 8};
		int cards[][] = new int [4][4];
		Random random = new Random();
		int temp, value;
		
		for (int n=0; n<=20; n++)
		{
			for (int i=0; i<16; i++)
			{
				value = random.nextInt(1000000)%15;
				temp = initial[i];
				initial[i] = initial[value];
				initial[value] = temp;
			}
		}
		value = 0;
		return cards;
	}
			
		public static void BeginGame(boolean[][] check, int[][] cards)
		{
			boolean GameOver = false;
			
			char row0, row1, column0, column1;
			int r1, c1;
			int r2 = 0, c2 = 0;
			
		do
		{
			do
			{
			System.out.println("Select a card: ");	
			String row = new String(input.nextLine());
					
			row0 = row.charAt(0);
			column0 = row.charAt(1);
			r1 = Character.digit(row0, 5);
			c1 = Character.digit(column0, 5);
			if (check[r1-1][c1-1] == true)
				{
				System.out.print("This one is already face up. Select again.");	
				}
			}
			while (check[r1-1][c1-1] != false);
			
			do
			{
			System.out.println("Select a second card: ");
			String row11 = new String(input.nextLine());
			row1 = row11.charAt(0);
			column1 = row11.charAt(1);
			r2 = Character.digit(row1, 5);
			c2 = Character.digit(column1, 5);
			if(check[r2-1][c2-1] == true)
				{
				System.out.print("This one is already face up. Select again.");	
				}
			}
			while((check[r2-1][c2-1] != false || ((r1==r2) && c1==c2)));
			r1--;
			c1--;
			r2--;
			c2--;
			System.out.println();
			System.out.println("  1 2 3 4 ");
			System.out.println("___________");
			for (int row=0; row<4; row++)
				{
				System.out.print("  " + (row+1) +"  ");
				for (int column=0; column<4; column++)
					{
					if ((row==r1)&&(column==c1))
				    	{
				        System.out.print(cards[row][column] +" ");
				        }
					else if((row==r2)&&(column==c2))
				        {
				        System.out.print(cards[row][column] +" ");
				        }
					else if (check[row][column] == true)
				        {
				        System.out.print(cards[row][column] +" ");
				        }
					else
				        {
				        System.out.print("* ");
				        }
				    }
				System.out.println();
				}
			
			System.out.println(); 
			if (cards[r1][c1]==cards[r2][c2])
				{
				System.out.println("You have a match!");
				check[r1][c1] = true;
				check[r2][c2] = true;
				}
	       
			System.out.println();
			System.out.println("  1 2 3 4 ");
			System.out.println("___________");
	      
			for (int row=0; row<4; row++)
				{
				System.out.print(" " +(row+1) +" | ");
				for (int column=0; column<4; column++)
				{
					if (check[row][column] == true)
						{
						System.out.print(cards[row][column] +" ");
						}
					else
						{
						System.out.print("* ");
						}
				}
				System.out.println();
				}
			
	      System.out.println();
	      GameOver = true;
	      for (int row=0; row<4; row++) 
	      	{
	        for (int column=0; column<4; column++)
	        {
	          if(check[row][column]==false)
	          {
	            GameOver = false;
	            column=5;
	          }
	        }
	        if(GameOver == false)
	        	{
	        	row=5;
	        	}
	      	}
	  	while(GameOver != true); 
		}
		while(GameOver = false);
		}
}
	
 	
  
