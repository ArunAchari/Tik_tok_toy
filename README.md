#Tik_tok_toy
"This is a simple Java-based Tic-Tac-Toe game developed using core Java and Swing for GUI. It allows two players to play on a 3x3 grid with turn-based logic. The project helps in understanding basic game development concepts like 2D arrays, event handling, and UI design using Java Swing."


package com.Game;
import java.util.Scanner;
public class Tik_tok_toy1 {
	static String green="\u001B[32m";
	static String blue="\u001B[34m";
	static String bold="\u001B[1m";
	static String black="\u001B[30m";
	static String red="\u001B[36m"+"\u001B[31m";
	static String yellow="\u001B[33m";
 
	static char[][] a = {{' ',' ',' '},
				{' ',' ',' '},
				{' ',' ',' '}};
	static char currentplayer = 'x';	

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		while(true) {
		printBord();
		System.out.println(blue+"currentplayer" +currentplayer + "'chance");
		System.out.println(bold+black+"enter the row(0-2)");
		int row = sc.nextInt();
		System.out.println(bold+black+"enter the col(0-2)");
		int col = sc.nextInt();
		if (row < 0 || row > 2 || col < 0 || col > 2 || a[row][col] != ' ') {
			System.out.println(red+"Invaled Move!!");
			continue;
		}
		a[row][col]=currentplayer;
		if(inspection()) {
			printBord();
			System.out.println(""+currentplayer+"winner!!!");
			break;
		}
		if(renderDraw()) {
			System.out.println(yellow+"game draw!!!");
			printBord();
			break;
		}
		currentplayer=currentplayer=='x'?'o':'x';

	}
		sc.close();
	}


	static void printBord() {
		System.out.println(green+"----------");
		for (int i = 0; i < 3; i++) {
			System.out.print("|");
			for (int j = 0; j < 3; j++) {
				System.out.print(a[i][j] + " |");
			}
			System.out.println("\n----------");
		}
	}

	private static boolean inspection() {
		// row check
		for(int i=0;i<3;i++) {
			if(a[i][0]==currentplayer && 
					a[i][1]==currentplayer &&
					a[i][2]==currentplayer) {
				return true;
			}
		}
		//column check
		for(int i=0;i<3;i++) {
			if(a[0][i]==currentplayer &&
				a[1][i]==currentplayer &&
				a[2][i]==currentplayer ) {
				return true;
			}
		}
		//diagonal one check
		if(a[0][0]==currentplayer && 
				a[1][1]==currentplayer &&
				a[2][2]==currentplayer) {
			return true;
		}
		//diagonal two check
		if(a[0][2]==currentplayer && 
				a[1][1]==currentplayer &&
				a[2][0]==currentplayer) {
			return true;
		}
		return false;
	}
	private static boolean renderDraw() {
		for(int i=0;i<3;i++) {
			for(int j=0;j<3;j++) {
				if(a[i][j]==' ') {
					return false;
				}
			}
		}
		return true;
	}


}
