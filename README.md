# SightPlusPlus
Our main code can be found on Github at this link: https://github.com/SightPlusPlus. As this project is quite big, we had to divide the code into multiple repositories.



# SightPlusPlus-Web_portal

## Main
The repository named SightPlusPlus-Web_portal is a presentation website for developers. To see the website, just download the code and open index.html.

The project itself is placed inside the other 3 repositories. So to run it, you would need a Realsense camera and a NUC computer from Intel (but the NUC computer is not mandatory, you can still run the code using your personal computer).

## Reference
The bootstrap template from [Start Bootstrap - Clean Blog](https://startbootstrap.com/theme/clean-blog/)



# SightPlusPlus-Server
Firstly, let’s start by starting the C++ Server - SightPlusPlus-Server (which was already
done by other Postgraduates students when we put our hands on this project).

*** NOTE 1: These explanations are taken from the ReadMe written by the old team.

*** NOTE 2: This system is meant to work on NUC computers. Because of this, you may have troubles running it on Apple computer as it should run on Windows computers. We know that because we had troubles running it on our Apple laptops.

## Installation and Development
This project uses Vcpkg for library dependencies. Install the following libraries with Vcpkg to run the solution (make sure to install the 64-bit versions, as this system is being developed with 64-bit systems in mind):

    ● realsense2
    ● opencv3
    ● opencv3[contrib] 
    ● tbb
    ● websocketpp
    ● spdlog
    ● GTest

## Installation and Run Manual of CMAKE 
This section is an instruction guide on how to install and run CMake. This will include a guide for building in windows power shell as well as within Microsoft Visual Studio 2019. Running the system with CMake has the same requirements as with the original version. This guide includes the use of vcpkg, and it is assumed that CMake is installed on your system.

## Open with VS
1. Startup Visual Studio and select "Open local Folder".

2. Navigate inside /Intel_SighPP_CMake and click select folder.

3. Right-click on the top-level CMakeLists.txt and select CMake Settings. This will open a new JSON page to instruct VS on how to build the system.
   
4. Following, Add the path to your vcpkg.cmake file to "CMake Toolchain file". This is roughly "/scritps/buildsystems/vcpkg.cmake".

5. You will now be able to compile the system given you have installed everything correctly.

6. Right-click on the top-level CMakeLists.txt and click Generate cache. This will build the base build instructions for the CMake system.

7. Finally, to build the executable under the build tab select rebuild all.

8. The executable files will now be within the ./build directory.

## Running the software within VS
Now that you have built the CMake, you can run the system in debug mode from Visual Studio.

NOTE: You may need to copy the models folder to the location of the executable as this is needed, especially if you changed the build directory.

There are a few options.

### Option 1, target view:
In this method, first, navigate to the solution explorer to the right to the home icon. Right-click the "switch view" icon and select the CMake target view.

You will now see the executables of the project.

To run the main project, navigate to "Intel_SightPP"

At this point, if you would like to edit the run arguments right-click the executable and select "add debug configuration."

Within the JSON object add the attribute args:[ "" ] and add the arguments you required

Finally: Either select Debug within the executable or set the item as Startup item and run from the top panel.

### Option 2:
To set the run arguments, right-click on the top-level CMake and select add build configuration, select default.

within the JSON object add the attribute args:[ "" ] and add the arguments you required

Next, either, you can right-click on the top .txt file and select debug, or you can set the text file as the Startup Item and run the software from the top control panel as usual.

Following you can run the executable such as Inter_SightPP.exe with the flags following.

## Flags
Flags for running the system include:

    ● realsense
        ○ This is used to run the system from the camera.
    ● -rec hello.bag
        ○ This is used to record the current input into a file with the name following the flag.
    ● -play hello.bag
        ○ This is used to play the file from the file following the flag. 
    ● -depth
        ○ This is used to show the depth stream in a window 
    ● -color
        ○ This is used to show the color stream in a window 
    ● -port
        ○ This is used to select the port the WebSocket server runs on, default is 7979 
    ● -caffe no_bn
        ○ This is used to import the caffe-based network named no_bn.caffemodel etc. 
    ● -outdoors
        ○ This is used to set up object detection networks, frame resolution and the prioritiser for outdoors environment.
    ● -indoors
        ○ This is used to set up object detection networks, frame resolution and the prioritiser for indoors environment.
    ● -covid
        ○ This is used to set up object detection networks, frame resolution and the prioritiser for Outdoors environment and uses a prioritiser that enforces social distancing.

## Real Life approach:
Connect the Realsense camera(s) and add the “realsense -outdoors” flags (for outdoors moving) or “realsense -indoors” flags (for indoors moving).



# SightPlusPlus-Client
After installing and successfully running the SightPluslus-Server, it’s time for the Client-side.

## Prerequisites
1. Install Node.js. Download the installation package from the official website of Node.js. Choose the LTS version. I am using NodeJS version 11.0, but any of them will work.

2. (For Windows) Add the installation directory into the environment variables of your OS.

## Run it
After you download the project package and extract it, open CMD in the ‘client’ folder. Run these commands below:
`npm install`
IMPORTANT! Please run the SightPlusPlus-Server before running SightPlusPlus-Client. A Connect Error will appear otherwise.

Now navigate to the client/src/ folder.

If you need to use the remote functions of the system, run in the terminal:
`node start_remote.js`
IMPORTANT! ALL 3 SYSTEMS (APP, SERVER, CLIENT) NEED TO BE ON THE SAME NETWORK TO WORK.

If you want to use the remote functionalities, run in the terminal (make sure you change the latitude and longitude with the desired coordinates):
`node start_static.js <latitude, longitude>`

That is it, now the Client should receive messages from the Server.



# SightPlusPlus-App
To use the app you can download the APK from here:
https://liveuclac-my.sharepoint.com/:u:/g/personal/zcabvud_ucl_ac_uk/EQxxIyK-tgZPnFGgm_Zo7zIBs09yk71X4JQooh_0qJq0sg?e=9JUZe1

Download it on your Android phone and install it. Now you can use the app. Make sure you download and start the Server and the Client systems first.


You can also download the code and run it on an emulator, or even emulate it on your own device. Now press the screen and tell the system to START, STOP, change SPEED (e.g SPEED 0.6), VOLUME (e.g Volume 0.6) or PITCH (e.g PITCH 0.6), turn on/off the VIBRATION (e.g VIBRATION on) or start the system for the static cameras (by saying “location”). Double-tap the screen to warn that there was an error with the recognized object.

To work on the code, you need to install the Flutter SDK. You can do it from here: https://flutter.dev/docs/get-started/install.

Now you need to set up an editor. We recommend using Android Studio, but it’s up to you. You need to install the Flutter and Dart plugins. Now everything should work

If you need to create a new APK, just type in the terminal (make sure you are in the root folder) flutter build apk.


NOTE: The client and the app are using Firebase. The credentials should be changed.
