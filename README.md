# ToDoList
Made on Eclipse Software @ID Tech

package nickolasprocessing;
import java.util.Scanner;
import processing.core.PApplet;


public class NickolasProcessing extends PApplet {
	
	static String[] tasks = new String[1000];
	
	String typing = "";
	static Scanner input = new Scanner (System.in);
	int Offset = 10;
	int newTask = 0;
	boolean start = true;
	public static void main(String[] args) {
		PApplet.main("nickolasprocessing.NickolasProcessing");
	}
	
	public void settings() {
		size(1000,800);
	}
	
	public void setup() {
		for(int i= 0; i<tasks.length; i++) {
			tasks[i] = "";
		}
	}

	public void draw() {
		
		if(start == true) {
		text("Welcome to Your Checklist!  Stay on top of tasks and never lose track of your Objectives! Type your name and press Enter!", 50, 50);
		text(typing, 50, 70);
		}
		if(start == false) {
		if (key == '\n')
			text("Welcome "+typing, 50, 120);
		
		if (key == '\n')
			text("Write your Task, then Press ENTER to move onto your next task", 50, 170);
		
		if (key == '\n')
		Offset = 180;
		
		for(int i=0; i<tasks.length; i++) {
			text(tasks[i], 70, Offset);
			Offset += 10;
			text(i+".", 50, Offset + 0);
		}
		}
		
	}
	
	public void keyPressed() {
		
		if(start == true) {
			typing += key;
			if(key =='\n') {
				start = false;
			}
		}
		
		tasks[newTask]+= key;
		
		if(key == '\n') {
			newTask++;
		}
			
	}
}
