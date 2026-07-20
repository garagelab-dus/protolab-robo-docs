---
title: "Minimum Camera Resolution for Teleoperation"
date: 2026-07-20
meta-data: camera-resolution, teleoperation, lerobot
---

Test-Szenario:

```shell
cd /Users/lerobot/repos/ernie-und-bert/scripts
# or
cd $repo_ernie/scripts
# camera settings are hard-coded in `init.cameras.sh` for this test, so we need to checkout the branch that contains the changes.
git checkout test/minimum-cam-resolution

# run the teleoperation script
./run_a_teleoperation.sh
```

Auflösung der Kameras: 320x240 Pixel, 30 FPS

Screenshot:

![screenshot rerun app](https://garagelab-dus.github.io/protolab-robo-docs/blog/images/minimum-cam-resolution-1.png)

???- info "Teleop loop time: 33.34ms (30 Hz)"

    ```txt
    (lerobot) lerobot@MacBook scripts % ./run_a_teleoperation.sh 
    robot_cameras2: { front: { type: opencv, index_or_path: 0, width: 320, height: 240, fps: 30 }, wrist: { type: opencv, index_or_path: 1, width: 320, height: 240, fps: 30 }}
    Press ENTER to continue or any other key to abort.
    objc[6105]: Class AVFFrameReceiver is implemented in both /Users/lerobot/.conda/envs/robot/lib/python3.12/site-packages/cv2/.dylibs/libavdevice.61.3.100.dylib (0x1039b03a8) and /Users/lerobot/.conda/envs/robot/lib/python3.12/site-packages/av/.dylibs/libavdevice.61.3.100.dylib (0x11bed43a8). This may cause spurious casting failures and mysterious crashes. One of the duplicates must be removed or renamed.
    objc[6105]: Class AVFAudioReceiver is implemented in both /Users/lerobot/.conda/envs/robot/lib/python3.12/site-packages/cv2/.dylibs/libavdevice.61.3.100.dylib (0x1039b03f8) and /Users/lerobot/.conda/envs/robot/lib/python3.12/site-packages/av/.dylibs/libavdevice.61.3.100.dylib (0x11bed43f8). This may cause spurious casting failures and mysterious crashes. One of the duplicates must be removed or renamed.
    INFO 2026-07-20 21:21:07 eoperate.py:211 {'display_compressed_images': False,
     'display_data': True,
     'display_ip': None,
     'display_port': None,
     'fps': 30,
     'robot': {'calibration_dir': None,
               'cameras': {'front': {'backend': <Cv2Backends.ANY: 0>,
                                     'color_mode': <ColorMode.RGB: 'rgb'>,
                                     'fourcc': None,
                                     'fps': 30,
                                     'height': 240,
                                     'index_or_path': 0,
                                     'rotation': <Cv2Rotation.NO_ROTATION: 0>,
                                     'warmup_s': 1,
                                     'width': 320},
                           'wrist': {'backend': <Cv2Backends.ANY: 0>,
                                     'color_mode': <ColorMode.RGB: 'rgb'>,
                                     'fourcc': None,
                                     'fps': 30,
                                     'height': 240,
                                     'index_or_path': 1,
                                     'rotation': <Cv2Rotation.NO_ROTATION: 0>,
                                     'warmup_s': 1,
                                     'width': 320}},
               'disable_torque_on_disconnect': True,
               'id': 'ernie',
               'max_relative_target': None,
               'port': '/dev/tty.usbmodem5A680100061',
               'use_degrees': True},
     'teleop': {'calibration_dir': None,
                'id': 'bert',
                'port': '/dev/tty.usbmodem5A680100531',
                'use_degrees': True},
     'teleop_time_s': None}
    INFO 2026-07-20 21:21:08 so_leader.py:78 bert SOLeader connected.
    INFO 2026-07-20 21:21:11 a_opencv.py:179 OpenCVCamera(0) connected.
    INFO 2026-07-20 21:21:13 a_opencv.py:179 OpenCVCamera(1) connected.
    INFO 2026-07-20 21:21:14 follower.py:105 ernie SOFollower connected.
    Teleop loop time: 33.34ms (30 Hz)
    ```

Die Auflösung von 320x240 Pixeln bei 30 FPS ist ausreichend für die Teleoperation. Die Bildqualität ist gut genug, um die Bewegungen des Roboters präzise zu steuern, ohne dass es zu Verzögerungen oder Ruckeln kommt.

---

Für das Training von KI-Modellen kann eine andere Auflösung vielleicht notwendig sein. Aber der Rechenaufwand für das ACT Model ist bei 320x240 um ein Vielfaches kleiner.

