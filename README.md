## W251
### Week 11 Homework
#### Travis Metz
#### July 2020

### Results
With dense layers of 64 and 32, batch size of 256 and unchanged epsilon of .995 and unchanged learning rate of .001:
- positive reward ~200 episodes
- >200 reward ~380
- 100 test average 248.76


### Other notes
In order to speed up, modified such that only showed graphical representation on every 100th episode during training, and printed results every 10th episode.
Used jtop to monitor resource usage - not entirely clear if GPU being used for model (as opposed to the graphical representation).


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

