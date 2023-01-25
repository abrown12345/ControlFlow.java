import java.util.Scanner;
import java.io.*;
import java.util.Random; 
import java.util.Arrays;
public class AsciiChars {

	static boolean testYes(String value) {
		if(value.toLowerCase().startsWith("y")) {
			return true;
		} else {
			return false;
		}
	}
	static int Range(int value, int lowerValue, int upperValue) {
		int width=upperValue-lowerValue+1;
		while(value>upperValue) {
			value= value- width;
		}
		while (value<lowerValue) {
			value= value+ width;
		}
		return value;
	}
	public static void main (String[] args) {
		Scanner userInput= new Scanner(System.in);
		Scanner scanner= new Scanner(System.in);
		AsciiChars.printNumbers();
		AsciiChars.printUpperCase();
		AsciiChars.printLowerCase();
		System.out.println("Please enter your name");
		String key= userInput.nextLine();
		System.out.printf("Hello %s",key);
		System.out.println("\nDo you wish to continue to the interactive portion? (Enter yes or no)");
		String response= userInput.nextLine();
		if(testYes(response)) {
			do {
				play(scanner);
				System.out.println("Do you want to play again?");
				response=userInput.nextLine();
			}while(testYes(response));
		} else {
			System.out.println("Please return later to complete the survey");
		}
	}
			
	public static void play(Scanner scanner) {
		Scanner userInput= new Scanner(System.in);
			System.out.println("We will now ask a series of questions");
			System.out.println("What is the name of your favorite pet?");
			String pet=userInput.nextLine();
			System.out.println("What is the age of your favorite pet?");
			Integer age=userInput.nextInt();
			System.out.println("What is your lucky number?");
			Integer lucky=userInput.nextInt();
			System.out.println("Do you have a favorite quarterback?");
			boolean quarterback= testYes(scanner.nextLine());
			int jersey = -1;
			if(quarterback) {
				System.out.println("What is the jersey number?");
				jersey=Integer.parseInt(scanner.nextLine());
			}
			System.out.println("What is the two-digit model year of your car?");
			Integer model=userInput.nextInt();
			System.out.println("Enter a random number between 1 and 50");
			Integer random=userInput.nextInt();
			int [] randomNumbers = new int[3];
			Random rng= new Random();
			for (int i=0; i<3; i++) {
				randomNumbers[i]= rng.nextInt(65)+1;
			}
			System.out.println("Enter a random number between 1 and 3");
			Integer random1=userInput.nextInt();
			Integer magicball=jersey*random1;
			if(magicball>75){
				Integer magicballnew= magicball-75;
				System.out.println("The magic ball number is:"+ magicballnew);
			}
			if (magicball<1) {
				int magicballnew=magicball+75;
				System.out.println("The magic ball number is:" + magicballnew);
			}
			System.out.println("The magic ball number is:" + magicball);
			Integer QAL= jersey+age+lucky;
			Integer PM= age+model;
			Integer RR= random-random1;
			Integer ML= model+lucky;
			System.out.println("Lottery numbers: " + QAL + "," + PM + "," + 42 + "," + RR + "," + ML +" " + "Magic ball:" + magicball); 
			}
	public static void printNumbers() 
	{ 	char ch;
		for (ch=48; ch<=57; ch++)
			System.out.println(ch);	
	}
	public static void printLowerCase()
	{	char ch; //Character variable ch
		for (ch=97; ch<=122; ch++)
			System.out.println(ch);
	}

	public static void printUpperCase() 
	{	char ch;
		for (ch=65; ch<=90; ch++)
			System.out.println(ch);	
	}	

}
