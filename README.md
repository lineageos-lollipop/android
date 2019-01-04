# LineageOS 12.1 (CM12.1)
To get started with Android/LineageOS, you'll need to get familiar with [Git](https://services.github.com/on-demand/downloads/github-git-cheat-sheet/) and [Repo](http://source.android.com/source/using-repo.html).


## Set up build environment
On the [LineageOS Wiki](https://wiki.lineageos.org), you will find additional useful information. (Just pick any device to find build instructions, but consider the device-specific statements not applicable). To build LineageOS 12.1, you need **OpenJDK 1.7**, which however is not part of the standard package repositories in a modern Linux distribution. See the Ask Ubuntu question [How do I install openjdk 7 on Ubuntu 16.04 or higher?](https://askubuntu.com/questions/761127/how-do-i-install-openjdk-7-on-ubuntu-16-04-or-higher). **Skip** the "PPA" suggestion even if it is the most upvoted and implement one of the next options.


## How to initially set up your build tree:
```Shell session
repo init -u https://github.com/cm12-amami/android.git -b cm-12.1 --groups=all,-notdefault,-darwin,-x86,-mips
cd .repo
git clone https://github.com/cm12-amami/local_manifests 
cd local_manifests 
git checkout cm-12.1 
cd ../.. 
repo sync --no-tags
```
Note: If you use a MAC to build, omit the `-darwin` in above `repo init` statement.

## How launch a cm-12.1 build:
```Shell session
make clean  
repo sync --no-tags 
source build/envsetup.sh  
brunch amami  
```

## How to contribute
Contributions (i.e. pull requests) are always welcome.
- We have an own [Thread on XDA](https://forum.xda-developers.com/sony-xperia-z1-compact/orig-development/lineageos-12-1-z1c-current-sec-patches-t3614936)
- You can also raise an issue on our [Issues page](https://github.com/cm12-amami/discussion/issues)


## Short on disk space and/or download bandwidth?
If you only want to build yourself from source and you don't want to really develop, analyze commit history and don't want to push commits to other repositories, you can drastically reduce the amount of downloaded data by modifying the above as follows (note: **NOT** recommended if you want to do anything more than just bulding 'as is'):
```Shell session
repo init -u https://github.com/cm12-amami/android.git -b cm-12.1 --depth=1 --groups=all,-darwin,-x86,-mips
cd .repo
git clone https://github.com/cm12-amami/local_manifests 
cd local_manifests 
git checkout cm-12.1 
cd ../.. 
repo sync --no-tags
```
