# The effect of bot type on score in the game pong
#### By Ian Koide

## Bot #1 Explained
```
paddle.y += paddle.velocity
```
Bot #1 is the simplest of the bots, its constantly moving down.

## Bot #2 Explained
```
if ball.y > paddle.y:
    paddle.y += y.velocity
if ball.y < paddle.y:
    paddle.y -= paddle.velocity
```
Bot #2 is also pretty simple. If the balls y position is above the paddle then the paddle moves up, if its bellow it moves down.

## Bot #3 Explained
```
if ball.y <= 180 and paddle.y >= 540:
    paddle.y += paddle.velocity

elif ball.y >= 540 and paddle.y <= 180:
    paddle.y -= paddle.velocity

else:
    if ball.y > paddle.y:
        paddle.y += paddle.velocity

    if ball.y < paddle.y:
        paddle.y -= paddle.velocity
```
Bot #3 is similar to bot #2 except that if the ball is above a certain height and the paddle is bellow a certain height then the ball will move in the opisite direction taking less time to get to the ball. It is the same when the ball is bellow a certain point and the paddle is above a certain point.

## Bot #4 Explained
```
global target

if ball.x > 1060 and ball.x < 1080:
    # Up
    if ball.yvelocity / 17 == 1: # If the ball is moving up
        if ball.y > 360:
            target = (1080 - ball.y) - (paddle.height / 2) + 17
            print(paddle.y , "Single Up")

        elif ball.y < 360:
            target = (360 + ball.y)  - (paddle.height / 2) # Wrong
            print(paddle.y , "Double Up")

    # Down      
    else: # If the ball is moving down
        if ball.y < 360:
            target = (360 - ball.y) + (paddle.height / 2) - 17 # Wrong
            print(paddle.y , "Single Down")

        if ball.y > 360:
            target = (ball.y - 360) - (paddle.height / 2)
            print(paddle.y , "Double Down")

if target > paddle.y:
    paddle.y += paddle.velocity

elif target < paddle.y:
    paddle.y -= paddle.velocity

else: 
    pass

```
Bot #4 calculates where the ball will end up on the side of the screen with the paddle. The first if statement is to check if the ball is in the calculation range. The next if statement inside the first is checking if the balls velocity is positive or negative. If it is positive and the starting ball y position is greater than 360 then it has to be a single bounce moving up. Then you use the formula screen width - ball y position to find where the ball will end up. After that you have to subtract the paddle height divided by 2 because the x position of the paddle is in the top corner not the middle. Then add the velocity of the paddle. See Bugs.