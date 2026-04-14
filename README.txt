******************
* Used Ubunut 24 *
******************

Compile with the following scons:
---------------------------------
python3.12
zeroc
- sudo apt install zeroc*
- sudo apt install libzeroc*
postgresql
- sudo apt install postgres*
qt5
- sudo apt-get install qtdeclarative5-dev qml-module-qtquick-controls
- sudo apt install designer-qt6
- sudo apt install qt5*
- sudo apt install libqt53*
- sudo apt install qt3*
scons
- python3 -m pip install scons==4.2.0
---------------------------


Compile with cmake
-------------------------
mkdir build
cd build
cmake ..
make
--------------------------




sudo apt install pip
mv /usr/lib/python3.12/EXTERNALLY-MANAGED /home/zolly/Documents
python3 -m pip install scons==4.2.0



sudo -u postgres createuser --login --pwprompt wolly
passw: wolly
sudo -u postgres dropdb TEST_PROJECT
sudo -u postgres createdb --owner=wolly TEST_PROJECT
psql TEST_PROJECT
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

And then update with DatabaseEditor

The startup arguments for the applications you can find in the AppStarter.xml

In the ObjectViewer
- Planning nog finisched yet

SocketBox
- Open for imlplementing dll's with the protocoll for communication

MethodsDll/ObjectsDll
- Create Objects and Methods as wanted to your need
- Don't forget to copy the methods and objects to the runtime folder in the directory of the ObjectViewer from the ServerTest
- Don't forget to modify the XML files to load the methods and objects
