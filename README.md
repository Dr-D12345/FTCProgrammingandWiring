# Basics of FTC Wiring and Programming

###### Provided Francis Lewis High School Robotics



## Fundamentals of Wiring

Wiring is one of the most crucial parts of robot. It is one of the biggest factors within preventing errors and making a presentable robot, however it often doesn't receive the care and attention it deserves. So today, we are going to speak on some key things to remember when you are wiring your robot. 	

**Mounting the Android Phone	**

When mounting the Android phone, some things to key mind include are:

- DO NOT mount the Phone on any metal objects, because this makes it susceptible to electrostatic discharge
- Be resistant to in-casing the phone in metal for it can interfere with the phone’s WiFi Connection
- Please speak with your programmer when choosing a place the phone is to be mounting the phone, in case your team chooses to use the phone’s camera for the Autonomous period with Vuforia
- All wires should be securely connected and should not be place in an area where they could possible be damaged

**Common Issues**

- Connection Issues
  - Inspect the ports on all modules
  - Isolating electronics from the metal components of the robot dramatically reduces connection issues
  - Make sure all cords are high quality and plugged correctly into modules
- Haphazard Wiring
  - Leads to Faulty Connections
  - Broken Wires
  - Difficulties troubleshooting
  - Solution: Allot time for wiring Make Wiring diagrams
  - And make distinguishing marks on the wires to tell differences

## Programming Sensors

Sensors are crucial when developing for the autonomous period. They provide heightened awareness of the robots surroundings allowing for more accurate and higher scoring auton. Today we are going to speak about 3 different sensor:

- Color Sensor

  - Responsible for defining colors and are more accurate than light sensor

  - ```java
    ColorSensor colorSensor;
    @Override
    	public void init() {
    		colorSensor = hardwareMap.get(NormalizedColorSensor.class, "sensor_color");
             colorSensor.enableLed(true);//set true or false based on how much light the color sensor is receiveing
    	}
    @Override
        public void loop() {

        telementry.addData("Red", colorsensor.red());
        telementry.addData("Blue", colorsensor.blue());
        telementry.addData("Green", colorsensor.green());
          if(colorsensor.blue>colorsensor.red()){
            //object is more blue than red
          }

        }
    ```

- Optical Distance Sensor

  - Detects differences in the distance from a target surface using a pulsed light

  - ```java
    OpticalDistanceSensor opticalDistanceSensor;
    @Override
    	public void init() {
    		opticalDistanceSensor = hardwareMap.get(OpticalDistanceSensor.class, "sensor_ods");

        }
    @Override
        public void loop() {
        telementry.addData("Amount of Waves detected",opticalDistanceSensor.getLightDetected());


        }

    ```

- Gyro Sensor

  - Reads rate of rotation around X,Y, Z axes
  - Allows for more accurate turns

  ```java
  Gyroscope gyroscope
  @Override
  	public void init() {
  		gyroscope = hardwareMap.get(Gyroscope.class, "sensor_gyro");

      }
  public void loop() {
   telemetry.addData("rate", "%.4f deg/s",      gyroscope.getAngularVelocity(AngleUnit.DEGREES).zRotationRate);

  }

  ```

  ​



   
