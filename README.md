Device configuration for Sony Xperia XZ1 SOV36 (poplar_kddi)
========================================================

Description
-----------

This repository is for LineageOS 18.1 on Sony Xperia XZ1 SOV36 (poplar_kddi).

How to build LineageOS
----------------------

* Make a workspace:

        mkdir -p ~/lineageos
        cd ~/lineageos

* Initialize the repo:

        repo init -u git://github.com/LineageOS/android.git -b lineage-18.1

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="whatawurst/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-18.1" />
            <project name="whatawurst/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="lineage-18.1" />
            <project name="whatawurst/android_device_sony_poplar_kddi" path="device/sony/poplar_kddi" remote="github" revision="lineage-18.1" />

            <!-- Pinned blobs for poplar -->
            <project name="whatawurst/android_vendor_sony_poplar_kddi" path="vendor/sony/poplar_kddi" remote="github" revision="lineage-18.1" />
        </manifest>

* Sync the repo:

        repo sync

* Extract vendor blobs

        cd device/sony/poplar_kddi
        ./extract-files.sh

* Setup the environment

        source build/envsetup.sh
        lunch lineage_poplar_kddi-userdebug

* Build LineageOS

        make -j8 bacon
