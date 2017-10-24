import java.awt.Color;

import javax.swing.JOptionPane;

import processing.core.PApplet;

public class pongpongpong1 extends PApplet {
	
	
	float y, yy;
	float x, xx;
	float speed = -7f, yspeed = -3f, hit = 0f;
	float ys = 3f, xs = 7f;
	int lives = 5,lives2 = 5,rectx=10,recty=100,rx = 580,ry = 100;
 
	public void setup() {
		textSize(32);
		size(600, 600);

		x = 300;
		y = 200;

	}
	
	public void draw() {
		fill(0);
		background(250, 150, 150);
		text("lives:"+ lives,0,600);
		text("lives:"+ lives2,500,600);
		recty = mouseY;
		
		fill(255);
		ellipse(x, y, 20, 20);
		rect(rectx,recty,10,100);
		rect(rx,ry,10,100);
		if (x <= -30) {
			x = 300;
			y = 300;
			lives = lives-1;
		}
		if (x >= 600) {
			x = 300;
			y = 300;
			lives2 = lives2 -1;
		}
		if (y <= 0) {
			yspeed = yspeed * -1;
			
		}
		if(y >= 600){
			yspeed = yspeed *-1;
		}
		
		x = x + speed;
		y = y + yspeed;
		if(x - 20< rectx){
			if(y+10 > recty && y + 10 < recty+100){
				speed = speed*-1;
			}
		}
		if(x + 20 > rx){
			if(y+10 > ry && y + 10 < ry+100){
				speed = speed*-1;
			}
		}
		if (keyPressed == true){
			if(keyCode == UP){
			ry=ry - 10;
			}
			if(keyCode == DOWN){
				ry = ry + 10;
			}
		}
		if(lives < 0){
			JOptionPane.showMessageDialog(null, "Game Over Player 1");
			System.exit(0);
		}if(lives2 < 0){
			JOptionPane.showMessageDialog(null, "Game Over Player 2");
			System.exit(0);
		}
				}
	

	public static void main(String[] args) {
		PApplet.main(new String[] { "Circle" });
	}
}
