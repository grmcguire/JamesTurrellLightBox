# JamesTurrellLightBox

## [Creator Statement](https://github.com/grmcguire/JamesTurrellLightBox/blob/ae182644c95c7d1ce381249f6c5b642e51b7d683/Creator%20Statement)
Click the link to access my statement on the tech of my project and the usefulness of it

## Documentation
### My Code

from gpiozero import LightSensor, Buzzer
import time
import pigpio #library for controlling LED lights

pi = pigpio.pi()


ldr = LightSensor(4)  # pin I used
while True:
    light = float(ldr.value) #recieves value pertaining to the amount of external light
    red = (light * -255) + 255 #equation making there less red the lighter it is
    green = (((light - .5)**2)*-600) +255 #parabola equation pertaining to the amount of green light
    blue = light * 255 #equation making there more blue the lighter it is
    pi.set_PWM_dutycycle(17, red)
    pi.set_PWM_dutycycle(22, blue)
    pi.set_PWM_dutycycle(24, green)
    time.sleep(1)
    print(ldr.value)
