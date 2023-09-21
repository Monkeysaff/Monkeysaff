python
import pygame
import random

# Initialize Pygame
pygame.init()

# Set up the display
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))

# Set up the colors
white = (255, 255, 255)
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 255)

# Set up the player
player_size = 50
player_pos = [screen_width / 2, screen_height - player_size]
player_speed = 10

# Set up the fruits
fruit_size = 50
fruit_pos = [random.randint(0, screen_width - fruit_size), 0]
fruit_speed = 5

# Set up the game loop
running = True
while running:
    # Event handling
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Player movement
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        player_pos[0] -= player_speed
    if keys[pygame.K_RIGHT]:
        player_pos[0] += player_speed

    # Keep player on the screen
    if player_pos[0] < 0:
        player_pos[0] = 0
    if player_pos[0] > screen_width - player_size:
        player_pos[0] = screen_width - player_size

    # Fruit movement
    fruit_pos[1] += fruit_speed
    if fruit_pos[1] > screen_height:
        fruit_pos[0] = random.randint(0, screen_width - fruit_size)
        fruit_pos[1] = 0

    # Check for collisions
    if (player_pos
