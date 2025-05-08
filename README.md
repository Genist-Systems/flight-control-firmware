The flight control firmware repo link is shown above. As of now, it should be public. 

You must clone using git. Type in this command below.
git clone https://github.com/Genist-Systems/flight-control-firmware --recursive
This may take some time if your internet is slow. It should take approximately 10-20 minutes.
Once this is done, best to verify all submodules have been initialized by typing:
git submodule update --init --recursive
and
git submodule sync

To compile the px4 files, we would use docker. Make sure you download docker first.

Once that is done, enter the flight-control-firmware directory,
cd flight-control-firmware
and type:
./Tools/docker_run.sh "make clean" 
./Tools/docker_run.sh "make px4_fmu-v6x_default"
This should compile the files. Check for errors. There will likely be some warnings though, but should be fine to ignore.
