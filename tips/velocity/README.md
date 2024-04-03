# Velocity Tuning

The following is a quick tip for working with our code base and the
wpilib math library to set up velocity tuning on the motor system,
as well as an overview of how PID works in general

## Our Code Base

### Theory

There is an EncoderMotor class inside of our components system. You
can find it in components/motor/EncoderMotor.py

This class takes in an encoder object and a motor object (motor set in
voltage mode), and uses the encoder to provide the given motor with
velocity and position controls. The idea here is to keep the velocity
and position logic iscolated from the rest of the code and in one location,
so it's easy to swap out motor logic and type in the code.

Basically we can think of this as a logical motor.


## Implementation

In order to add velocity to the motor, we will need to use a pid computation
inside of the set function of the motor class, specifically in velocity mode.

more or less it should be as simple as:


```python
def set(self,val):
    if self.mode == MotorModes.velocity:
        self.motor.set(self.pid.calculuate(self.get_velocity(),value))
```

The devil of course is in the details with this particular implementation.

### devilish details

the get\_velocity() function was created before our knowledge of .getRate() on the
wpilib.encoder class. If at all possible we want to be useing the getRate off of the built
in class for a more accurate reading. 
We actually have this code on one of our other commits
in the git repo, but it's simple enough that we should be able to add it back in (as at the time
of writing we do not have it in the main branch on commit f9bdfc0).

When we did testing with this initially we found that there tended to be a lot of noise off of this 
particular sensor, so to account for that we are probably going to want to use an averageing function
to smooth out the errors were getting from the sensor.

We have a pre-built solution for doing circular averages in the code in the utils/math/algebra.py file under the class
RotatingAverage, I would use that for this, with probably a fairly high default on the incoming signal.

So you would get something like.


```pthon
def get_velocity(self):
    return self.rotating_average.set_through(
        self.encoder.getRate()
    )

```

## PID stuff

for tuning the PID values we are probably GOING to have to have an I value off of the PID. This is because with velocity mode,
our ending value will have some minimum position, if we just use a proportion control, when we have zero error, we will
have zero output from the system. As a result we REALLY want to make sure that we have a large enough I value for setting our
velocity or we well never converge on a set velocity value.
