- 👋 Hi, I’m @abhinav-nova
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...import pygame
import sys

# Game constants
SCREEN_WIDTH = 400
SCREEN_HEIGHT = 600
PIPE_WIDTH = 80
PIPE_HEIGHT = 600
BIRD_WIDTH = 40
BIRD_HEIGHT = 40
GRAVITY = 0.5

# Colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Initialize Pygame
pygame.init()
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
clock = pygame.time.Clock()

# Load images
bird_image = pygame.image.load('bird.png')
pipe_image = pygame.image.load('pipe.png')

# Game variables
bird_x = SCREEN_WIDTH / 2
bird_y = SCREEN_HEIGHT / 2
bird_velocity = 0
pipe_x = SCREEN_WIDTH
pipe_y = SCREEN_HEIGHT / 2
score = 0

# Game loop
while True:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                bird_velocity = -10

    # Move bird
    bird_velocity += GRAVITY
    bird_y += bird_velocity

    # Move pipe
    pipe_x -= 5
    if pipe_x < -PIPE_WIDTH:
        pipe_x = SCREEN_WIDTH
        pipe_y = random.randint(0, SCREEN_HEIGHT - PIPE_HEIGHT)

    # Collision detection
    if (bird_x + BIRD_WIDTH > pipe_x and
        bird_x < pipe_x + PIPE_WIDTH and
        (bird_y < pipe_y or bird_y + BIRD_HEIGHT > pipe_y + PIPE_HEIGHT)):
        print("Game Over!")
        pygame.quit()
        sys.exit()

    # Draw everything
    screen.fill(WHITE)
    screen.blit(bird_image, (bird_x, bird_y))
    screen.blit(pipe_image, (pipe_x, pipe_y))
    pygame.display.flip()

    # Cap framerate
    clock.tick(60)
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
abhinav-nova/abhinav-nova is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
