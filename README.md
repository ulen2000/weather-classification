# weather-classification
### Dataset
To achieve multi-weather classification, we have produced an open-source dataset. The dataset consists of about 60,000 images made up of five common weather classification types, e.g., sunny, rainy, snowy, foggy, and night, summarized in following tale. Specifically, we also inspected these images qualitatively and disregarded images that did not belong to any of these categories or have low quality.

<img width="689" alt="360截图1814122374108116" src="https://user-images.githubusercontent.com/58459187/113407386-c52d4300-93df-11eb-89d0-81190eb874d0.png">

*The dataset link is https://drive.google.com/file/d/13zJ65SBv5s40HS0kUbF1jT54TX7-awCB/view?usp=sharing*


### Application
we integrated the method through docker, making it easier to deploy in heterogeneous IoT devices and apply to scenarios of smart city, and now the deployment of the test code is ready

*you can download it from the link here: https://hub.docker.com/repository/docker/27718842/weather/general*

The operation is quite simple, just type:  
```console
systemctl start docker

docker images

docker run -it 'image_id' bin/bash
```
<img width="430" alt="360截图17571113043443" src="https://user-images.githubusercontent.com/58459187/113405869-1b4cb700-93dd-11eb-8756-f3d29caf6260.png">

After entering the docker container, type:
```console
cd /root/model

python3 customize_service.py -data_path 'your_image_path'

# e.g., customize_service.py -data_path ./images/Picture1

# Remember to put the pictures that need to be tested in the 'images' folder 
```




The docker container technology is to package an application and its required resources into a docker image. Docker can use the image to create a container so as to realize the rapid transplantation and deployment of the application.
<img width="1144" alt="docker1" src="https://user-images.githubusercontent.com/58459187/119315294-48646a00-bca8-11eb-88b3-55c7e300e9a9.png">

For further implementation in reality, we integrated the method through docker, making it easier to deploy in heterogeneous IoT devices and apply to scenarios of the smart city. Now the deployment of the test code is ready.

The model application is designed as follow:

<img width="893" alt="模型应用" src="https://user-images.githubusercontent.com/58459187/113404600-02430680-93db-11eb-85ae-16ace32ebb0e.png">


This paper designs an application interface as shown in the figure below. This interface includes two input items, one is the trained weather image classification model, and the other is the weather image to be discriminated. The weather image classification model is saved to the specified path, and the model is read and activated through the __init__() function. The environment image taken by the camera is saved to the specified file path, and the image is read using the read_image() function. Finally, use the interface() function to get the weather conditions of the current location.

*The final output is the weather label with the highest confidence and the confidence value of each type of weather.*

<img width="1536" alt="应用接口设计" src="https://user-images.githubusercontent.com/58459187/113404608-04a56080-93db-11eb-9cad-fbfedf3283c1.png">

## Operating environment
The operating environment in docker container is as follows:
* Linux version 4.4.0-63-generic (buildd@lcy01-31) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) 
* Python 3.6

The version of the main python library is as follows:
>numpy             1.19.4
>
>Pillow            8.0.1
>
>torch             1.7.1+cu110
>
>torchaudio        0.7.2
>
>torchvision       0.8.2+cu110
>
>typing-extensions 3.7.4.3
