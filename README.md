#include <Sparki.h> // include the sparki library
float B = 0.0;
float R = 1.1;
void setup()
{
    sparki.servo(SERVO_CENTER); // Center the Servo
}
void loop()
{
    sparki.RGB(0, 0, B);
    sparki.moveForward(); // move Sparki forward
    int cm = sparki.ping(); // measures the distance with Sparki's eyes
{
    B += 0.1;
    R += 0.1;
    sparki.RGB(100*abs(sin(R)), 0, 100*abs(sin(B)));
    delay(100);

    if(cm != -1) // make sure its not too close or too far
    { 
        if(cm < 20) // if the distance measured is less than 20 centimeters
        {
            sparki.beep(); // beep!
            sparki.moveBackward(10); // back up 10 centimeters
            sparki.moveRight(30); // rotate right 30 degrees
            delay(1000);
        }
    }
    delay(100); // wait 0.1 seconds (100 milliseconds)
}

