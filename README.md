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



