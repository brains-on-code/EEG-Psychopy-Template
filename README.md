# EEG-Psychopy-Template

----

### What You need

* Any EEG, in the case of the tu chemnitz software engineering professorship the CGX quick 20

* A Setup Software for configuring the EEG and to check the electrodes, in the case of the tu chemnitz software engineering professorship the CGX acquisition software

* A program that can connect to Python libraries to establish the connection to the EEG.

* A program to provide stimuli

----

## CGX-quick 20 with Psychopy

* Set up a Psychopy program that establishes the EEG connection and interrupts it at the end to save the data. Events should also be set to allow synchronization of the stimuli with the EEG data. See the example code for this. 


#### Code for initializing
```python
eeg_rec = None

if use_eeg==True:
    from EEGTools.Recorders.LiveAmpRecorder.liveamp_recorder import LiveAmpRecorder as Recorder
    eeg_rec = Recorder()
    eeg_rec.connect()
```

#### Code for starting the data collection
```python
if use_eeg==True:
    eeg_rec.start_recording()
```

#### Code for starting the data collection
```python
if use_eeg==True:
    eeg_rec.start_recording()
```

#### Code for closing the recording and saving the data
```python
if use_eeg==True:
    eeg_rec.refresh()
    eeg_rec.disconnect()
    # name of the data to Save
    eeg_rec.save("EEG_Collected_data_raw")
```

#### Code for setting events
```python
# for setting the start of the stimulus
if use_eeg==True: 
    eeg_rec.refresh()
    # set the event id based on the stimulus your showing
    # hash a string or event code you like
    eeg_rec.set_event(hash("StartOfStimulus")%1000000007)

# for setting the start of the stimulus
if use_eeg==True: 
    eeg_rec.refresh()
    # set the event id based on the stimulus your showing
    # hash a string or event code you like
    eeg_rec.set_event(hash("EndOfStimulus")%1000000007)
```

* Install the EEG Library on your target machine.

* Use of the EEG:

  * Plugin the Connection USB Stick

  * Insert the bateries into the EEG

  * Connect the electrodes to the ears, using both cables on the left side of the EEG and only one cable on the right side.

  * Adjust the electrodes to the participant's hairstyle and head shape.

  * Turn on the EEG

  * CGX acquisition software and connect to the EEG (This is under 'Device' and there under 'Discovered Divices'. The eeg must then be selected and connect clicked.)
  
  * Set up the electrodes/ EEG so that there is a good connection (The status of the electrodes can be seen under 'Channels' Red means no connection, light green is semi good, dark green is perfect. EXT channel is always red.)

  * Start the RDA Server and the Lab Streaming Layer via the CGX acquisition software (Under 'Device' at the very bottom)
  
  * Start the Psychopy experiment and collect your data
  
  
  

