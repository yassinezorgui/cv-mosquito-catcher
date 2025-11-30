# Mosquito Exterminator 🦟

A fun, interactive computer vision-based game where you use hand gestures to catch mosquitoes and avoid bees!

## Overview

**Mosquito Exterminator** is a real-time game that uses your webcam and hand tracking to let you interact with the game world. Your hand acts as a cursor that you can use to click on and eliminate mosquitoes while avoiding bees. The game combines pygame for graphics and Mediapipe for hand detection to create an engaging, gesture-based gaming experience.

## Features

- 🎮 **Hand Gesture Controls**: Use your hand to control the game cursor
- 🦟 **Dynamic Gameplay**: Catch mosquitoes and avoid bees
- ⏱️ **60-Second Time Challenge**: Beat the clock to get the highest score
- 🎵 **Audio Feedback**: Sound effects for slaps and penalties
- 📊 **Score System**: Gain points for eliminating mosquitoes, lose points if you hit bees
- 🎨 **Animated Sprites**: Smooth animations for insects and hand cursor
- 📈 **Progressive Difficulty**: More bees spawn as the game progresses

## Gameplay

### Objective
- **Eliminate mosquitoes** to increase your score
- **Avoid bees** - hitting them results in a 5-point penalty
- **Survive for 60 seconds** and achieve the highest score possible

### How to Play
1. Start the game from the menu
2. Use your hand to point and close your fist to "click"
3. Click on mosquitoes to eliminate them (1 point each)
4. Watch out for bees that spawn - avoid clicking them (-5 points)
5. More bees appear as time runs out
6. Return to menu when the game ends

## Technical Stack

- **pygame**: Graphics and game engine
- **OpenCV (cv2)**: Webcam input and video processing
- **Mediapipe**: Hand pose detection and tracking
- **Python 3**: Core programming language

## Project Structure

```
cv-mosquito-catcher/
├── main.py                  # Main game loop and entry point
├── game.py                  # Core game logic and state management
├── menu.py                  # Menu interface
├── settings.py              # Game configuration and constants
├── hand_tracking.py         # Hand detection using Mediapipe
├── hand.py                  # Hand object and hitbox logic
├── mosquito.py              # Mosquito class and behavior
├── bee.py                   # Bee class (extends Mosquito)
├── background.py            # Background rendering
├── ui.py                    # UI elements and text rendering
├── image.py                 # Image loading and manipulation utilities
├── Assets/                  # Game resources
│   ├── mosquito/            # Mosquito sprites
│   ├── bee/                 # Bee animation frames (1-6)
│   ├── Sounds/              # Audio files
│   │   ├── Komiku_-_12_-_Bicycle.mp3  # Background music
│   │   ├── slap.wav                    # Click/hit sound
│   │   └── screaming.wav               # Bee hit penalty sound
│   └── hand.png             # Hand cursor sprite
└── README.md                # This file
```

## Installation

### Prerequisites
- Python 3.7 or higher
- Webcam/camera device

### Dependencies

Install required packages:
```bash
pip install pygame opencv-python mediapipe numpy
```

### Setup

1. Clone or download the repository
2. Navigate to the project directory
3. Ensure your webcam is connected and working
4. Run the game:
```bash
python main.py
```

## Game Configuration

Edit `settings.py` to customize the game:

- `SCREEN_WIDTH, SCREEN_HEIGHT`: Window resolution (default: 1920x1080)
- `FPS`: Game frames per second (default: 90)
- `GAME_DURATION`: Length of game in seconds (default: 60)
- `MOSQUITOS_SPAWN_TIME`: Spawn interval in seconds (default: 1)
- `MOSQUITOS_MOVE_SPEED`: Speed range for mosquitoes
- `BEE_PENALITY`: Points lost when hitting a bee (default: 5)
- `MUSIC_VOLUME`: Background music volume (0-1)
- `DRAW_FPS`: Show FPS counter (true/false)
- `DRAW_HITBOX`: Show collision boxes for debugging (true/false)

## Controls

| Action | Control |
|--------|---------|
| Move cursor | Move your hand in front of the webcam |
| Click/Slap | Close your fist (detected by hand tracking) |
| Pause/Quit | Press ESC |
| Main menu | Click START or Quit buttons |

## Game Mechanics

### Insects
- **Mosquitoes**: Spawn regularly, move randomly across the screen, worth 1 point each
- **Bees**: Spawn with increasing frequency as time runs out, worth -5 points if clicked

### Hand Tracking
- Uses Mediapipe's hand pose detection
- Tracks hand position in real-time
- Detects hand closure based on finger positions
- Adapts hand sprite size when closing fist

### Difficulty Scaling
- Game starts with only mosquitoes
- Bee spawn probability increases linearly throughout the game
- Second mosquito spawns after game halfway point (30 seconds)
- Bees move at similar speed to mosquitoes

## Scoring

| Action | Points |
|--------|--------|
| Hit mosquito | +1 |
| Hit bee | -5 |
| Completing game | Bonus based on time remaining |

## Troubleshooting

**Webcam not detected:**
- Ensure your webcam is plugged in and enabled
- Check camera permissions in your OS settings
- Try `cv2.VideoCapture(1)` or higher index in `game.py` if using multiple cameras

**Hand not being detected:**
- Ensure adequate lighting in your environment
- Position your hand fully in the camera frame
- Adjust `min_detection_confidence` in `hand_tracking.py` if needed

**Low FPS/Performance issues:**
- Reduce `SCREEN_WIDTH` and `SCREEN_HEIGHT` in settings
- Lower `FPS` value
- Close other applications

## Future Enhancements

- Difficulty levels (easy, normal, hard)
- Leaderboard system
- More insect varieties with unique behaviors
- Power-ups and special abilities
- Multiplayer hand tracking
- Mobile/tablet support
- Sound toggle in menu

## License

This project is provided as-is for educational and entertainment purposes.

## Author

Created as an opensource, interactive computer vision game project.

---

**Enjoy the game and good luck exterminating those mosquitoes!** 🎮✋
