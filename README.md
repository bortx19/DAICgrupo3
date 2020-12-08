# DAICgrupo3

import time
from grove.gpio import GPIO

buzzer = GPIO(5, GPIO.OUT)
led1 = GPIO (16, GPIO.OUT)
led2 = GPIO (18, GPIO.OUT)
led3 = GPIO (26, GPIO.OUT)

button1 = GPIO(22, GPIO.IN)
button2 = GPIO(24, GPIO.IN)

contador = 0


while True:        
    if button1.read():
        buzzer.write(1)
        time.sleep(0.2)
        
        if button1.read():
            print("MAL")
        else:
            if contador == 3:
                contador = 0
                print(contador)

            else:
                contador = contador + 1
                print(contador)
    else:
        buzzer.write(0)
    
    if contador == 0:
        
        led1.write(0)
        led2.write(0)
        led3.write(0)
        buzzer.write(0)
        
    elif contador == 1:
        
        led1.write(1)
        led2.write(0)
        led3.write(0)
        buzzer.write(0)
        
        #if button2.read():
        #while contadortiempo1 > 600s:
        #empezar la cuenta atras del contadortiempo1
        #parpadeo del led1
        
        #while contadortiempo1 >0 and <=600s:
        #continuar con el contadortiempo1 hasta q llegue a 0
        #aumentar el parpadeo del led
        
        #if contadortiempo1 == 0:
        #buzzer.write(1)
        #contador = 0
    
    elif contador == 2:
        led1.write(0)
        led2.write(1)
        led3.write(0)
        buzzer.write(0)
       
    elif contador == 3:
        led1.write(0)
        led2.write(0)
        led3.write(1)
        buzzer.write(0)
    
    time.sleep(0.1)
   
