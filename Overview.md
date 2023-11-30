Which package/library did you select?
- Pygame package in Python
  
What is the package/library?
- Pygame package is a Python programming language package that is both free and open source, designed for creating multimedia applications such as games. [1]

What purpose does it serve?
- Creating a simple game like Space Invaders using Pygame is a common project for beginners learning game development. It allows individuals to understand the basics of game architecture, graphics rendering, user input handling, collision detection, and many more. It involves using many significant concepts such as classes, functions, loops, and conditional statements to create a functioning game. [1]
- Pygame is a popular library for creating 2D games in Python. Building Space Invaders helps developers become familiar with the Pygame library and its features, such as handling images, sounds, and input. [1]
- Even though Space invader is simple, it requires the implementation of game mechanics, enemy behaviors, and player controls, which can challenge developers to think critically. [1]
- Once the basic Space Invaders game is implemented, developers can customize and expand upon it. This might include adding new features, modifying game mechanics, incorporating different levels, or improving the graphics and sound effects. This customization allows for creativity and experimentation. [1]

What would be some sample input/output?
- In the space invader game, sample input would be all images, sounds, commands, sizes of the game on the screen, etc. Additionally, the output is the 2D game for letting the audience play and enjoy.

How do you use it? 
- Import Pygame package in python by typing the following command in your terminal (better in Visual studio code) [1]
```
pip install pygame
```
- then type the following import statement in your program [1]
```
import pygame
```
- Design the simple game as desired.

What are the functionalities of the package/library? 
- Ex. Starting by creating a simple show screen with a desired background. Make sure that your images file are in the same directory with your code file. [3]
```
import pygame
#define size
screen_width = 1200
screen_height = 600
#pass in sizes
screen = pygame.display.set_mode((screen_width, screen_height))
#Pick the name for the game
pygame.display.set_caption('Space Invader YUH YUH')
#limited fps(framerate)
fps = 180
#define fps
clock = pygame.time.Clock()
#load background
background = pygame.image.load("space_bg.png")
#create a drawing function
def draw_background():
    screen.blit(background, (0, 0))
#Now, create a loop that calls function event handler from pygame
#And then draw the screen inside this loop
run = True
while run:
    clock.tick(fps)
    #draw background
    draw_background()
    #event handler
    for event in pygame.event.get():
        #done playing
        if event.type == pygame.QUIT:
            run = False 
    #update background.
    pygame.display.update()
#once done with the program, quit pygame libary
pygame.quit()
```

- Ex. Creating a spaceship class to draw and have multiple desired function. [3]
```
import pygame
#define size
screen_width = 1200
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption('Space Invader YUH YUH')
#limited fps(framerate)
fps = 180
#define fps
clock = pygame.time.Clock()
#load background
background = pygame.image.load("space_bg.png")
def draw_background():
    screen.blit(background, (0, 0))
#create spcaeship class
class Spaceship(pygame.sprite.Sprite):
    #self, position at x and y
    def __init__(self, x, y):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("spaceship.png")
        self.rect = self.image.get_rect()
        self.rect.center = [x, y]

#create sprite groups
#work as a list
spaceship_group = pygame.sprite.Group()
#create Player
#at the center, and the bottom
spaceship = Spaceship(int(screen_width / 2), screen_height - 100)
spaceship_group.add(spaceship)
run = True
while run:
    clock.tick(fps)
    #draw background
    draw_background()
     #draw sapceship on the screen
    spaceship_group.draw(screen)
    #event handler
    for event in pygame.event.get():
        #done playing
        if event.type == pygame.QUIT:
            run = False 
    #update background, aliens, etc.
    pygame.display.update()
pygame.quit()
```
- Ex. Now, we have the background and the spaceship, let's move the space hip to the left and right but not exceed the set up screen. Add the following code into the spaceship class.
```
def update(self):
        #set moevment speed
        speed = 8
        #get key press
        #contains all the key that has been pressed
        key = pygame.key.get_pressed()
        #if left k has been pressed
        #limit it to be at the end of both side of screen
        if key[pygame.K_LEFT] and self.rect.left > 0:
            #move left
            self.rect.x -= speed #decrease by 8 each time
        if key[pygame.K_RIGHT] and self.rect.right < screen_width:
            #move to right
            self.rect.x += speed
```
Next, add this following code in the while loop after the event handler. We just simply called the moving function from the spaceship class.
```
spaceship.update()
```
- Ex. Games with no sound will not satisfy the joy of playing. Here is the simple way to put in the sound every time the spaceship shoots, gets hit, or destroyed. [3]
```
#load sounds
explosion_fx = pygame.mixer.Sound("explosion.wav")
explosion_fx.set_volume(0.25)

explosion2_fx = pygame.mixer.Sound("Voicy_Bonk.MP3")
explosion2_fx.set_volume(105)

laser_fx = pygame.mixer.Sound("laser.wav")
laser_fx.set_volume(0.25)
```
We can simply call each sound and play by typing the folowing command inside the class or anywhere we desired to.
```
<SONG_VARIABLE>.play()
```
For example, 

