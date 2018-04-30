# ARGame
The Complete Instructions to Get Where I Am Now, In Hopefully Much Less Time:

Step one is basically this: https://docs.microsoft.com/en-us/windows/mixed-reality/install-the-tools
1.	Install Unity, make sure to install the “Windows Store .NET Scripting Backend” with it in the install wizard.
2.	Install Visual Studio 2017 (Community which is free is fine). After installation, say edit and make sure you have Universal Windows Platform and Game Development with Unity selected. Think of these as SDKs.

You can ignore everything else on this webpage. That said, things you need to do with your HoloLens:
1.	First off, go to the Main menu -> Settings -> Update -> Reset (this seems extreme but trust me if you don’t you can’t retie the device to your Microsoft account and so basically can’t do anything)
2.	Wait for reboot, go back into Settings -> Update -> For developers and Enable Developer Mode.
3.	Do ^ on your development PC.
4.	You can’t do it right now unless you have Visual Studio open, but this is the same screen on the HoloLens you’ll need to be on to pair the devices later.
5.	Now on the HoloLens, Main menu -> Windows Store -> search for “Holographic Remoting Player” -> hit “Free” to install.

Now for setting up a project in Unity:
Basically this is all in https://docs.microsoft.com/en-us/windows/mixed-reality/holograms-100 & https://docs.microsoft.com/en-us/windows/mixed-reality/holograms-101 but this is like, the quick start version.
1.	Follow Holograms 100 up to Chapter 3.
2.	In Unity, go to File -> Build Settings. (this a is essentially chapter 6 from the same page but if you don’t’ do this first chapter 3 makes no sense)
3.	Add Open Scenes to put your new scene into the build.
4.	Hit Universal Windows Platform and “Switch Platform”
5.	Make sure Build Type is D3D and that “Unity C# Projects” is checked.
6.	Make sure you complete chapter 3 from Holograms 100, everything past that is pseudo-optional based on how you want to debug and deploy, etc.

Importing from Maya:
1.	Assuming you have Maya installed on your development PC, this is actually SUPER easy.
2.	Drop your .mb files into the Unity Assets folder.
3.	Done. 😊

You can basically make whatever you want in Unity at this point. For me that was pretty much importing my assets from Maya, arranging them, then doing most of the steps in this: https://docs.microsoft.com/en-us/windows/mixed-reality/holograms-101

To debug / run / see in HoloLens:
If you want to use the Holographic Remoting Player to see the scene:
1.	Open the app on the HoloLens
2.	It should show you an IP address, note this down
3.	In Unity, Windows -> Holographic Emulation, change None to Remote to Device and put the IP into the Remote Machine box. Hit connect when ready.
4.	Once the connection status is green and reads Connected, if you hit the play button in the Unity Editor, the scene will be visible in the headset.
5.	Note: Disconnect the HoloLens when you want to resume working in Unity. This may seem obvious, but it’s very easy to want to stop playing the scene, make a quick edit, and then reply without disconnection and reconnecting the HoloLens. Don’t do this, because despite testing this on a high end gaming desktop, this frequently froze Unity and the entire computer.
2ND Note: when you hit play in Unity, you’re going to be popped into the camera exactly where it is in the HoloLens. This means if you dev this like I did, your scene will probably be where the computer screen is in front of you. You can either the scene to make this work, or turn around or to the side before hitting the button. Just a heads up.

If you want to deploy to the HoloLens via Visual Studio:
From (https://docs.microsoft.com/en-us/windows/mixed-reality/holograms-101 with edits with generalizations)
1.	Unity select File > Build Settings.
2.	Click Build.
3.	When Unity is done, a File Explorer window will appear.
4.	Open *YourProject*.sln.
5.	Using the top toolbar in Visual Studio, change the target from Debug to Release and from ARM to X86.
6.	Click on the arrow next to the Device button and select Remote Machine to deploy over Wi-Fi.
7.	Set the Address to the name or IP address of your HoloLens. If you do not know your device IP address, look in Settings > Network & Internet > Advanced Options (do not ask Cortana "Hey Cortana, What's my IP address?" like the instructions say, she’ll google it and it’ll be wrong)
8.	Leave the Authentication Mode set to Universal.
9.	Click Select
10.	Click Debug > Start Without debugging or press Ctrl + F5. If this is the first time deploying to your device, you will need to pair it with Visual Studio (HoloLens: Settings -> Update -> For developers -> Pair and enter the PIN into Visual Studio)
11.	The project will now build, deploy to your HoloLens, and then run.
12.	Put on your HoloLens and you’ll see the Unity logo and then your application.

Current bugs / issues:
•	Despite the code for cursor movement, and gesture recognition being in my project, I’ve been unable to get either to work in either the Holographic Remoting Player or with deployment.
•	Cursor itself is missing a mesh (which explains the lack of a visual of ^ but not the lack of interaction)…this is because the mesh is in the HoloLens library you should import is following 101, however, when I import the behavior is the same in the Remoting Player and I am unable to build due to errors in Unity that originate from that libraries files. Remove library, remove bugs. 

And one more note, recording from the HoloLens:
1.	In HoloLens, say “Hey Cortana…Take A Video”
2.	Do a Bloom gesture when done.
3.	Turn on Device Portal in Settings -> Update -> for Developers.
4.	Then connect using the IP in the Microsoft HoloLens app for desktop
5.	Go to Photos and Video, find your video and download it.
