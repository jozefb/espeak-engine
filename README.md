# espeak-engine
The ESpeakEngine is Objective-C static library containing light wrapper for eSpeak open source speech synthesizer.
It does not add any new features to eSpeak, it only exposes its funcionality as Objective-C class methods and combines this functionality with iOS _AVFoundation Framework_

##Introduction
A few years ago I was looking for some Objective-C framework which would allow to speech text on iOS devices in our project. In that time i did not find any, but only tree plain speech synth libraries written i C - eSpeak, Flite and Festival. After couple days of research and attempts to integrate those libraries for iOS SDK I choosed eSpeak and Flite as candidates (I was able to successfully customize only eSpeak and Flite in reasonable time, they supports more languages, Google use eSpeek for its translation service…).

In next couple of lines is described eSpeak speech synthesizer wrapper - ESpeakEngine.

##Details
The ESpeakEngine is Objectice-C static library project containing very light wrapper for eSpeak open source speech synthesizer. It does not add any new features to eSpeak, it only exposes its funcionality as Objective-C class methods and combines this functionality with iOS AVFoundation Framework (to see all available properties of eSpeak synthesizer, please read documentation on its homepage url). It also uses standard delegate pattern by defining ESpeakEngineDelegate. In static library project also exists a test target which contains simple iPhone app. This sample app has only a one screen with the UITextView for text input and the UIButton to start speech syntesis of an entered text.

###Usage
Usage of the ESpeakEngine is very easy, You have to add:

* link the ESpeakEngine static library project (ESpeakEngine static library project has to be located at same directory as a main project)
* link the AVFundation.Framework
* add path to folder eSpeak_1.0/Classes in Target Build Settings: Header Search Paths
* link ESpeakEngine data folder espeak-data in main project (drag it in Project Navigator pane from linked eSpeak.xcodeproj project & drop it to any location in a main project)
Then import the ESpeakEngine header in class which is holding engine instance:
```objc
#import "ESpeakEngine.h"
```
In the init or the viewDidLoad method create a new instance of the ESpeakEngine and set all parameters you want (language, volume, gender… etc.):
```objc
- (void)viewDidLoad {
    [super viewDidLoad];
    engine = [[ESpeakEngine alloc] init];
    engine.volume = 1;
    [engine setLanguage:@"en"];
} 
```
And finally bind any button touch event to code which calls the ESpeakEngine a speak method:
```objc
- (IBAction)speech {
    NSString * text = self.textView.text;
    [engine speak:text];
}
```
No documentation is included in this up-to-date version. Anyhow, the source code is self-explanatory and has altogether only a few hundred lines, also test application is good start point to look for more properties.

Any questions will be answered, feel free to contact me.
