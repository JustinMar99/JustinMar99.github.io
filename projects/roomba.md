---
layout: project
type: project
image: images/roomba.png
title: roomba
permalink: projects/roomba
date: 2019-02-13
labels:
  - Java
summary: Developed a moving object with obstacle detecting capabilities.
---

In this project, I was the sole programmer except on using a provided array to generate the map. The map has walls, and dirt that the roomba had to interact with. The code generates a roomba in the top left corner that moves randomly and leaves a small gray circle on areas its already been to. The roomba when on contact with an element of the map, will either collect it if it is a dirt block or move in a different direction if it is a wall. The program ends when the roomba collects all the dirt blocks. 

In this project, I learned how to connect an array to an image, and in doing so, create the map for the code from the array. I also learned how to detect obstacles with a moving object. Here's an example from the code that detects walls or obstacles in the roomba's path:

```java
public boolean collision(int x, int dx, int y, int dy, EZImage[] wall) {		//Checks if wall is present in chosen direction
		for(int i = 0; i<wall.length; i++) {
			if(wall[i] != null) {						//Only checks for existing wall added to arrays
				if(wall[i].isPointInElement(x+(dx*25), y+(dy*25))) {	//25 because while roombrah canvas is 32 pixels, roombrah itself is only about 25
					return true;
				} 
			}
		}
		return false;
	}
```

Here's an example in how the code detects if there is dirt in the roomba's path:

```java
public void clean(int x, int dx, int y, int dy, EZImage[] dirt) {			//Checks if dirt is present in chosen direction
		for(int i = 0; i<dirt.length; i++) {
			if(dirt[i] != null) {
				if(dirt[i].isPointInElement(x+(dx*25), y+(dy*25))) {
					dirt[i].translateTo(0, 0);
					dirt[i].pushToBack();		
					vacuum.play();
					dirtCount++;
					if(dirtCount == 9) {									
						victory.play();
					}
				}
			}
		}
	}
```

The code checks if the wall, obstacle, or dirt is in the roomba's path using the isPointInElement() method on the array containing the wall and dirt blocks. I also learned about moving objects that are no longer needed instead of deleting them. This was done on the dirt blocks, moving them to the top left corner and pushing it behind the wall that is there.

You can see a video demonstration at https://www.youtube.com/watch?v=TCad7c73uAw
