# Sariska-Media-Unity-Package
Sariska Media Package for Unity (Android and iOS)

The repo contains the unity package which can be downloaded and added to you unity project to get started.

# About Sariska Media Unity SDK

The Sariska Video SDK for Unity lets you quickly add real-time communication to your Unity script. The SDK includes the following features to create seamless unity applications for Android and iOS.

**Platforms**: Android and iOS

**Real-time communication**: Bring audio and video communication to your users at ultra-low latency.

**Open Source**: Based on the extremely popular Jitsi Architecture, bring the power and constant innovation of open source into your project.

The SDK is written in the Adapter pattern, which makes it extremely lightweight, with reusable code written in languages native to the platform, it lets developers have enormous flexibility on what features to cherry-pick.

For documentation, read through the link at: https://docs.sariska.io/media/development/c-unity-engine

# Get Started:

To import this package in your unity package.

1. Clone the repo to your local system.
2. Open the project in the Editor where you want to import the asset package.
3. Choose Assets > Import Package > Custom Package. A file browser appears, prompting you to locate the Sariska-Media-Unity-SDK.unitypackage file.
4. In the file browser, select the file you want to import and click Open. The Import Unity Package window displays all the items in the package already selected, ready to install.
5. Deselect any items you don’t want to import and click Import. Unity puts the contents of the imported asset package into the Assets folder, so that you can access them from your Project window.


# Implementation for Android and iOS

## Importing SariskaMediaUnitySdk

``` C#
using Plugins.SariskaMediaUnitySdk;
```

## Initialize SDK

After the SDK is added to your project, first initialize the SDK before proceeding with the setting up for the video call.
``` C#
SariskaMediaUnitySdk.InitSariskaMediaTransport();
```

## Setup Local Stream

The SetupLocalStream method in SariskaMediaUnitySdk gives you the option to set up a stream with a set of parameters, which lets you choose between an audio or a video call, and the resolution of the video in case of a video call. Additionally, the method requires the user to send texture pointers for both textures defined by the user.
``` C#

// void SetupLocalStream(audio, video, resolution, localTexturePointer, remoteTexturePointer)

SariskaMediaUnitySdk.SetupLocalStream(true, true, 180, localTexturePointer, remoteTexturePointer);

```

## Create Connection

In order to enter the room and start a call, the create connection method lets you give a room name and user name as parameters. Once these parameters are sent to the SDK, it automatically creates a JWT token for the user and establishes a conference for people to join it. 

``` C#
SariskaMediaUnitySdk.CreateConnection(roomName, userName);
```

## Mute/Unmute Call

A local participant can mute or unMute their audio by using the following methods.

```C#
// To mute audio
SariskaMediaUnitySdk.MuteAudio();

// To unmute audio
SariskaMediaUnitySdk.UnMuteAudio();
```

## Mute/Unmute Video

A local participant can mute or unMute their video by using the following methods.
``` C#
// To mute video
SariskaMediaUnitySdk.MuteVideo();

// To unmute video
SariskaMediaUnitySdk.UnMuteVideo();
```

## Switch Camera

A participant can switch the camera between the front and back by calling the switch camera method. By default, the video call initializes with the front camera open. 
```C#
// To switch between camera
SariskaMediaUnitySdk.SwitchCamera();
```

## Lock/Unlock Room

A moderator can lock and unlock a room by calling the below two methods. While locking the room, the moderator has to provide a password in the form of a string. 
```C#
// Lock a room with a password 
SariskaMediaUnitySdk.LockRoom(password);

// Unlock a room 
SariskaMediaUnitySdk.UnlockRoom();
```

## Change Audio Output

The audio output can be changed to the speaker and turned off by calling the OnSpeaker method for switching to speaker and OffSpeaker for switching to the default output.
```C#
// Speaker on
SariskaMediaUnitySdk.OnSpeaker();

// Speaker off
SariskaMediaUnitySdk.OffSpeaker();
```

## Get Participant Count

The GetParticipantCount method returns the number of participants present in the meeting at the time the method is called.
```C#
// Get Participant count 
// hidden, if assigned true, counts hidden participants as well 

bool hidden = true;
int participantCount = SariskaMediaUnitySdk.GetParticipantCount(hidden);
```
## Get Dominant Speaker

The GetDominantSpeaker method returns the id in form of a string of the dominant speaker of the meeting.
```C#
// Returns the id of the dominant speaker

string participantId = SariskaMediaUnitySdk.GetDominantSpeaker();
```
