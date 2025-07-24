# driving32 Statefile

*Made by jacober-calc for the SwissMicros DM32*

## Note from the Author

You will find the most recent version and information on this Statefile in this GitHub repo. While the file is hosted on the [official SwissMicros forum](https://forum.swissmicros.com), we do not guarentee that any version other than what is found here is the most up to date. Additionally, any reports on issue or bugs with the program, including contributions on further developments, will only be actioned via this GitHub repo. Thank you for being interested in the **driving32 Statefile** project and helping to make the state file more useful for users to come!

## Install and Download

You can find instructions on how to install .d32 Statefiles to your calculator [via the DM32 User Manual](https://technical.swissmicros.com/dm32/doc/dm32_user_manual.html#_saving_and_loading_a_state). The process is extremely simple. You can download the .zip file from the release page from this GitHub repository.

Consulting this **Readme.md** before use is highly recommended. The program is simple enough to use, but the readme contains useful information. The file you will want to install on your calculator from the .zip file is **Driving.d32**.

## Routines and Instructions

Contained within the Statefile you will find 8 subroutines labelled as follows:

> - **LBL S** / 0133 lines / STOPDIST routine
> - **LBL P** / 0101 lines / PHYSICS routine
> - **LBL G** / 094 lines / GFORCE routine
> - **LBL D** / 084 lines / DFORCE routine
> - **LBL T** / 088 lines / TFORCE routine
> - **LBL M** / 043 lines / MIRRORS routine
> - **LBL K** / 066 lines / KICKOUT routine
> - **LBL W** / 056 lines / WEIGHT routine

Each routine is explained in greater detail below.

### LBL S: STOPDIST Routine

The STOPDIST routine calculates the safe stopping distance of a vehicle using speed, reaction time (seconds), friction (coefficient) and slop as variable inputs by the user. The calculation used is based on the official AASHTO formula.

![Four-line stack variable input.](https://i.imgur.com/9LQN49q.jpeg)

To use this program the user inputs the variables on to the four-line display stack. The order is important. Velocity in km/h is placed in the t-register (added first by the user), reaction time in seconds is placed in the z-register (added second by the user following ENTER after velocity variable), friction coefficient is placed in y-register (added by user third), and grade is placed in the x-register, added last by the user. The program will not function correctly without all registers filled with the appropriate variable, so any blank variables should be filled with a "0".

![Results on four-line display at the end of STOPDIST routine.](https://i.imgur.com/azJcKRQ.jpeg)

Once the stack is full the user simply selects XEQ S to run the STOPDIST routine. Once complete the display will show three pieces of information on the z,y, and x-registers. In the z-register the program will display the distance travelled (in meters) during the reaction time, the y-register will show the distance travelled while braking, and the x-register will show the total stopping distance (value of z-register plus value of y-register).

The following variables are used by the routine:

> - Variable B / Braking distance
> - Variable F / Friction coefficient
> - Variable R / Reaction time
> - Variable S / Stopping distance
> - Variable T / Reaction distance
> - Variable V / Velocity in meters per second

### LBL P: PHYSICS Routine

The PHYSICS routine takes velocity (km/h) and weigh (kg) and produces standard physics values for momentum and kinetic energy.

![User input for PHYSICS routine.](https://i.imgur.com/xzyvH1U.jpeg)

The user inputs the velocity (km/h) in the y-register (first by the user followed by ENTER), and the weight (kg) in the x-register. The program is running by pressing XEQ P.

![Results of the PHYSICS routine.](https://i.imgur.com/nCMf9Zh.jpeg)

All four lines of the stack are used when the program ends. On the t-register the program displays the velocity converted to meters per second (m/s), on the Z-register the program recalls the weight inputted by the user (kg), in the y-register the program displays kinetic energy in joules (J), and in the x-register the program momentum in kilogram meters per second (kg⋅m/s).

The following variables are used by this routine:

> - Variable E / Kinetic energy
> - Variable M / Momentum
> - Variable V / Velocity in meters per second
> - Variable W / Weight

### LBL G: GFORCE Routine

The GFORCE routine takes velocity (km/h) and desired g-force experienced (g) and produces results for stopping (distance, deceleration rate, time and g-force). This routine works in conjuntion with the DFORCE and TFORCE routines with each acting as the single-variable input initiator for the final product.

![GFORCE routine user input.](https://i.imgur.com/IAmrUMi.jpeg)

The user inputs velocity (km/h) in the y-register (first entry by the user followed by ENTER) and the desired g-force (g) in the x-register (last by the user). The program starts by pressing XEQ G.

![GFORCE final results display.](https://i.imgur.com/Pwhu93G.jpeg)

The program displays information on all four lines of display. In the t-register the program displays the braking distance (m), in the z-register the program displays deceleration (m/s), in the y-register the program displays braking time (s), and in the x-register the program displays braking g-force (g).

The following variables are used by this routine:

> - Variable A / Deceleration rate
> - Variable D / Distance
> - Variable G / GForce
> - Variable T / Time
> - Variable V / Velocity in meters per second

### LBL D: DFORCE Routine

The DFORCE routine takes velocity (km/h) and desired distance (m) and produces results for stopping (distance, deceleration rate, time and g-force). This routine works in conjuntion with the GFORCE and TFORCE routines with each acting as the single-variable input initiator for the final product.

![DFORCE user input display.](https://i.imgur.com/TF5AMTP.jpeg)

The user inputs velocity (km/h) in the y-register (first entry by the user followed by ENTER) and the desired distance (m) in the x-register (last by the user). The program starts by pressing XEQ D.

![DFORCE final results display.](https://i.imgur.com/OcKbgpM.jpeg)

The program displays information on all four lines of display. In the t-register the program displays the braking distance (m), in the z-register the program displays deceleration (m/s), in the y-register the program displays braking time (s), and in the x-register the program displays braking g-force (g).

The following variables are used by this routine:

> - Variable A / Deceleration rate
> - Variable D / Distance
> - Variable G / GForce
> - Variable T / Time
> - Variable V / Velocity in meters per second

### LBL T: TFORCE Routine

The TFORCE routine takes velocity (km/h) and time (s) and produces results for stopping (distance, deceleration rate, time and g-force). This routine works in conjuntion with the GFORCE and DFORCE routines with each acting as the single-variable input initiator for the final product.

![TFORCE user input display.](https://i.imgur.com/YRv8Q9G.jpeg)

The user inputs velocity (km/h) in the y-register (first entry by the user followed by ENTER) and the desired time (s) in the x-register (last by the user). The program starts by pressing XEQ T.

![TFORCE final results display.](https://i.imgur.com/6GCNYUk.jpeg)

The program displays information on all four lines of display. In the t-register the program displays the braking distance (m), in the z-register the program displays deceleration (m/s), in the y-register the program displays braking time (s), and in the x-register the program displays braking g-force (g).

The following variables are used by this routine:

> - Variable A / Deceleration rate
> - Variable D / Distance
> - Variable G / GForce
> - Variable T / Time
> - Variable V / Velocity in meters per second

### LBL M: MIRRORS routine

The MIRRORS routine takes velocity (km/h) and time between mirror checks (s) and calculates the distance travelled between mirror checks. Additionally, the program converts velocity into meters per second in the final display to provide a comparion to the distance travelled between mirror checks.

![MIRRORS user input display.](https://i.imgur.com/ZNGgfBs.jpeg)

The user inputs velocity (km/h) in the y-register (first entry by the user followed by ENTER) and the time between mirror checks in second (s) in the x-register (last by the user). The program starts by pressing XEQ M.

![MIRRORS final results display.](https://i.imgur.com/VQIJcgF.jpeg)

The program displays information in the y-register and the x-register. In the y-register is displayed the velocity in meters per second (m/s). In the x-register is displayed the distance in meters (m) between mirror checks.

The following variables are used by this routine:

> - Variable D / Distance between mirror checks
> - Variable T / Time between mirror checks
> - Variable V / Velocity in meters per second

### LBL K: KICKOUT Routine

The KICKOUT routine calculates the overhang of a vehicle (over a curb or into a turn) based on the turning angle and distance off curb (or track). The routine includes a feature for the user to input a customized overhang distance for a particular vehicle, and average figures for a personal vehicle and transit bus are provided in the program for ease of use.

Note: ensure the calculator is in DEGREE MODE prior to running this program.

![KICKOUT user input display.](https://i.imgur.com/y70FKEG.jpeg)

The user first enters the turning angle in degrees (deg) into the y-register (first entered by the user followed by ENTER). The user then enters the distance off the curb in meters (m) into the x-register (entered last by the user). The program is started by pressed XEQ K.

![Overhang variable prompt.](https://i.imgur.com/V1HK0th.jpeg)

The user is promoted to provide an overhang value in meters (m). There are two values provided in the y-register and z-register. These are average values for a passenger vehicle (y-register) and a transit bus (z-register). 

![Overhang provided data.](https://i.imgur.com/cdQYpEZ.jpeg)

The user can use these values by pressing R(DOWN) until the value is in the input field followed by R/S to continue the routine. The user can also enter their own values and input the figured by pressing R/S to continue the routine.

![KICKOUT final results display.](https://i.imgur.com/sXjEd12.jpeg)

The final results are displayed on all four lines. In the t-register the turning angle the user input is displayed in degrees (deg), in the z-register the distance off the curb in meters (m) is displayed, in the y-register the overhang value in meters (m) is displayed, and in the x-register the overhang distance in meters (m) is displayed.

The following variables are used by this routine:

> - Variable A / Turning angle
> - Variable D / Distance off curb
> - Variable K / Kickout distance
> - Variable O / Overhang distance

### LBL W: WEIGHT Routine

The WEIGHT routine takes the number of adults and the number of children in a vehicle and using the official Transport Canada official weights, produces a total passenger count and weight in kilograms (kg).

![WEIGHT user data input display](https://i.imgur.com/6bQCrDZ.jpeg)

The user simply enters the number of adults in the y-register (first followed by ENTER) and the number of children in the x-register (second data provided after ENTER). The program is started by selecting XEQ W.

![WEIGHT final results display.](https://i.imgur.com/NDbRIB2.jpeg)

The program uses the y-register and the x-register to display the final results. In the y-register is the total number of passengers in the vehicle. In the x-register is the total weight in kilograms (kg) based on Transport Canada figures.

The following variables are used by this routine:

> - Variable A / Number of adults
> - Variable C / Number of children
> - Variable P / Total number of passengers
> - Variable W / Total weight

## Units Used

All units used throughout this Statefile are SI. Velocities are inputted by the user in km/h and often displayed in m/s for useful comparison to other data points. Weights are in kilograms. And all distances are in meters.

## Disclaimer

Nothing in this Statefile should be used for real-world driving applications. All of the physical calculations are based on theoretical Newtonian physics at the level of a high school student. While the Statefile has tremendous use in classroom and instructional settings for professional drivers or young drivers learning the road, the formulas used do not stand up to the rigor of real-world application.

## By jacober-calc for SwissMicros DM32

> - [SwissMicros Website](https://www.swissmicros.com)
> - [DM32 product page](https://www.swissmicros.com/product/model-dm32)
> - [SwissMicros full products page](https://www.swissmicros.com/products)
> - [DM32 Online User Manual](https://technical.swissmicros.com/dm32/doc/dm32_user_manual.html)
> - [SwissMicros Calculator Forum](https://forum.swissmicros.com/index.php)

![jacober-calc](https://i.imgur.com/YVqd59l.png)
