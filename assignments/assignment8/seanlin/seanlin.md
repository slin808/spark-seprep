I was able to get up to the last part and got everything to work except for streamlit 

![image](https://github.com/slin808/spark-seprep/assets/113227265/0dbd9752-cf8d-4c3e-be2f-3a26fdcee0f6)



Along the way, I encountered many issues while trying to get the small bin model and running the other commands especially as a  Windows user.

# Challenges faced along the way and how I overcame them#

podman build -t whisper:image . didn't work initially
I overcame this issue by running podman machine start to start the default machine before running this command in order to get it to work. 

![image](https://github.com/slin808/spark-seprep/assets/113227265/086bc7ac-9fb0-4e2e-b818-2c06a7b04e15)

wget --no-config --quiet --show-progress -O ggml-small.bin https://huggingface.co/ggerganov/whisper.cpp/resolve/main/ggml-small.bin didn't work on Windows
I overcame this issue by just manually going to the site and downloading the model and placing it in the correct folder
![image](https://github.com/slin808/spark-seprep/assets/113227265/d4f3e287-0d53-4ae7-aaa4-faf27fb1fe80)


ffmpeg -i <input.mp3> -ar 16000 -ac 1 -c:a pcm_s16le <output.wav>
I also had trouble running the ffmpeg on command prompt on Windows so I overcame this issue by moving my original m4a file and converting it to a wav file by downloading ffmpeg on WSL using pip install. Originally there was an issue with this but this was fixed when I did sudo apt update and then pip install ffmpeg. 
Running the command on wsl produced the corresponding output.wav file which I moved back into my orginal directory.
![image](https://github.com/slin808/spark-seprep/assets/113227265/1324140f-a5e0-45e0-9b48-4b7f4de32613)

Deploying model service error. Originally I ran the command given replacing it with my local path to the model but I got an invalid reference format. However, I realized the error came from the backslashes which are an issue on Windows command prompt but not on Unix systems.

# Improvements and suggestions to the process #
Perhaps, in future semesters, work can be completed on a virtual Unix system/server for everyone so commands wouldn't be variable and the issues encountered won't be machine dependent. 
