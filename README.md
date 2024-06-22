### Jetson Xavier NX (running jetpack 5.1.3)
-----------------------
sudo apt update -y; sudo apt install tensorrt python3-pip -y; sudo apt-get install cuda-toolkit-*

sudo ldconfig

cd /tmp

git clone https://github.com/NVIDIA-AI-IOT/jetson_benchmarks.git; cd jetson_benchmarks

sudo sh install_requirements.sh

mkdir models

python3 utils/download_models.py --all --csv_file_path ./benchmark_csv/nx-benchmarks.csv --save_dir /tmp/jetson_benchmarks/models 

----Make sure to have Mode 20W 6-cores------

sudo python3 benchmark.py --all --csv_file_path ./benchmark_csv/nx-benchmarks.csv --model_dir /tmp/jetson_benchmarks/models --jetson_clocks

                Model Name         FPS
0             inception_v4  331.010492
1                 vgg19_N2  142.000824
2  super_resolution_bsd500  194.998501
3        unet-segmentation  171.750874
4          pose_estimation  331.584907
5          yolov3-tiny-416  750.907848
6         ResNet50_224x224  909.530273
