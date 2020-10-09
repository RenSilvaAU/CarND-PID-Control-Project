# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

## Ren Silva - Udacity


# Reflection

It is interesting that I am going through this exercise at the same time that I am tuning a simulation in [skoods](https://skoods.org).

The skoods car is, in fact, much harder to control than this one. So - the parameters I tuned there were a fantastic starting point to tune Udacity's car.

## Steering Control
This is how I manually tuned the **steering** PID controller:

### P - Proportional
The **P** parameter is what makes the car respond to changes in direction. The larger the P parameter, the faster the car responds to changes in course. The problem withe P parameter is that it overshoots - and the car drives like a child driving a toy car (it reminds me of Arnold Schwarzenegger's character in "Twins") - and it needs another parameter: the "Derivative".

### D - Derivative  
The **D** parameter is what makes the go back to back to a straight line after it overshoots. The larger it is, the faster the car will go back to a straight line after it changed direction. Too fast, and it waits for the next command too quickly. 

### I - Integral  
The **I** parameter lets the car correct the accumulated direction error. Too small, and it never corrects itself. Too large, and the car moves back too fast (zig-zagging madly like Schwarzenegger’s character). I started from zero and just made it large enough to slowly correct its course, at the same time as the car responds to changes in course (from parameter P).

## Throttle Control
I started with constant acceleration of 0.3 - but it became clear that I would never beat any speed record with that.

So, I experimented with a few options. 
### P - Proportional
Th **P** parameter was my main parameter for the throttle. The idea is simple: if CTE is larger, the car needs to slow down (we don't want to run fast when we are steering hard), so the P parameter was set lower when the error is higher and vice-versa.
### D - Derivative 
Same principle: the lower the error, the more dampening we use to make acceleration smoother.
### I - Integral  
I set it to zero and left it there - the accumulated CTE should not influence acceleration.

## Result
The result is shown in this video:

<a href="https://www.youtube.com/watch?v=UoNyG5H5PLk">
<img src="https://github.com/RenSilvaAU/CarND-PID-Control-Project/blob/master/pics/renslap.png?raw=true" width=40%/>
</a>




