# LineageOS 12.1 (CM12.1)
To get started with Android/LineageOS, you'll need to get familiar with [Git and Repo](http://source.android.com/source/using-repo.html).

## How to initially set up your build tree:
```Shell session
repo init -u https://github.com/cm12-amami/android.git -b cm-12.1 
cd .repo
git clone https://github.com/cm12-amami/local_manifests 
cd local_manifests 
git checkout cm-12.1 
cd ../.. 
repo sync
```

## How launch a cm-12.1 build:
```Shell session
make clean  
repo sync  
source build/envsetup.sh  
brunch amami  
```

## How to contribute
Contributions (i.e. pull requests) are always welcome.
- We have an own [Thread on XDA](https://forum.xda-developers.com/sony-xperia-z1-compact/orig-development/lineageos-12-1-z1c-current-sec-patches-t3614936)
- You can also raise an issue on out [Issues page](https://github.com/cm12-amami/discussion/issues)


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
