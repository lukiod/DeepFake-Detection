# Deep fake detection Django Application
## Requirements:

**Note :** Nvidia GPU is mandatory to run the application.
- CUDA version >= 10.0 for GPU
- GPU Compute Capability > 3.0 


You can find the list of requirements in [requirements.txt](https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/blob/master/Django%20Application/requirements.txt). Main requirements are listed below:

```
Python >= v3.6
Django >= v3.0
```

## Directory Structure

- ml_app -> Directory containing code in views.py file
- project_settings -> Contains Django settings and files to run in production
- static -> Contains all css, js and json files (for face-api)
- templates -> Template files for HTML

<b>Note:</b> Before running the project make sure you have created directories namely <strong>models, uploaded_images, uploaded_videos</strong> in the project root and that you have proper permissions to access them.
# Running application on Docker
#### Step 1: Install docker desktop and start the Docker daemon

#### Step 2: Run the deepfake detection docker docker image
```
docker run --rm --gpus all -v static_volume:/home/app/staticfiles/ -v media_volume:/app/uploaded_videos/ --name=deepfakeapplication abhijitjadhav1998/deefake-detection-20framemodel
```
#### Step 3: Run the Ngnix reverse proxy server docker image
```
docker run -p 80:80 --volumes-from deepfakeapplication -v static_volume:/home/app/staticfiles/ -v media_volume:/app/uploaded_videos/ abhijitjadhav1998/deepfake-nginx-proxyserver
```
#### Step 4: All set now launch up your application at [http://localhost:80](http://localhost:80)

### Step 5: Star⭐ this repo 😉 on <a href="https://github.com/lukiod/SIH_2024" >  <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /> </a> and   Star⭐ this image on  </a>


Please note that currently we have only pushed the image of 20 Frames model, If you can to create your own image of other frames model follow the steps given in the [blog](https://abhijithjadhav.medium.com/dockerise-deepfake-detection-django-application-using-nvidia-cuda-40cdda3b6d38).

# Running application locally on your machine
We Recommend Using Wsl or Linux As their might be some issue with some libs

## For Linux 

### Prerequisite
1. Copy your trained model to the models folder.
   - You can download our trained models from the [Google Drive](https://drive.google.com/drive/folders/1UX8jXUXyEjhLLZ38tcgOwGsZ6XFSLDJ-?usp=sharing) or you can train your models using the steps mentioned in Model Creation directory.

#### Step 1 : Clone the repo and Navigate to Django Application

`git clone https://github.com/lukiod/SIH-2024.git`

#### Step 2: Create virtualenv (optional)

`python -m venv venv`

#### Step 3: Activate virtualenv (optional)

`venv\Scripts\activate`


#### Step 4: Install requirements

`pip install -r requirements.txt`

#### Step 5: Copy Models

`Copy your trained model to the models folder i.e Django Application/models/`

## For Windows
### Prerequisite
#### Step 1: Clone the repo and Navigate to Django Application

`git clone https://github.com/lukiod/SIH-2024.git`
#### Step 2: Install WSl into  your System
`wsl --install` in your cmd 
#### Step 3: Update and Upgrade your linux subsystem 
`sudo apt update`
`sudo apt upgrade`
#### Step 4 Install python into your wsl 
Typing `wsl` in front of a cmd prompt make your command run in wsl 
Example if you are in VS Code type `wsl sudo apt install python3-pip`
#### Step 5: Install requirements
`wsl sudo apt install cmake`
`wsl sudo apt install dlib`
`wsl sudo apt install -y libgl1-mesa-glx libglib2.0-0`
`wsl sudo apt install -y libsm6 libxext6 libxrender-dev`
`wsl sudo apt install -y libgl1-mesa-glx libglib2.0-0 libsm6 libxrender1 libxext6`
`wsl pip install -r requirements.txt`
- You can download our trained models from [Google Drive](https://drive.google.com/drive/folders/1UX8jXUXyEjhLLZ38tcgOwGsZ6XFSLDJ-?usp=sharing)

**Note :** The model name must be in specified format only i.e *model_84_acc_10_frames_final_data.pt*. Make sure that no of frames must be mentioned after certain 3 underscores `_` , in the above example the model is for 10 frames.


### Step 6: Run project

`python manage.py runserver`

## Demo 
### You can watch the [youtube video](https://www.youtube.com/watch?v=_q16aJTXVRE&t=823s) for demo
<p align="center">
  <img src="https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/blob/master/github_assets/fakegif.gif" />
</p>  
