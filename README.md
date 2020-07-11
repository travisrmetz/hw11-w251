## W251
### Week 11 Homework
#### Travis Metz
#### July 2020

### Results
With dense layers of 64 and 32, batch size of 256, unchanged epsilon decay of .995, and unchanged learning rate of .001:
- positive reward ~200 episodes (rolling 10)
- />200 reward ~380 (rolling 10)
- 100 test average 248.76


32, 16, 256
- positive reward ~ 240 (rolling 10)
- />200 reward ~460 (rolling 10)
- 100 test average 167.41

64, 32, 512
- positive reward ~250 (rolling 10)
- />200 reward ~420 (rolling 10)
- 100 test average 237.61

64, 32, 256, 0.99 decay
- positive reward ~170 (rolling 10)
- />200 reward ~240 (rolling 10)
- 100 test average 253.03
- 62.69 minutes to train

128, 64, 256, 0.99 decay
- positive reward ~110 (rolling 10)
- />200 reward ~210 (rolling 10)
- 100 test average - inadvertently stopped before finished
- 48 minutes to train (stopped at 320)

128, 64, 256, 0.995 decay
- positive reward ~ 280 (rolling 10)
- />200 reward ~ 420 (rolling 10)
- 100 test average - 252.90
- 97 minutes to train (stopped at 860)
- 60 minutes to test

256, 128, 256, 0.995 decay
- positive reward ~ 270 (rolling 10)
- />200 reward ~ 410 (rolling 10)
- 100 test average - 254.21
- 92 minutes to train (stopped at 1000)
- 61 minutes to test

512, 512, 256, 0.995 decay
- positive reward ~ 350 (rolling 10)
- />200 reward ~ 720 (rolling 10)
- 100 test average - 196.14
- 123 minutes to train (stopped at 1000)
- 71 minutes to test

256, 256, 256, 0.995 decay
- positive reward ~ 270 (rolling 10)
- />200 reward ~ 640 (rolling 10)
- 100 test average - 243.67
- 88 minutes to train (stopped at 740)
- 68 minutes to test

64, 64, 256, 0.995 decay
- positive reward ~  (rolling 10)
- />200 reward ~  (rolling 10)
- 100 test average - 
-  minutes to train (stopped at )
-  minutes to test



### Other notes
In order to speed up, modified such that only showed graphical representation on every 100th episode during training, and printed results every 10th episode.
Used jtop to monitor resource usage - not entirely clear if GPU being used for model (as opposed to the graphical representation).
Modified to measure last 10 scores to get better sense of recent progress.


### commands to build image
docker build -t hw11-image -f Dockerfile.agent .
(TRM changed so that does not automatically run lander)

### commands to run image etc
xhost +
sudo jetson_clocks --store
sudo jetson_clocks
time docker run --name hw11 -it --rm --net=host --runtime nvidia  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix:rw --privileged -v /home/trmetz/hw11-w251/:/tmp/ hw11-image

### monitor gpu and system usage
sudo jtop

