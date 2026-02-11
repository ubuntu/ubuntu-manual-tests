**Audio Check** Before you begin, make sure you are booted into a fresh session, and that you haven't opened any audio applications - including any browser pages with audio content. 

Open Ubuntu Studio Controls from the menu
    Start Jack and confirm it runs properly (DSP shows a percentage). Then stop jack to confirm it closes properly (DSP shows 0%). Finish by starting Jack and keeping it on for the duration of this test.
    Start Carla and keep it around for your Patchbay. Open Hydrogen from the menu
    Create a quick beat and play it - you should hear sound. If you aren't hearing any sound, make sure that connections are accurate in **Carla -> Patchbay** , and that your hardware levels are not muted.
    See http://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro for more info on audio on Ubuntu Studio if you're having trouble. 
    You can close Hydrogen once you are done
Make sure pulseaudio is connected to jack
    In **Carla -> Patchbay** make sure that PulseIn and PulseOut exist and are connected to system input/output.
Test desktop sound through jack
    Open firefox and go to any page that has audio. Flash video will not work, so html5 is preferred - such as http://youtube.com/html5. 
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
