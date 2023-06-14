import pygame
from pygame.locals import *

# Initialize Pygame
pygame.init()

# Set up the display
screen_width = 800
screen_height = 400
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Pixel Football Game")

# Set up the colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)

# Set up the player
player_pos = [50, screen_height // 2]
player_size = 50

# Set up the game clock
clock = pygame.time.Clock()

# Main game loop
running = True
while running:
    # Event handling
    for event in pygame.event.get():
        if event.type == QUIT:
            running = False

    # Player movement
    keys = pygame.key.get_pressed()
    if keys[K_UP] and player_pos[1] > 0:
        player_pos[1] -= 5
    if keys[K_DOWN] and player_pos[1] < screen_height - player_size:
        player_pos[1] += 5

    # Update the display
    screen.fill(BLACK)
    pygame.draw.rect(screen, WHITE, (player_pos[0], player_pos[1], player_size, player_size))

    pygame.display.update()
    clock.tick(60)

# Quit the game
pygame.quit()
