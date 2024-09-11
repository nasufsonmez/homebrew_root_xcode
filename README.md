In Xcode you need to set these PATHS

1. Instead of downloading and compiling ROOT/CERN from source. I use Brew package manager and installed the latest ROOT.

2. Then I need to find the main path Brew installed the libraries and headers related to ROOT.

  % root-config --cflags
  & -stdlib=libc++ -pthread -std=c++17 -m64 -I/opt/homebrew/Cellar/root/6.32.04/include/root

  The brew installed the the ROOT in the following path.
    /opt/homebrew/Cellar/root/6.32.04
    
3. I simply defined my variable ROOTSYS in XCode as "/opt/homebrew/Cellar/root/6.32.04"
4. The header search path as
    XCode setting: Header search path
    $(ROOTSYS)/include/root
5. The same for the ROOT sym libraries.
    XCode setting:Runpath search path
    $(ROOTSYS)/lib/root
6. The last is the linker flags for the executable.
 XCode setting:Other Linker flags

-L$(ROOTSYS)/lib/root
-lCore
-lImt
-lRIO
-lNet
-lHist
-lGraf
-lGraf3d
-lGpad
-lROOTVecOps
-lTree
-lTreePlayer
-lRint
-lPostscript
-lMatrix
-lPhysics
-lMathCore
-lThread
-lMultiProc
-lROOTDataFrame
-Wl,-rpath,$(ROOTSYS)/6.32.04/lib/root
-stdlib=libc++
-lpthread
-lm
-ldl

!! Beware these need to be added not as a one line but one entry in each line.

7. Then you should be good to go.

<img width="1438" alt="Screenshot 2024-09-11 at 16 24 12" src="https://github.com/user-attachments/assets/7c281ad7-f0c6-44d0-8ca4-89d60e10a71d">
<img width="1438" alt="Screenshot 2024-09-11 at 16 24 09" src="https://github.com/user-attachments/assets/06a99cff-750b-468d-a31e-f4b643433d46">

<img width="1189" alt="Screenshot 2024-09-11 at 16 21 46" src="https://github.com/user-attachments/assets/31e3cdb4-d84b-4f3e-89da-22b205988fab">

<img width="768" alt="Screenshot 2024-09-11 at 16 19 59" src="https://github.com/user-attachments/assets/14bf69d9-27b6-4c63-860c-dafb0a402a32">