```
#shooting by tapping a spacebar and if half of the time has passed
if key[pygame.K_SPACE] and time_now - self.last_shot > cooldown:
  #play the sound everytime it got hit
  laser_fx.play()
```

When was it created?
- Pygame package was created on October 28th, 2000. [2]

Why did you select this package/library?
- This package provides multiple simple, yet fundamental functions to build an interesting game as desired. Not only those functions are useful, but they also provide the basic knowledge of understating the syntax and how object-oriented programming works such as Spaceship class, Alien class, or Bullet class. Moreover, the flexibility it offers enables programmers to customize various elements, introducing different levels of complexity or unique features. For example, the ability to design varied levels for each alien or enable the spaceship to move left and right enhances the creative possibilities within the game. We could even develop a spaceship to move back and forth. Pygame allows individuals to simply code a game by supplying its easy-to-understand syntax. 

How did learning the package/library influence your learning of the language? 
- The process of learning the Pygame library has significantly influenced my understanding of the Python programming language. By working with Pygame, I have gained insights into various aspects of programming, particularly in the context of game development. For example, Pygame encourages the use of object-oriented programming principles. Building classes for game elements like spaceship character, bullet object, or a background scene becomes essential. This provides me more of the perspective of OOP concepts in Python, such as encapsulation, inheritance, and polymorphism. Moreover, I could get to practice more of the Object Manipulation. Working with Pygame involves extensive manipulation of game objects on the screen. This has improved my skills in handling objects, including their creation, modification, and interaction within a program. In terms of designing Game Logic, it involves planning how different elements interact, respond to user input, and contribute to the overall gaming experience. In summary, learning Pygame has not only advanced my skills in game development but has also practiced my understanding of Python's capabilities, particularly in areas such as object-oriented design, problem-solving, and overall software development.

How was your overall experience with the package/library?
- Pygame offers a positive and accessible experience for game development. Its simplicity and the ability to quickly see results make it an easy choice when it comes to building a simple game.
When would you recommend this package/library to someone? 
- I would recommend Pygame to someone interested in building a game, especially if they are relatively new to programming or game development. The library's simplicity and a lot of resources available, including tutorials and community support, make it a great starting point for learning about game development concepts.

Would you continue using this package/library? Why or why not?
- Yes, I would continure to use it and explore more in details of the package. It remains relevant for various projects, ranging from simple games to more complex applications. Because of its simplicity, the use can be advantageous for rapid prototyping and testing game ideas. However, as developers gain more experience and venture into more advanced game development, there might be other libraries or frameworks that offer additional features or performance benefits.

References: [1] https://realpython.com/pygame-a-primer/ 
            [2] https://www.pygame.org/docs/tut/PygameIntro.html#:~:text=Pygame%20was%20started%20in%20October,pygame%20version%201.0%20was%20released.
            [3] https://github.com/russs123/space_invaders

