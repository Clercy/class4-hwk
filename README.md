# class4-hwk
#-------------------------------------------------------------------------
#Successful recipe to this point
FROM ubuntu:16.04
MAINTAINER Luigi Clerici <Clercy.github.io>
RUN apt-get update
RUN cat /etc/lsb-release
#RUN apt-get install -y python
RUN apt-get install -y python3-pip
RUN pip3 install numpy pandas
# Set the working directory to /app
#WORKDIR /app

# Copy the current directory contents into the container at /app
ADD our_csv_parser_My_Homework.py housing.data.txt /

# Run script when the container launches
CMD ["python3", "./our_csv_parser_My_Homework.py"]

#
#  Install: python3 instead of python2 (if its not 3 already)
#  Install: pip (python page installer) for the corresponding Python 3
#  Use pip to install: numpy, pandas
#
#-------------------------------------------------------------------------

#Last build before successful RUN
lcler@LAPTOP-D2T6EOO0 MINGW64 ~/Desktop/class4-hwk (master)
$ docker build -t class4-python-image ./
Sending build context to Docker daemon  139.3kB
Step 1/8 : FROM ubuntu:16.04
 ---> 7e87e2b3bf7a
Step 2/8 : MAINTAINER Luigi Clerici <Clercy.github.io>
 ---> Using cache
 ---> 5a4d6caa160f
Step 3/8 : RUN apt-get update
 ---> Using cache
 ---> d564a701771e
Step 4/8 : RUN cat /etc/lsb-release
 ---> Using cache
 ---> 9ffdbeeb9ee4
Step 5/8 : RUN apt-get install -y python3-pip
 ---> Using cache
 ---> bdd5bb4b1600
Step 6/8 : RUN pip3 install numpy pandas
 ---> Using cache
 ---> 6475339f61ae
Step 7/8 : ADD our_csv_parser_My_Homework.py housing.data.txt /
 ---> Using cache
 ---> 18a7e3fb610e
Step 8/8 : CMD ["python3", "./our_csv_parser_My_Homework.py"]
 ---> Running in 3d29a0f70404
Removing intermediate container 3d29a0f70404
 ---> b34e337a9fc0
Successfully built b34e337a9fc0
Successfully tagged class4-python-image:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

#When executed the following run command received this message.
lcler@LAPTOP-D2T6EOO0 MINGW64 ~/Desktop/class4-hwk (master)
$ docker run -ti class4-python-image
the input device is not a TTY.  If you are using mintty, try prefixing the command with 'winpty'

#I proceeded to execute without the "t" and the script ran
lcler@LAPTOP-D2T6EOO0 MINGW64 ~/Desktop/class4-hwk (master)
$ docker run -i class4-python-image
[0.00632, 18.0, 2.31, 0, 0.538, 6.575, 65.2, 4.09, 1, 296.0, 15.3, 396.9, 4.98, 24.0]
59.635665714285715
124.29256675476427
[0.02731, 0.0, 7.07, 0, 0.469, 6.421, 78.9, 4.9671, 2, 242.0, 17.8, 396.9, 9.14, 21.6]
56.235315
117.35289232650675
