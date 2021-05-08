package week5;


import javax.swing.*;
import java.awt.event.*;
import java.util.*;

import acm.graphics.*;
import acm.program.GraphicsProgram;

public class BoxDiagram extends GraphicsProgram {
	private HashMap<String, GCompound> dict;
	private GCompound moveBox;
	private JTextField textEntry = new JTextField("", 30);
	private int scrHeight;
	private int scrWidth;
	private static final double BOX_WIDTH = 120;
	private static final double BOX_HEIGHT = 50;
	private int moveBoxOffsetX;
	private int moveBoxOffsetY;
	
	public void init() {
		dict = new HashMap<String, GCompound>();
		this.scrHeight = getHeight();
		this.scrWidth = getWidth();
		
		add(new JLabel("Name"), SOUTH);
		add(textEntry, SOUTH);
		add(new JButton("Add"), SOUTH);
		add(new JButton("Remove"), SOUTH);
		add(new JButton("Clear"), SOUTH);
		
		addActionListeners();
		addMouseListeners();
	}
	
	public void run() {
	
	}
	
	public void actionPerformed(ActionEvent e) {
		String cmd = e.getActionCommand();
		String message = textEntry.getText();
		if (cmd.equals("Add")) {
			addBox(message);
			textEntry.setText("");
		}
		else if(cmd.equals("Remove")) {
			removeBox(message);
			textEntry.setText("");
		}
		else if(cmd.equals("Clear")) {
			clearBoxes();
		}
	}

	public void addBox(String boxName) {
		if (!dict.containsKey(boxName)) {
			GCompound newBox = new GCompound();
			newBox.add(new GRect(BOX_WIDTH, BOX_HEIGHT), -BOX_WIDTH/2, -BOX_HEIGHT/2);
			GLabel textBox = new GLabel(boxName);
			newBox.add(textBox, -textBox.getWidth()/2, 5);
			newBox.setLocation(scrWidth/2, scrHeight/2);
			add(newBox);
			dict.put(boxName, newBox);
		}
	}
	public void removeBox(String boxName) {
		if (dict.containsKey(boxName)) {
			remove(dict.get(boxName));
			dict.remove(boxName);
		}
	}
	public void clearBoxes() {
		Set<String> tmpset = new HashSet<String>(); 
		tmpset.addAll(dict.keySet());
		for (String x: tmpset) {
			remove(dict.get(x));
			dict.remove(x);
		}
	}
	
	
	public void mousePressed(MouseEvent e) {
		int x = e.getX();
		int y = e.getY();
		GObject tmp = getElementAt(x, y);
		if (tmp != null ) {
			moveBox = (GCompound) tmp;
			GPoint tmpPoint = moveBox.getLocalPoint(x, y);
			moveBoxOffsetX = (int) tmpPoint.getX();
			moveBoxOffsetY = (int) tmpPoint.getY();
		}
	}
	
	public void mouseDragged(MouseEvent e) {
		if (moveBox != null) {
			int x = e.getX();
			int y = e.getY();
			moveBox.setLocation(x-moveBoxOffsetX, y-moveBoxOffsetY);
		}
	}
}
