TARGET DECK
Home::Creating Sounds From Scratch::03 - Tools of the Trade

# Sound Generators
There are essentially two primary sound sources in all of music synthesis: the *oscillator* and *digital playback*

## Oscillator (VCO) <!--fc-->
The traditional analog method of generating sound electronically. It produces alternating electrical current, hence the name *voltage control oscillator*
<!--ID: 1718928191982-->



### Waveforms Generated by Oscillators <!--fc-->
- sine wave 
- square wave
- triangle wave
- sawtooth wave
- white/pink noise
![[Pasted image 20240607210942.png]]
<!--ID: 1718928192007-->


### Sine Wave <!--fc-->
The most basic waveform, consisting of only its fundamental pitch. Useful to fill the lower octave of a more complex sound
![[Pasted image 20240608145441.png]]
<!--ID: 1718928192023-->


## Triangle Wave <!--fc-->
Mostly a fundamental frequency with a slight presence of odd harmonics decreasing in intensity at an exponential rate. Given it's weak overtones it's not super useful in subtractive synthesis
![[Pasted image 20240608145452.png]]
<!--ID: 1718928192040-->


## Square Wave <!--fc-->
A square wave has equally sized positive and negative stages in each wave cycle because of its composition of only odd harmonics that decrease less abruptly than the triangle wave
![[Pasted image 20240608150345.png]]
<!--ID: 1718928192055-->


### Pulse Wave <!--fc-->
Can be described as an a-symmetrical square wave, one that has a transition point earlier than the halfway point - the positive stage is shorter than the negative stage. Useful for LFO modulation
<!--ID: 1718928192071-->


## Sawtooth Wave <!--fc-->
The most complex of the standard waveform, very good starting point for subtractive synthesis
The sawtooth contains *all* harmonics decreasing in intensity, thus they become a prominent characteristic in its timbre
![[Pasted image 20240608150820.png]]
<!--ID: 1718928192085-->


## Noise <!--fc-->
Useful for percussive sounds, accentuating the attack portion of a patch, or special effects
<!--ID: 1718928192100-->


# Digital Playback

