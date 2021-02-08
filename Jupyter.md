## Nice cheat sheet

https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Jupyter_Notebook_Cheat_Sheet.pdf

## Run pew in remote

export LC_ALL=C

pew new -p python3.6 -r rep_package/requirements.txt botse

**screen** => to start the screen

**screen -ls** => to check the list of screens

**ctrl-A+D** detach the screen

**ctrl-A+C** switch between screens

**screen -r ID** => to return to screen with the ID

**screen -rd** => to return

jupyter notebook --allow-root --no-browser --port=9091 --ip=0.0.0.0

ssh -N -L 8892:localhost:9091 mehdi@10.102.141.242


## Download package in notebook

import sys
!pip install package
