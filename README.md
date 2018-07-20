# ToDoList
Made on Eclipse Software @ID Tech

package nickolasprocessing;
import java.util.Scanner;

import processing.core.PApplet;
import processing.core.PImage;


public class NickolasProcessing extends PApplet {
	
	static String[] tasks = new String[1000];
	box[] boxes = new box[1000];
	PImage img1;
	PImage img2;
	int boxOffset = 10;
	String typing = "";
	static Scanner input = new Scanner (System.in);
	int Offset = 10;
	int newTask = 0;
	int rectOffset=30;
	boolean start = true;
	public static void main(String[] args) {
		PApplet.main("nickolasprocessing.NickolasProcessing");
	}
	
	public void settings() {
		size(1000,800);
		
		img1 = loadImage("Orange_checkbox-unchecked.svg.png");
	}
	
	public void setup() {
		background(31, 190, 225);
		for(int i= 0; i<tasks.length; i++) {
			tasks[i] = "";
		}
	}

	public void draw() {
		
		if(start == true) {
		text("Welcome to ForYouList!  Stay on top of tasks and never lose track of your Objectives! Type your name and press Enter!", 50, 50);
		text(typing, 50, 70);
		fill(255,225,0);
		
		}
		if(start == false) {
			
		
		
		Offset = 180;
		
		rectOffset =170;
		for(int i =0; i<= newTask;i++) {
			if(boxes[i] == null) {
				break;
				}
			if(boxes[i].checked == true&& boxes[i]!= null) {
				fill(0,255,0);
			}
			
				else {
					
			fill(255,0,0);}
			rectMode(CORNER);
			rect(40,rectOffset,15,15);
			rectOffset+=20;
		}
		//mess with Offset
		
		textSize(15);
		for(int i=1; i<tasks.length; i++) {
			text(tasks[i], 90, Offset-1);
			
			fill(0,0,0);
			
			text(+i+".", 70, Offset);
			Offset += 20;
		}
		
		if (key == '\n')
			text("Welcome "+typing, 50, 120);
			fill(255,255,255);
		
		if (key == '\n')
			text("Write your Task, then Press ENTER to move onto your next task", 50, 160);
		}
		
	}
	
	//textSize(50);
	boolean insideBox = false;
	public void mousePressed() {
		rectOffset =170;
		for(int i = 0; i<newTask; i++) {
			if(mouseX> 40&& mouseX<50&& mouseY >rectOffset&& mouseY<rectOffset+20) {
				if(boxes[i].checked == false)
						boxes[i].checked = true;
				else if(boxes[i].checked == true) {
					boxes[i].checked = false;
				}
				
				println("it works!");	
			}rectOffset+=20;
			println("mouseX:"+mouseX+"mouseY:"+mouseY);
			println(i+" rectOffset:"+rectOffset+"rectOffset+20: "+(rectOffset+20));
		}
		
	}
	PImage[]checkbox = new PImage [1000];
	public void keyPressed() {
		
		if(start == true) {
			typing += key;
			if(key =='\n') {
				start = false;
			}
		}
		if(start == false) {
		tasks[newTask]+= key;
		
		if(key == BACKSPACE) {
			char[] temp = tasks[newTask].toCharArray();
			tasks[newTask]="";
			for(int i = 0 ; i<temp.length-2; i++) {
			clear();
			background(31, 190, 214);
			tasks[newTask]+=""+ temp[i];
			}
			
		}
		
		if(key == '\n') {
			boxes[newTask] = new box();
			newTask++;
			
		}
		}
			
	}
}
class box{
	boolean checked;

	box(){
		checked = false;
		
	}
}
