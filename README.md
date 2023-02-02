# detect-fire-in-raspberrypi
This program detects fire in a Raspberry Pi using Node.js and OpenCV. To get started, you must ensure that OpenCV is built. Check the instructions in this repo https://github.com/UrielCh/opencv4nodejs#readme If you need any help, you can reach out at Discord (@OMAR#1234) or open an issue in the repository.
this code was test in pi4 with node v18.13.0 cpu usage (4-25) av 12
# instructions  
after building it and running it won't work you must change the pi-camera lib 
go to "/node_modules/pi-camera/index.js"
change the snap() function to
```
 snap() {
    if (this.mode !== 'photo') {
      throw new Error(`snap() can only be called when Pi-Camera is in 'photo' mode`);
    }
    
    return Execute.run(Execute.cmd('raspistill --timeout 2 -o /home/lukes/fire4/a.jpg', this.configToArray()));
  }

```
where /home/lukes/fire4/a.jpg is where you want to save the photo and --timeout 2 is max time it needs 
after that go to index.mjx file (the code file) and change
```
const file = resolve('/home/lukes/fire4/a.jpg'); 
```
to the place you are saving your pic
NOTE:you must keep thee same name (a.jpg)
and it should work
# TODO
- detect the size of the fire
- detect if there are people in it
- obtain the location using GPS.
