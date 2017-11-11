# Basics of FTC Wiring and Programming

###### Provided Francis Lewis High School Robotics

This is a basic guide describing the  basics of java programming, wiring and FTC programming



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

[Java Basics](https://github.com/Dr-D12345/FTCProgrammingandWiring/blob/master/bascis_in_java.md)

Sensors are crucial when developing for the autonomous period. They provide heightened awareness of the robots surroundings allowing for more accurate and higher scoring auton. Today we are going to speak about 3 different sensor:

- Color Sensor

  - Responsible for defining colors and are more accurate than light sensor

  - ```java
    ColorSensor colorSensor;

        @Override
        public void init() {
            colorSensor = hardwareMap.get(ColorSensor.class, "sensor_color");
            colorSensor.enableLed(true);//set true or false based on how much light the color sensor is receiveing
        }

        @Override
        public void loop() {

            telemetry.addData("Red", colorSensor.red());
            telemetry.addData("Blue", colorSensor.blue());
            telemetry.addData("Green", colorSensor.green());
            if (colorSensor.blue() > colorSensor.red()) {
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
  GyroSensor  gyroSensor;
      @Override
      public void init() {
          gyroSensor = hardwareMap.get(GyroSensor.class, "sensor_gyro");
          gyroSensor.calibrate();
      }

      public void loop() {
         telemetry.addData("X value: ",gyroSensor.rawX());
          telemetry.addData("Y value: ",gyroSensor.rawY());
          telemetry.addData("Z value: ",gyroSensor.rawZ());
      }
  ```

## Autonomous programming. Decoding the encrypted code.

**Different Types of Opmodes**

- OpMode

  - Used primarily during the driver controlled period

  - Uses input of gamepad to perform tasks

  - Operates on a continuous loop

  - Never Ends and can only end on by the driver

  - ```java
    //A very Basic Opmode
    //decleration of the 2 motors
    private DcMotor leftDrive = null;
    private DcMotor rightDrive = null;

    @Override
        public void init() {//the function that gets intialized once the driver hits init
            telemetry.addData("Status", "Initialized");

          //getting the
            leftDrive  = hardwareMap.get(DcMotor.class, "left_drive");
            rightDrive = hardwareMap.get(DcMotor.class, "right_drive");
          //settting the direction so no values need to be inversed
           	leftDrive.setDirection(DcMotor.Direction.FORWARD);
            rightDrive.setDirection(DcMotor.Direction.REVERSE);

        }
    @Override
        public void loop() {//the part that starts once the driver hits play
           //setting the motor power based on the input of the game pad
            leftDrive.setPower(gamepad1.left_stick_y);
            rightDrive.setPower(gamepad1.right_stick_y);

        }

    ```

- Linear OpMode

  - Operates during the Autonomous period

  - Operates Linearly(from beginning to end)

  - Stops once it reaches the end of the program

  - Initiated by the drivers team

  - ```java
    //A very Basic LinearOpmode
    //decleration of the 2 motors
    private DcMotor leftDrive = null;
    private DcMotor rightDrive = null;
      @Override
        public void runOpMode() throws InterruptedException{
    	//initalize motors
           leftDrive  = hardwareMap.get(DcMotor.class, "left_drive");
           rightDrive = hardwareMap.get(DcMotor.class, "right_drive");

          waitForStart();
          //go full power
          leftDrive.setPower(1)
          rightDrive.setPower(1)
          Thread.sleep(4000);//wait for 4 seconds
          //turn off motors
          leftDrive.setPower(0)
          rightDrive.setPower(0)
        }//end

    ```

**Vuforia**

- Vuforia is a simple image processing framework and it does most of jobs for you compare to OpenCV.


- Vuforia allows you to simply scan in objects and download them to the phone. This is the simplest way of using computer vision in the FTC game to decode the Crypto Box.

- ```java
  VuforiaLocalizer vuforia;
  @Override
      public void init() {//the function that gets intialized once the driver hits init
          telemetry.addData("Status", "Initialized");
        //find the camera
        int cameraMonitorViewId = hardwareMap.appContext.getResources().getIdentifier("cameraMonitorViewId", "id", hardwareMap.appContext.getPackageName());
        //inialize the vufoira
        VuforiaLocalizer.Parameters parameters = new VuforiaLocalizer.Parameters(cameraMonitorViewId);
        //see the key
  parameters.vuforiaLicenseKey = "ATsODcD/////AAAAAVw2lR...d45oGpdljdOh5LuFB9nDNfckoxb8COxKSFX";

    this.vuforia = ClassFactory.createVuforiaLocalizer(parameters);
        //loading the assets
    VuforiaTrackables relicTrackables = this.vuforia.loadTrackablesFromAsset("RelicVuMark");
          VuforiaTrackable relicTemplate = relicTrackables.get(0);
          relicTemplate.setName("relicVuMarkTemplate"); // can help in debugging; otherwise not necessary


      }

  public void loop(){
     telemetry.addData("VuMark", "%s visible", vuMark);//just like get the data from the cryptobox

  }
  ```

  ​

## Additional Resources

[PowerPoint](https://docs.google.com/presentation/d/14HG1e36PG30nOiCY_7Dr6g6dsKZz9uHJGXEXTaaPF9s/edit?usp=sharing)

[VuforiaHomePage](https://www.vuforia.com/)

[FTC Offical Wiki](https://github.com/ftctechnh/ftc_app/wiki)



  ​
