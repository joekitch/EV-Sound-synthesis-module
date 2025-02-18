# EV-Sound-synthesis-module
A system to give EV conversions some characteristic sound, designed for the CORVOLT project, but may eventually be abstracted

---

## Disclaimer

This is a very experimental system, and while not inherently dangerous, i don't claim any responsibility of any silly things someone might end up doing

---

## Backround

Evs tend to be labeled as boring, partially becasue they're so silent. 
This system is an attempt to remedy that by building a complex soundscape which matches the character of the car, a mix of entirely snyhetic sound and amplifying existing sounds

---

## Working principle

The general idea is to have a central audio processing node somewhere which listens on the main canbus for key values like throttle position, rpms, current speed, and meta values like "torque requested".

The audio processor needs to be based around a Shepard's Tone, which continuously rises or falls due to an auditory illusion

[![Example of shepards tone](https://img.youtube.com/vi/_bpUSNZQAb4/0.jpg)](https://www.youtube.com/watch?v=_bpUSNZQAb4?t=28)

---

## Building the sound

The core sound is an amalgum of several components layered together
- a recording of the original engine's idle, modified with multiple low pass filters and other effects, to produce a clean hum
[![Sample sound made some time ago](https://img.youtube.com/vi/M_10pjS2_b0/0.jpg)](https://www.youtube.com/watch?v=M_10pjS2_b0)
- the synthetic octobass sound used by hans zimmer in the dune soundtracks
[![Clip from a live hans zimmer concert](https://img.youtube.com/vi/DgL_Zmljjso/0.jpg)](https://www.youtube.com/watch?v=DgL_Zmljjso?t=139)
- For startup, the slowed version of a sound font used for custom home made lightsabers
[![Clip from a live hans zimmer concert](https://img.youtube.com/vi/n8FQuJVUgbM/0.jpg)](https://www.youtube.com/watch?v=n8FQuJVUgbM)
- at higher RPMs, the tesla large drive unit makes a very pleasing high pitched sound similar to a supercharger. With a faraday cage around the motor, and a long wire looped around the motor and hooked up to an AM amplifier, the sound can be smoothed and amplified
[![Sound sample from a tesla model S tuned to an am radio station](https://img.youtube.com/vi/j4AxsGk-LdQ/0.jpg)](https://www.youtube.com/watch?v=j4AxsGk-LdQ)
- Several other possible sound items including
- old electric generator startup whines https://youtu.be/fNuI6keQXYA?list=PLl0_UMyNNQrKSdmRJHtk31pC2WC_6_uIY ,
- laser cleaning system sounds https://youtu.be/iYGduuxXHl4?list=PLl0_UMyNNQrKSdmRJHtk31pC2WC_6_uIY ,
- angry synth noises, similar to what was used in doom 2016 https://youtu.be/04uzirXiL9U?list=PLl0_UMyNNQrKSdmRJHtk31pC2WC_6_uIY&t=168
- possibly more, as i find them


---

## Amplifying the tesla motor 

The tesla large drive unit generates a lot of EMF on the am radio band, which is very easily picked up by the am radios on older tesla model S' (the am radio was removed from newer teslas exactly because of this). It's considered a nuisance by modern ev manufacturers, so much so that it's hard to find AM in evs these days.

With a good faraday cage around the motor to prevent external AM signal from leaking in, and a coil wrapped around the motor housing, going into an AM amplifier, that could be used as a very "pure" sound of the motor rotating 

From there, it's just another input line for puredata to use as needed 

The goal would be to feed that sound in at higher throttle precentages, so the car makes a very intense sound when it's pushed hard

---

## Hardware

- an EV VCU capable of outputting the needed parameters in an accessible (non encrypted) way
- raspberry pi to continuously run Puredata
- Canbus shield or hat for the pi, letting it tap into the main vehicle canbus
- Speakers designed for this kind of sound, Possibilities include the Thor electronic exhaust system, Enginevox, and Hansshow, as well as several no-name options on places like aliexpress

---

## Software

- Puredata, running continuously on the Pi
- a canbus interpreter layer

---

## Diagram


