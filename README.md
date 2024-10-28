# AIProject
Repo for Rubik's Cube Project

---
title: VideoCube
---

# VideoCube

```{figure} ../_static/videos/environments/video_cube.gif
:width: 120px
:name: VideoCube
```

This environment is part of the <a href='..'>Atari environments</a>. Please read that page first for general information.

|                   |                                      |
|-------------------|--------------------------------------|
| Action Space      | Discrete(18)                         |
| Observation Space | Box(0, 255, (210, 160, 3), uint8)    |
| Import            | `gymnasium.make("ALE/VideoCube-v5")` |

For more VideoCube variants with different observation and action spaces, see the variants section.

## Description

Solve a Rubik's cube in a nonstandard way: guide Hubie around the cube and swap tiles on the cubes face with one another until each face consists of only one color.

For a more detailed documentation, see [the AtariAge page](https://atariage.com/manual_html_page.php?SoftwareLabelID=974)

## Actions

VideoCube has the action space `Discrete(18)` with the table below listing the meaning of each action's meanings.
As VideoCube uses the full set of actions then specifying `full_action_space=True` will not modify the action space of the environment if passed to `gymnasium.make`.

| Value   | Meaning      | Value   | Meaning         | Value   | Meaning        |
|---------|--------------|---------|-----------------|---------|----------------|
| `0`     | `NOOP`       | `1`     | `FIRE`          | `2`     | `UP`           |
| `3`     | `RIGHT`      | `4`     | `LEFT`          | `5`     | `DOWN`         |
| `6`     | `UPRIGHT`    | `7`     | `UPLEFT`        | `8`     | `DOWNRIGHT`    |
| `9`     | `DOWNLEFT`   | `10`    | `UPFIRE`        | `11`    | `RIGHTFIRE`    |
| `12`    | `LEFTFIRE`   | `13`    | `DOWNFIRE`      | `14`    | `UPRIGHTFIRE`  |
| `15`    | `UPLEFTFIRE` | `16`    | `DOWNRIGHTFIRE` | `17`    | `DOWNLEFTFIRE` |

See [environment specification](../env-spec) to see more information on the action meaning.

## Observations

Atari environments have three possible observation types:

- `obs_type="rgb"` -> `observation_space=Box(0, 255, (210, 160, 3), np.uint8)`
- `obs_type="ram"` -> `observation_space=Box(0, 255, (128,), np.uint8)`
- `obs_type="grayscale"` -> `Box(0, 255, (210, 160), np.uint8)`, a grayscale version of the q"rgb" type

See variants section for the type of observation used by each environment id by default.

## Variants

VideoCube has the following variants of the environment id which have the following differences in observation,
the number of frame-skips and the repeat action probability.

| Env-id               | obs_type=   | frameskip=   | repeat_action_probability=   |
|----------------------|-------------|--------------|------------------------------|
| ALE/VideoCube-v5     | `"rgb"`     | `4`          | `0.25`                       |
| ALE/VideoCube-ram-v5 | `"ram"`     | `4`          | `0.25`                       |

## Difficulty and modes

It is possible to specify various flavors of the environment via the keyword arguments `difficulty` and `mode`.
A flavor is a combination of a game mode and a difficulty setting. The table below lists the possible difficulty and mode values
along with the default values.

| Available Modes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Default Mode   | Available Difficulties   | Default Difficulty   |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|--------------------------|----------------------|
| `[0, 1, 2, 100, 101, 102, 200, 201, 202, 300, 301, 302, 400, 401, 402, 500, 501, 502, 600, 601, 602, 700, 701, 702, 800, 801, 802, 900, 901, 902, 1000, 1001, 1002, 1100, 1101, 1102, 1200, 1201, 1202, 1300, 1301, 1302, 1400, 1401, 1402, 1500, 1501, 1502, 1600, 1601, 1602, 1700, 1701, 1702, 1800, 1801, 1802, 1900, 1901, 1902, 2000, 2001, 2002, 2100, 2101, 2102, 2200, 2201, 2202, 2300, 2301, 2302, 2400, 2401, 2402, 2500, 2501, 2502, 2600, 2601, 2602, 2700, 2701, 2702, 2800, 2801, 2802, 2900, 2901, 2902, 3000, 3001, 3002, 3100, 3101, 3102, 3200, 3201, 3202, 3300, 3301, 3302, 3400, 3401, 3402, 3500, 3501, 3502, 3600, 3601, 3602, 3700, 3701, 3702, 3800, 3801, 3802, 3900, 3901, 3902, 4000, 4001, 4002, 4100, 4101, 4102, 4200, 4201, 4202, 4300, 4301, 4302, 4400, 4401, 4402, 4500, 4501, 4502, 4600, 4601, 4602, 4700, 4701, 4702, 4800, 4801, 4802, 4900, 4901, 4902, 5000, 5001, 5002]` | `0`            | `[0, 1]`                 | `0`                  |

 A  T  A  R  I      V  I  D  E  O      C  U  B  E


(c) 1983 ATARI, INC. ALL RIGHTS RESERVED

Table of Contents

1. Tour a Cube Master's World!
2. Game Play
3. Using the Controllers
4. Console Controls
5. Game Variations
6. Scoring
7. Helpful Hints
8. Game Select Matrix


1. TOUR A CUBE MASTER'S WORLD!

Welcome to the cubical world of Hubie the Cube Master.  Hubie can
solve the ATARI VIDEO CUBE puzzle in seconds flat -- 33.7 seconds, to
be exact.  That's fast, but then, he's had a lot of practice.  You
see, puzzles are Hubie's specialty.

Hubie wasn't always a Cube Master -- in fact he used to live a pretty
ordinary life.  Every morning he made his breakfast, fed his dog
Ralph, and went to work.  He did have a peculiar habit, though.  Hubie
loved everything that had to do with squares or angles.  For instance,
he was always sure to eat three square meals a day -- waffles for
breakfast, ravioli for lunch, and cube steaks for dinner.  Hubie slept
in a perfectly square bed.  Every day he swam laps in a square
swimming pool.  And each morning, as he walked to work, Hubie was sure
to count the squares in the sidewalk beneath his feet.

People called Hubie a blockhead, but when they did, he always had an
answer.  Looking them squarely in the eyes, Hubie would shout,
"Squares are important!  Try playing checkers on a _round_
checkerboard.  Or try using ice _balls_ instead of ice _cubes_ in your
drinks.  Can you imagine going to New York to visit Madison _Round_
Garden?  It's just not the same.  It wouldn't work!"  And with that,
he would square his shoulders and walk off.

Yes, Hubie certainly had a checkered past.  But that was before the
big change in his life.  One day, while square dancing in his favorite
restaurant (the one with the checkered tablecloths), someone gave
Hubie a puzzle -- a cube puzzle.  He played it day and night, twisting
and turning it to move the colors to the proper sides.  Soon, he
started to see cubes and squares everywhere -- on the walls of his
house, inside Ralph's square water dish, and even in the mirror while
brushing his teeth.

Something very strange was happening to Hubie.  One morning, instead
of being in his square bed, he found himself on a strange flat
surface.  He saw immediately that everything around him was square --
he was in an entirely square world!  This transformation was a
mystery, but Hubie didn't really care.  He was...Hubie the Cube Master!

Hubie knew his mission in life was to teach cubists and future cubists
the best ways to play the magical cube puzzle.  He promised himself
that he would learn how to solve the magical cube faster than anyone
else in the world.  He invites you to help him with his pledge -- can
you solve the cube faster than Hubie?  Try it and see!

2. GAME PLAY

Hubie's home is a six-sided, multi-colored cube.  Each side has nine
smaller faces, colored red, blue, green, white, purple, or orange.
When you start a game, the colors are scrambled.  Your task is to
arrange the colors so that each side becomes one solid color.

Play ATARI VIDEO CUBE by moving Hubie around the cube and having him
pick up and drop colors.  Each time Hubie picks up a color, he trades
his color for the one he has picked up (see Figure 1).  You can then
make Hubie run to another face to trade for a different color.  Solve
the puzzle in the least amount of moves or time (see Section 6,
SCORING).  Or, you can watch Hubie race the clock to solve the cube.
You might even get some cube-solving tips!

[ Figure 1 -- Dropping and Picking Up Colors: Figure 1 shows two
screen shots: the left-hand one shows the little elfin figure "Hubie"
standing on a red square in the middle of a randomized cube face.
Hubie is white in this screen shot.  The right-hand screen shot shows
a red Hubie standing on a white square. ]

You can only see one side of the cube at a time, except when turning
the cube to another side.  To turn the cube, move Hubie to the edge of
any side.  The cube will rotate, (see Figure 2) and Hubie will enter
the next side.  The cube and rotate up, down, and sideways.

[ Figure 2 -- Hubie Rotating the Cube: Hubie can be seen here crawling
from one side of the cube to another.  During this process, the cube
assumes an edge-on view where you can see both sides at the same
time. ]

3. USING THE CONTROLLERS

Use your left Joystick Controller with this ATARI Game Program
cartidge.  Be sure the controller is firmly plugged into the LEFT
CONTROLLER jack at the back of your 2600 Video Computer System game.
Hold the joystick with the red controller button to your upper left,
toward the television screen.  (See your Owner's Manual for further
details.)

Move Hubie around the cube with your Joystick.  He moves up, down,
right, and left in the same direction you move your Joystick.  Hubie
cannot move onto a square of the same color.  For example, if Hubie is
blue, he cannot run onto a blue square.  If you try moving Hubie onto
a square the same color as he, a warning buzzer or beep will sound.
(See Section 4, CONSOLE CONTROLS for further details.)

Use the red controller button to make Hubie pick up and drop colors.
Press the button once, and Hubie will pick up the color of the square
he is positioned on.  Press the button again, and Hubie will drop the
color on to the same or a different square.  Hubie can pick up, drop,
and carry colors to any square on the cube.

4. CONSOLE CONTROLS

GAME SELECT SWITCH

To select a game variation, press the GAME SELECT switch.  (See
Section 5, GAME VARIATIONS, for more information about game
variations.)  The game number will appear at the bottom of the screen.
(See Figure 3.)

[ Figure 3 -- Game Variation Number: At the bottom of the screen shot
in Figure 3 are the words "GAME: 1."  An arrow pointing at the 1
indicates that it represents the Game Variation. ]

GAME RESET SWITCH

To start or restart a game, press the GAME RESET switch.  You'll enter
the CUBE SELECT mode, and can select one of 50 different cubes.  The
colors on each cube are scrambled differently.  Use your Joystick to
select a cube number.  Push up or left to increase the cube number by
tens; push down or right to increase the cube number by ones (see
Figure 4).  The number you select appears on the bottom of the screen,
beneath the magical cube (see Figure 5).

         + 10

          /|\
           |
  + 10 <---> + 1
           |
          \|/

          + 1

Figure 4 -- Selecting the Cube Number

[ Figure 5 -- Cube Number: At the bottom of the screen shot
in Figure 5 are the words "CUBE: 1."  An arrow pointing at the 1
indicates that it represents the Cube Number. ]

After you select a cube, start the game by pressing the red controller
button once.  You're ready to go!

TV TYPE SWITCH

Set this switch to COLOR if you're playing on a color television set.
Set it to B-W to play the game in black and white.

DIFFICULTY SWITCHES

If you set the LEFT DIFFICULTY switch to the A position, a buzzer will
sound each time Hubie tries to run on to a square of the same color as
he.  Set the switch to the B position to change the buzzer sound to a
"beep."

The RIGHT DIFFICULTY switch has no function in this game.

5. GAME VARIATIONS

ATARI VIDEO CUBE includes 18 game variations.

Games 1-10 play at normal speed, and Games 11-18 play at a faster
speed.  In Games 3, 4, 7, 8, 13, 14, 17, and 18, the cube is blacked
out unless rotating to a different side.

Games 5-8, and Games 15-18 are slef playing, in which Hubie shows you
how to solve the cube in the least amount of moves or time.  In these
variations, all you need to do is press the GAME RESET switch.  The
computer will take control and start the game.

In Games 9 and 10, Hubie's movements are restricted and he can only move in
two directions: up, or to the right.

Odd-numbered games (1, 3, 5, 7, 9, 11, 13, 15, and 17) are scored by
the number of moves and the number of colors that are swapped.
Even-numbered games (2, 4, 6, 8, 10, 12, 14, 16, 18) are scored by the
time it takes to solve the cube.

6. SCORING

The object of the ATARI VIDEO CUBE game is to get the lowest score
possible.  If you are playing an odd-numbered game, your score is
displayed as a single number on the bottom of the screen.  Each time
Hubie crosses a new square, picks up a color, or attempts to cross a
square of his own color, you score one point.  Your score is displayed
on the lower center portion of the screen, beneath the cube (see
Figure 6).

[ Figure 6 -- Score in Number of Moves: At the bottom of the screen
shot in Figure 6 is the number 534 above the words "CUBE: 1."  An
arrow pointing at the 534 indicates that it represents the score. ]

If you are playing an even-numbered game, a timer measures the amount
of time it takes to finish the game.  Games are measured in minutes,
seconds, and tenths of a second (see Figure 7).

[ Figure 6 -- Score in Elapsed Time: At the bottom of the screen shot
in Figure 7 is what looks like "1 = 34 - 3" above the words "CUBE:
1."  Presumably this is a representation of 1:34.3 in Atari's font.
An arrow pointing at the timer indicates that it represents the
score. ]

7. HELPFUL HINTS

o Look for sides with three or more squares of a single color.  Decide
which color you want each side to be and keep adding to them.

o Try not to backtrack.  If you can pick up and deposit colors on
three or more sides without turning back, you will save valuable moves
and time.

o Watch the computer solve the cube a few times.  Then try using some
of the same strategies that Hubie uses to complete the cube.

o Notice there is one extra square of color per game (for instance,
one extra square of blue).  This will be the _last_ square Hubie picks
up to win the game.

8. GAME SELECT MATRIX

         ____________________ Game Variation
         |  _________________ Speed ( N = Normal, F = Fast )
         |  |  ______________ Scoring ( M = Moves, T = Time )
         |  |  |   __________ Blacked Out
         |  |  |   |   ______ Restricted Movement
         |  |  |   |   |   __ Computer Play
         |  |  |   |   |   |
         V  V  V   V   V   V
        ---------------------
         1  N  M |   |   |
        ---------|---|---|---
         2  N  T |   |   |
        ---------|---|---|---
         3  N  M | X |   |
        ---------|---|---|---
         4  N  T | X |   |
        ---------|---|---|---
         5  N  M |   |   | X
        ---------|---|---|---
         6  N  T |   |   | X
        ---------|---|---|---
         7  N  M | X |   | X
        ---------|---|---|---
         8  N  T | X |   | X
        ---------|---|---|---
         9  N  M |   | X |
        ---------|---|---|---
        10  N  T |   | X |
        ---------|---|---|---
        11  F  M |   |   |
        ---------|---|---|---
        12  F  T |   |   |
        ---------|---|---|---
        13  F  M | X |   |
        ---------|---|---|---
        14  F  T | X |   |
        ---------|---|---|---
        15  F  M |   |   | X
        ---------|---|---|---
        16  F  T |   |   | X
        ---------|---|---|---
        17  F  M | X |   | X
        ---------|---|---|---
        18  F  T | X |   | X
        ---------------------

CO19741-70 REV. 1 2670
(c) 1983 ATARI, INC. ALL RIGHTS RESERVED
Printed in U.S.A.

[ This manual was hand-typed, using only the finest natural
ingredients, by Bryan Raynor.  Feel free to address comments/questions
to btr9p@virginia.edu ]

A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.

* v5: Stickiness was added back and stochastic frame-skipping was removed. The environments are now in the "ALE" namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release
