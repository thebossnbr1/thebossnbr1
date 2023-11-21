import pygame

def main():

    # Initialize pygame
    pygame.init()

    # Set up the display
    display = pygame.display.set_mode((800, 600))
    pygame.display.set_caption("My Game")

    # Define the player object
    player = {
        "x": 400,
        "y": 300,
        "width": 50,
        "height": 50,
        "color": (255, 255, 255),
    }

    # Define the goal object
    goal = {
        "x": 700,
        "y": 500,
        "width": 50,
        "height": 50,
        "color": (0, 255, 0),
    }

    # Game loop
    running = True
    while running:

        # Check for events
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    player["x"] -= 5
                elif event.key == pygame.K_RIGHT:
                    player["x"] += 5
                elif event.key == pygame.K_UP:
                    player["y"] -= 5
                elif event.key == pygame.K_DOWN:
                    player["y"] += 5

        # Check for collisions
        if player["x"] + player["width"] >= goal["x"] and \
            player["y"] + player["height"] >= goal["y"] and \
            goal["x"] + goal["width"] >= player["x"] and \
            goal["y"] + goal["height"] >= player["y"]:
            print("You win!")
            running = False

        # Fill the display with white
        display.fill((255, 255, 255))

        # Draw the player
        pygame.draw.rect(display, player["color"], player)

        # Draw the goal
        pygame.draw.rect(display, goal["color"], goal)

        # Update the display
        pygame.display.flip()

# Run the game
main()

