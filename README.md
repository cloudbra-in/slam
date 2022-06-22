# slam.cloud-bra.in

`slam.cloud-bra.in` provides the functionality to create 2D map for navigation from the 2D laser scan data without installing specific SLAM method in your PC. (But you need ROS1 and ROS1 supported robot.)

Currently it provides bellow methods.

* cartographer
* slam_toolbox
* gmapping

You'll get a zip file which contains `pgm` file and `yaml` file for navigation.

If you have some interest, we are very happy if you give us some feedbacks in [cloud-brain discord](https://discord.gg/rUTNbwqvnA).

## Prepare

Record your robot's data using `rosbag record`

### Required Topics

* /scan: sensor_msgs/LaserScan
* /tf: tf2_msgs/TFMessage
* /tf_static: tf2_msgs/TFMessage

### Check your bag file

Use `rosbag info` to check your bag contains required topics.
You can rename your `/scan` topic in the next step.
In the bellow example, you have `/scan/front_filtered` and `/scan/rear_filtered`.

```bash
$ rosbag info 2022-05-12-08-30-17.bag
path:         2022-05-12-08-30-17.bag
version:      2.0
duration:     1:41s (101s)
start:        May 12 2022 08:30:17.20 (1652311817.20)
end:          May 12 2022 08:31:58.77 (1652311918.77)
size:         4.5 MB
messages:     6341
compression:  lz4 [18/18 chunks; 34.18%]
uncompressed: 12.9 MB @ 130.0 KB/s
compressed:    4.4 MB @  44.4 KB/s (34.18%)
types:        sensor_msgs/LaserScan [90c7ef2dc6895d81024acba2ac42f369]
              tf2_msgs/TFMessage    [94810edda583a504dfda3829e70d7eec]
topics:       /scan/front_filtered   1068 msgs    : sensor_msgs/LaserScan
              /scan/rear_filtered    1067 msgs    : sensor_msgs/LaserScan
              /tf                    4201 msgs    : tf2_msgs/TFMessage
              /tf_static                5 msgs    : tf2_msgs/TFMessage
```

### Compress your bag file (optional)

Compress your bag file to reduce the size of the data to be uploaded.

```bash
rosbag compress 2022-05-12-08-30-17.bag
```

## Use slam.cloud-bra.in

1. Access [slam.cloud-bra.in](https://slam.cloud-bra.in)
1. Select your bag file
1. Change the scan_topic name and frame_id if you need
    1. In the above example, rename `/scan` to `/scan/front_filtered`
    1. Check if it's OK to use `/base_link` as robot frame_id
1. Upload!
1. Wait until the map is completed
1. Check and download the results

## Sample bags

You can download a sample bag file [here](https://github.com/cloudbra-in/slam-doc/raw/main/sample_bags/2022-05-12-08-30-17.bag).
