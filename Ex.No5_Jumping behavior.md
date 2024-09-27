# Ex.No: 5  Implementation of Jumping behavior 
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
To write a python program to simulate Jumbing behavior. 
### Algorithm:
1. Start the program
2. Import the necessary modules
3. Initiate the pygame engine and window
4. Specify the necessary parameter for player height,depth,gravity,jump power. 
5. Create a game loop to simulate the continuous behavior.
6. If Quit button is pressed then quit the pygame window.
7. Move the player left when left button is pressed
8. Move the player right when right button is pressed
9. If space bar is pressed then enable the jump by increasing y axis value.
10. land the player and display the player at every timestep
11.  Stop the program
 ### Program:
```
import pygame
from pygame.locals import *
from sys import exit

sprite_image_filename = r'E:\Downloads\fourarms.png'
pygame.init()
screen = pygame.display.set_mode((640, 480), 0, 32)
sprite = pygame.image.load(sprite_image_filename)
screen.fill((255, 255, 255))
clock = pygame.time.Clock()

# Speed in pixels per second
speed = 250
# The x coordinate of our sprite
x = 0.0

# Variables for jumping
y = 100
y_velocity = 0
gravity = 1000  # pixels per second squared
jump_speed = -600  # initial jump velocity

# Flag to check if the sprite is on the ground
is_jumping = False

while True:
    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.quit()
            exit()
        elif event.type == KEYDOWN:
            if event.key == K_SPACE and not is_jumping:
                y_velocity = jump_speed
                is_jumping = True
    
    # Clear the screen
    screen.fill((255, 255, 255))
    
    # Calculate the time passed
    time_passed = clock.tick(30)
    time_passed_seconds = time_passed / 1000.0
    
    # Calculate the distance moved horizontally
    distance_moved = time_passed_seconds * speed
    x += distance_moved
    
    # Calculate vertical movement
    y_velocity += gravity * time_passed_seconds
    y += y_velocity * time_passed_seconds
    
    # Check if sprite has landed on the ground
    if y >= 100:
        y = 100
        y_velocity = 0
        is_jumping = False
    
    # Draw the sprite at the new position
    screen.blit(sprite, (x, y))
    
    # If the image goes off the end of the screen, move it back
    if x > 640:
        x -= 640
    
    # Update the display
    pygame.display.update()

```
### Output:
![](exp5op1.jpeg)


### Result:
Thus the simple jumping behavior was implemented.
