# 1. Live Audio Effect Reference

## 1.1 Auto Shift

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/01_-_auto_shift_new.jpg)

Auto Shift is a real-time pitch tracking and correction effect made for **monophonic audio** (with a inclination towards vocal recordings and samples). It can receive pitch information in two main ways:

- **Scales** - you define in the device (Quantizer)
- **MIDI notes** - coming from another track (MIDI sidechain), which could be helpgul for harmonies and pitch control.

### 1.1.1 Usage 

Auto Shift is categorized in the new version of Live as an **Audio Effect**. It can work best when added to an audio track that contains a clear pitched signal (voice, monophonic synth lead, bass, etc.).

Drag **Auto Shift** onto an audio track. In the **Input** section, you can choose a **Pitch Range** (High / Mid / Bass) that matches the source. Next, you can use one of the correction modes:
- **Quantizer**: pick a Root + Scale (or select included notes), then adjust **Correction Strength**.
- **MIDI**: enable **MIDI In**, choose a MIDI track as the source, and play notes to control the correction.
Lastly, set **Dry/Wet** to balance natural vs corrected sound.

### 1.1.2 Input - Pitch Tracking and Latency

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftInputSectionL12.png)

The Input section is where you optimize tracking before you touch “tuning” parameters. The Input Pitch shows you the detected notes in letter notation and cents. 

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftInputLEDL12.png)

The Pitch Range (High, Mid or Bass) selects the expected input range, making the detection more reliable - you can use High for signals in a high frequency range, Mid for signals in a mid frequency range and, finally, Bass for signal in a lower frequency range. 

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftLiveModeL12.png)

The Input Gain, with the range bwetween -24 to +24 dB trims the signal incoming into the detector for more accurate detection. At the bottom, Latency is displaying in milliseconds the time difference between input and output of the audio device. For live performance scenarios, the Live Mode, which can be toggled in the title bar, reduces latency for performance. This setting can introduce gltiches depending on the speed of the pitch change.

### 1.1.3 Quantizer Mode - Scale-Based Correction

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftQuantizerL12.png)

The Quantizer setting aims to correct incoming audio to the notes of a defined scale.

This section contains multiple control which change different aspects of the quantization process. With Correction Strenght you can adjust how strongly the audio is corrected to reach the target note. To combat the corrections made, Smooth, which has a range of 0ms t0 200ms, changes the interpolation time for less artifacts.

In the audio device, there is a built in setting which changes the target musical scale. With Root & Scale you tell the device which target it should reach. You can use the parameters Use Current Scale which will prompt Auto Shift to follow the active clip scale selected in the session (“scale awareness”). Aftewards, the scale’s notes will be highlighted.

If you want to build a custom scale, you can use Included Notes. You to enable and disable note and make your personalized scale. 

For further pitch adjustment, Pitch Shift transposes the sound after correction, while maintaining the target key.

### 1.1.4 MIDI Mode (Pitch Correction from Notes)

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftMIDIInputL12.png)

When you enable MIDI In, Auto Shift switches to using incoming MIDI data to determine the target pitch instead of using the scale established in the Quantizer.

You can select in this menu the **External Source** if you want to select and alternate source MIDI. The MIDI Mode includes the setting **Tapping Point**, where you can select if you want to introduce the MIDI signal either Pre FX, Post FX or Post Mixer. You can select Post FX or Post Mixer to include, for example, any audio effects which you might have on your desired MIDI input track.

Choose between two voice modes Mono and Poly to have access to one or up to 8 voices. The Mono mode provides a Glides setting which can be selected for sliding between note values. Polt Mode provides either 2, 4 or 8 voices for harmonization. 

Enabling MIDI Input causes Auto Shift to only output audio when it is receiving MIDI notes.

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftMIDITabL12.png)

The keyboard at the top shows which MIDI note is currently being received. The keys light up in real time while notes are being updated. 

The MIDI Mode features an Envelope section which includes Attack and Release parameteres which are visualized in the box to their right. Turning on Note Latch will make the last held MIDI note stay active even after the key has been released. 

The Pitch Bend paramenter, abreviated PB, select by how much the pitch will is altered when using the Pitch Bend Wheel on your controller of choice. 

At the bottom of the menu, you can select up to four sources of modulation as input from the MIDI track of choice. Auto Shift is reaching to the external track and pulling the MIDI data to drive the mod writing. 

### 1.1.5 LFO Tab (Modulation)

![Alt text](../images/Manual/01_Audio_Effects/01.01_Auto_Shift/AutoShiftLFOTabL12.png)

Auto Shift includes an LFO that can modulate the following values: Pitch, Formant, Volume, and Pan.

Opt for the Reset parameters if the you want to retrigger the LFO at onsets. The onset can be either pitch detection in Quantizer mode, or notes in MIDI mode. The Delay and Attack parameters shape how the LFO fades in and fades out.

Custom waveforms are accessible in by selecting Waveform and selecting one of the multiple waveforms, which include stepped, sample and hold and random variants.Optional, the Rate can run free or sync to tempo

The LFO affects the incoming signal even pitch correction is not on.

### 1.1.6 Pitch and Formant Shifting

You can use pitch and formant controls for “tuned” effects or as a creative pitch/formant shifter.

You can transpose the signal with Pitch Shift in semitones & cents. This parameter has the option fine in order to tune it in cents. Formant Shift with value between -100% and 100% changes tonal and timbral character without changing perceived pitch.

Developed to achieve a natural sound, Formant Follow links formant movement to pitch movement for more natural results.

### 1.1.7 Vibrato

Vibrato is and option useful subtle motion in the signal or harder pitch effects. 

It has an Amount option which can alter the signal by a maximum of 200 cents. You can adjust the Rate of the vibrato by a minimum of 2Hz or a maximum of 15Hz. Choosing a Fade In time selects how quickly the vibrato reaches its target value. Natural Vibrato offer the same effect but with small variations for a more organic feel. 

The Dry/Wet control also lives here. At 50%, you can create a simple doubler-style blend between dry and processed signals.

## 1.2 Chorus Ensemble

Chorus-Ensemble is time modulation device developed inside Live 12 and earlier versions. It serves as a chorus effect with multiple modes(**Chorus**, **Ensemble**,**Vibrato**) each tailoring to different use. With the latest update, the **Clasic** mode has been renamed to **Chorus** to better reflect it resulting effect. The updated **Chorus** mode features two new parameters with which you can interact:

- **Time** - you can now select the time between the delay lines as opposed to having them scaled dynamically per tap. This setting also included the previous behaviour by selecting **Auto**.
- **Tap** - is a parameter which allows you to switch between a one or two tap delay.