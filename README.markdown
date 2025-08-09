# 🚀 Jetson Nano Boot & Setup Guide 🌟

Welcome to the ultimate guide for unlocking the full potential of your **Jetson Nano**! This comprehensive, step-by-step tutorial will guide you through resetting, configuring, and optimizing your Jetson Nano for cutting-edge deep learning tasks. From booting via SSD to installing **YOLOv5** for real-time object detection, this guide is crafted for both beginners and seasoned developers. Let’s embark on this exciting journey to supercharge your Jetson Nano! 🎉

---

## 🔄 Resetting Your Jetson Nano

To reset your Jetson Nano and prepare it for deep learning, we’ll start by setting up a virtual machine with **Ubuntu Linux** on your computer (Figure 1). This establishes a robust foundation for a clean and efficient setup.

> **⚠️ Critical Note:** You **must** use **Ubuntu 18.04**, as other versions are incompatible with the Jetson Nano.

**Download Link:** [1] https://releases.ubuntu.com/18.04/

![Figure 1: Downloading Ubuntu 18.04](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ubuntu%20versiyon%2018.04%20indirme.png)

Once Ubuntu is installed, download the **Nvidia SDK Manager** on the virtual machine (Figure 2). Visit the link below, select the “**.deb Ubuntu**” option, and log in or sign up for an Nvidia account to proceed. Without an account, the installation will fail.

**Link:** [2] https://developer.nvidia.com/drive/sdk-manager

![Figure 2: Nvidia SDK Manager Download](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20jetson%20nano%20indirme.png)

Navigate to the download directory in Ubuntu, open a terminal, and run:

```bash
sudo dpkg -i nvidiasdkmanager.deb
```

If an error occurs, resolve it with:

```bash
sudo apt --fix-broken install
```

Retry the `dpkg` command—it should now work flawlessly.

Launch the **Nvidia SDK Manager** to access the login screen (Figure 3). After logging in, a user-friendly interface will appear.

![Figure 3: Nvidia SDK Manager Login](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20log%20in%20ekran%C4%B1.png)

Select your **Jetson Nano model** under the “**Target Hardware**” section (Figure 4). Choosing the correct model ensures compatibility.

![Figure 4: Selecting Your Jetson Nano Model](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri%20se%C3%A7im%20ekran%C4%B1%20.png)

Check the box for **DeepStream** under “**ADDITIONAL SDKS**” and proceed to **Step 2** (Figure 5).

![Figure 5: DeepStream Selection](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/download%20ve%20install%20ekran%C4%B1.png)

In **Step 2**, accept the privacy policy. Choose between:
- **Download now. Install later**: Downloads files for manual installation.
- **Direct Download and Install**: Performs immediate installation (this may take time).

Select **Manual Setup** instead of “Automatic Setup - Jetson Nano” (Figure 6).

![Figure 6: Manual Setup Selection](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/manuel%20setup%20jetson%20nano.png)

Enter a new **username** and **password** for the Jetson Nano, then click **Finish** to continue.

The **SDK Components** screen (Figure 7) allows you to install essential software like **CUDA**, **CUDA X-AI**, and **OpenCV** for deep learning and image processing.

![Figure 7: SDK Components Installation](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20paketleri%20y%C3%BCkleme%20.png)

Choose your installation method:
1. **USB Connection**: The virtual machine shares its internet via USB. Keep the IP address unchanged.
2. **Ethernet Connection**: Use a USB Wi-Fi adapter, enter the Jetson Nano’s IP address, and proceed.

Upon completion, the Jetson Nano will have the necessary deep learning libraries and will boot automatically. Connect it to a monitor to access the login screen and enter your credentials.

> **💡 Pro Tip:** Skipping the installation requires manual library installation via the Jetson Nano’s terminal. Find detailed instructions here: [3] https://github.com/55selcukozdemir/web_self-car/blob/main/README.md

![Figure 8: Jetson Nano Models](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri.png)

As shown in Figure 8, Jetson Nano has three models: **Jetson Nano**, **Jetson Nano (Developer Kit)**, and **Jetson Nano (2GB Developer Kit)**.

- **SD Card Models**: A 64GB SD card offers sufficient storage for deep learning libraries.
- **Non-SD Card Models (4GB RAM, 16GB Internal Storage)**: Internal storage is inadequate, so use an external device (e.g., hard disk, SSD, or flash drive). An **SSD** is recommended for superior performance, as flash drives and hard disks are slower.

---

## 💾 Booting from an SSD

**Reference Video:** [4] https://youtu.be/53rRMr1IpWs

To boot from an SSD, clone the required repository:

```bash
git clone https://github.com/JetsonHacksNano/bootFromUSB.git
```

Navigate to the repository:

```bash
cd bootFromUSB
```

![Figure 9: Disks Application](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/diskler.png)

Format the SSD (Figure 9). Search for “**disks**” and open the Disks application (Figure 10).

![Figure 10: Selecting the SSD](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ssd.png)

Select the SSD, click the three-line menu, and choose **Format Disk** (Figure 11). Set partitioning to **GPT** (Figure 12), then confirm (Figure 13).

![Figure 11: Format Disk Option](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/format.png)

![Figure 12: GPT Partitioning](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/GPT.png)

![Figure 13: Format Confirmation](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/areyousure.png)

Create a new partition by clicking the **+** button (Figure 14).

![Figure 14: Creating a New Partition](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/%2Bssd.jpg)

Partition the SSD, name it, and select **Internal disk for use with Linux systems only (Ext4)** under “Type” (Figure 15). Click **Create** to finalize (Figure 16).

![Figure 15: Partitioning the SSD](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/disk%20b%C3%B6lme.png)

![Figure 16: Ext4 Partition Type](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ext4.png)

Verify the SSD:

```bash
ls /dev/sda*
```

Copy system files to the SSD:

```bash
./copyRootToUSB.sh -p /dev/sda1
```

Navigate to the SSD’s **boot/extlinux** directory and open a terminal:

```bash
sudo cp extlinux.conf extlinux.conf.original
```

Edit the **extlinux.conf** file:

```bash
sudo gedit extlinux.conf
```

![Figure 17: Editing extlinux.conf](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/extlinuxconfig.png)

Copy the marked section, paste it below, and replace “primary” with “sdcard” (Figure 18).

![Figure 18: Modifying extlinux.conf](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sdcard.png)

Update the root partition for SSD booting:

```bash
./partUUID.sh
```

![Figure 19: Finding the SSD PARTUUID](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/partuuid.png)

Copy the “**root=PARTUUID=...**” string and paste it into the “root” section of the primary entry in **extlinux.conf** (Figure 20).

![Figure 20: Updating the Root Partition](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/root.png)

> **⚠️ Note:** The PARTUUID (e.g., “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1”) is unique to your SSD. Ensure you use the correct value.

Save and close **extlinux.conf** with **Ctrl+S**.

### 🌟 SD Card Supported Jetson Nano

For SD card-supported models, shut down the Jetson Nano, ensure no SD card is inserted, and power it on. Verify the boot:

```bash
lsblk
```

![Figure 21: Verifying SSD Boot](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/lsblk.png)

If “**/**” appears next to **sda1**, the SSD boot is successful.

### 🌟 Non-SD Card Supported Jetson Nano

For models without SD card support, delete all system files from internal storage. The device will shut down. Restart with the SSD connected to boot from it. Verify with:

```bash
lsblk
```

Ensure “**/**” appears next to **sda1**.

---

## 🖼️ Installing YOLOv5 on Jetson Nano

**Reference Video:** [5] https://youtu.be/oKaLyow7hWU

Let’s harness the power of **YOLOv5** for real-time object detection! Clone the YOLOv5 repository:

```bash
git clone https://github.com/ultralytics/yolov5.git
```

Navigate to the **yolov5** directory and review the **requirements.txt** file for required libraries. We’ll install **OpenCV 4.1.1** (not 4.1.2 as listed) without pip to optimize GPU performance with CUDA.

### 🎯 Step 1: Install OpenCV

> **Note:** Skip this step if OpenCV was installed via Nvidia SDK Manager.

Clone the OpenCV repository:

```bash
git clone https://github.com/JetsonHacksNano/buildOpenCV.git
```

Navigate to **buildOpenCV** and set “**NUM_JOBS**” to 1 for non-SD card models (Figure 22).

![Figure 22: Modifying NUM_JOBS](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_jobs.png)

Save the file and run:

```bash
cd buildOpenCV
./buildOpenCV
```

### 🎯 Step 2: Install Additional Libraries

Install **python3-pip**:

```bash
sudo apt install python3-pip
```

Install the required libraries:

```bash
pip3 install -U PyYAML==5.3.1
pip3 install tqdm
pip3 install cython
pip3 install -U numpy==1.18.5
sudo apt install build-essential libssl-dev python3-dev
pip3 install cycler==0.10
pip3 install kiwisolver==1.3.1
pip3 install pyparsing==2.4.7
pip3 install python-dateutil==2.8.2
pip3 install --no-deps matplotlib==3.2.2
sudo apt install gfortran
sudo apt install libopenblas-dev
sudo apt install liblapack-dev
pip3 install scipy==1.4.1
sudo apt install libjpeg-dev
pip3 install pillow==8.3.2
pip3 install typing-extensions==3.10.0.2
```

### 🎯 Step 3: Install PyTorch and Torchvision

The Jetson Nano’s ARM architecture requires a specialized PyTorch installation. Follow Nvidia’s forum instructions: [6] https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

![Figure 23: PyTorch Versions](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/torchvision.png)

Select **PyTorch 1.10** for Python 3.6 (Figure 24).

![Figure 24: PyTorch and Torchvision Compatibility](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/python%20torchvision.png)

Download the PyTorch wheel file (Figure 25):

```bash
wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O torch-1.10.0-cp36-cp36m-linux_aarch64.whl
```

Install dependencies:

```bash
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev
```

Install the PyTorch wheel file:

```bash
pip3 install --no-deps torch-1.10.0-cp36-cp36m-linux_aarch64.whl
```

Install **Torchvision**:

```bash
sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
git clone --branch v0.11.1 https://github.com/pytorch/vision torchvision
cd torchvision
export BUILD_VERSION=0.9.0
python3 setup.py install --user
```

Install **Seaborn**:

```bash
pip3 install --no-deps seaborn==0.11.0
```

Test YOLOv5:

```bash
cd yolov5
python3 detect.py --source data/images --weights yolov5s.pt
```

![Figure 26: YOLOv5 Test Results](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sonu.png)

The pretrained **yolov5s.pt** model accurately detects objects like people and buses (Figure 26).

### 📷 RealSense Library for Real-Time Processing

For real-time image processing, install the **RealSense SDK**:

```bash
git clone https://github.com/jetsonhacks/installRealSenseSDK.git
cd installRealSenseSDK
```

Edit **buildLibrealsense**, replacing “**NUM_PROCS**” with 1 (Figure 27).

![Figure 27: Modifying NUM_PROCS](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_proc.png)

Run the build script:

```bash
./buildLibrealsense.sh
```

Verify the installation:

```bash
python3
import pyrealsense2
```

If an error occurs (Figure 28), update the Python path.

![Figure 28: Pyrealsense Error](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense.png)

Edit **.bashrc**, changing **/usr/local/lib** to **/usr/local/lib/python3.6/pyrealsense2** (Figure 29).

![Figure 29: Updating Python Path](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pythonpath.png)

Apply changes:

 []./installRealSenseSDK
./buildLibrealsense.sh
```

Verify again:

```bash
python3
import pyrealsense2 as rs
```

A successful import moves to the next line (Figure 30).

![Figure 30: Successful Pyrealsense Import](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense2.png)

Install **libcanberra-gtk**:

```bash
sudo apt install libcanberra-gtk*
```

### 🎥 Camera Testing with YOLOv5

Run real-time detection:

```bash
cd yolov5
python detect.py --weights yolov5s.pt --source 0
```

The **.pt** file contains the trained model. The **yolov5s.pt** tests pretrained models for objects like people and computers. For the **Teknofest Agricultural Unmanned Vehicle CORE Team**, we trained a custom **.pt** file to detect and spray foreign plants (Figure 31).

![Figure 31: Custom YOLOv5 Detection](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/yabanci-bitki.jpg)

---

## 📚 References

1. https://releases.ubuntu.com/18.04/
2. https://developer.nvidia.com/drive/sdk-manager  
   https://youtu.be/0nplGFQ07po
3. https://github.com/55selcukozdemir/web_self-car/blob/main/README.md
4. https://youtu.be/53rRMr1IpWs
5. https://youtu.be/oKaLyow7hWU
6. https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

---

# 🌟 JetsonNano-bootandsetup (Türkçe)

## 🔄 JETSON NANO SIFIRLAMA

Jetson Nano’yu sıfırlamak ve derin öğrenme projelerine hazırlamak için bir sanal makine kuruyoruz ve bu makineye **Ubuntu Linux** yüklüyoruz (Şekil 1). Bu, temiz ve verimli bir kurulumun temelini oluşturur.

> **⚠️ Önemli Not:** **Ubuntu 18.04** sürümünü indirmelisiniz; diğer sürümler Jetson Nano ile uyumlu değildir.

**İndirme Linki:** [1] https://releases.ubuntu.com/18.04/

![Şekil 1: Ubuntu 18.04 İndirme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ubuntu%20versiyon%2018.04%20indirme.png)

Ubuntu yüklendikten sonra, sanal makineye **Nvidia SDK Manager**’ı indirin (Şekil 2). Aşağıdaki linkten “**.deb Ubuntu**” seçeneğini seçin ve Nvidia hesabıyla giriş yapın veya kaydolun. Hesap olmadan kurulum çalışmaz.

**Link:** [2] https://developer.nvidia.com/drive/sdk-manager

![Şekil 2: Nvidia SDK Manager İndirme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20jetson%20nano%20indirme.png)

İndirme dizinine gidin, terminal açın ve şu komutu çalıştırın:

```bash
sudo dpkg -i nvidiasdkmanager.deb
```

Hata alırsanız:

```bash
sudo apt --fix-broken install
```

`dpkg` komutunu tekrar deneyin; artık sorunsuz çalışacaktır.

**Nvidia SDK Manager**’ı başlatın. Giriş ekranı görünecek (Şekil 3). Giriş yaptıktan sonra kullanıcı dostu arayüz açılır.

![Şekil 3: Nvidia SDK Manager Giriş](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20log%20in%20ekran%C4%B1.png)

“**Target Hardware**” bölümünden **Jetson Nano modelinizi** seçin (Şekil 4). Doğru model seçimi uyumluluk için kritiktir.

![Şekil 4: Jetson Nano Model Seçimi](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri%20se%C3%A7im%20ekran%C4%B1%20.png)

“**ADDITIONAL SDKS**” altında **DeepStream** kutusunu işaretleyin ve **2. Adım**’a geçin (Şekil 5).

![Şekil 5: DeepStream Seçimi](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/download%20ve%20install%20ekran%C4%B1.png)

**2. Adım**’da gizlilik politikasını kabul edin. Seçenekler:
- **Download now. Install later**: Dosyaları indirir, manuel kurulum için saklar.
- **Doğrudan İndir ve Kur**: Hemen kurulum yapar (uzun sürebilir).

“**Automatic Setup - Jetson Nano**” yerine **Manual Setup**’ı seçin (Şekil 6).

![Şekil 6: Manuel Kurulum Seçimi](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/manuel%20setup%20jetson%20nano.png)

Jetson Nano için yeni **kullanıcı adı** ve **şifre** girin, ardından **Finish**’e tıklayın.

**SDK Components** ekranı (Şekil 7), **CUDA**, **CUDA X-AI**, ve **OpenCV** gibi derin öğrenme ve görüntü işleme yazılımlarını yüklemenizi sağlar.

![Şekil 7: SDK Components Yükleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20paketleri%20y%C3%BCkleme%20.png)

Kurulum yöntemi seçin:
1. **USB Bağlantısı**: Sanal makine internetini USB ile paylaşır. IP adresini değiştirmeyin.
2. **Ethernet Bağlantısı**: USB Wi-Fi adaptörü kullanın, Jetson Nano’nun IP adresini girin ve devam edin.

Kurulum tamamlandığında, Jetson Nano derin öğrenme kütüphanelerini yüklemiş olacak ve otomatik olarak açılacaktır. Giriş ekranını görmek için monitöre bağlayın ve kimlik bilgilerinizi girin.

> **💡 İpucu:** Kurulumu atlarsanız, kütüphaneleri Jetson Nano terminalinden manuel yüklemeniz gerekir. Ayrıntılı talimatlar: [3] https://github.com/55selcukozdemir/web_self-car/blob/main/README.md

![Şekil 8: Jetson Nano Modelleri](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri.png)

Şekil 8’de görüldüğü gibi, Jetson Nano’nun üç modeli vardır: **Jetson Nano**, **Jetson Nano (Developer Kit)**, ve **Jetson Nano (2GB Developer Kit)**.

- **SD Kart Modelleri**: 64GB SD kart, derin öğrenme kütüphaneleri için yeterli depolama sağlar.
- **SD Kart Desteksiz Modeller (4GB RAM, 16GB Dahili Depolama)**: Dahili depolama yetersizdir; harici bir cihaz (sabit disk, SSD veya flash bellek) kullanın. En iyi performans için **SSD** önerilir.

## 💾 SSD'den Önyükleme

**Yararlanılan Video:** [4] https://youtu.be/53rRMr1IpWs

SSD’den önyükleme için gerekli depoyu kopyalayın:

```bash
git clone https://github.com/JetsonHacksNano/bootFromUSB.git
```

Depoya gidin:

```bash
cd bootFromUSB
```

![Şekil 9: Diskler Uygulaması](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/diskler.png)

SSD’yi formatlayın (Şekil 9). “**disks**” araması yapın ve Diskler uygulamasını açın (Şekil 10).

![Şekil 10: SSD Seçimi](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ssd.png)

SSD’yi seçin, üç çizgili menüden **Format Disk**’i seçin (Şekil 11). Bölümlemeyi **GPT** yapın (Şekil 12) ve formatı onaylayın (Şekil 13).

![Şekil 11: Disk Formatlama](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/format.png)

![Şekil 12: GPT Bölümleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/GPT.png)

![Şekil 13: Format Onayı](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/areyousure.png)

**+** düğmesine tıklayarak yeni bir bölüm oluşturun (Şekil 14).

![Şekil 14: Yeni Bölüm Oluşturma](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/%2Bssd.jpg)

SSD’yi bölün, isim verin ve “Type” altında **Internal disk for use with Linux systems only (Ext4)** seçin (Şekil 15). **Create** ile tamamlayın (Şekil 16).

![Şekil 15: SSD Bölümleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/disk%20b%C3%B6lme.png)

![Şekil 16: Ext4 Bölüm Türü](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ext4.png)

SSD’yi kontrol edin:

```bash
ls /dev/sda*
```

Sistem dosyalarını SSD’ye kopyalayın:

```bash
./copyRootToUSB.sh -

 /dev/sda1
```

SSD’nin **boot/extlinux** dizinine gidin ve terminal açın:

```bash
sudo cp extlinux.conf extlinux.conf.original
```

**extlinux.conf** dosyasını düzenleyin:

```bash
sudo gedit extlinux.conf
```

![Şekil 17: extlinux.conf Düzenleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/extlinuxconfig.png)

İşaretli bölümü kopyalayın, altına yapıştırın ve “primary” kısmını “sdcard” ile değiştirin (Şekil 18).

![Şekil 18: extlinux.conf Güncelleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sdcard.png)

SSD’den önyükleme için root kısmını güncelleyin:

```bash
./partUUID.sh
```

![Şekil 19: SSD PARTUUID Bulma](https://github.com/Farukcinemre/Jetくなります

**Şekil 19: SSD PARTUUID Bulma](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/partuuid.png)

“**root=PARTUUID=...**” dizesini kopyalayın ve **extlinux.conf**’daki primary girişinin “root” kısmına yapıştırın (Şekil 20).

![Şekil 20: Root Bölümünü Güncelleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/root.png)

> **⚠️ Not:** PARTUUID (ör. “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1”) SSD’nize özeldir. Doğru değeri kullanın.

**extlinux.conf**’u **Ctrl+S** ile kaydedip kapatın.

### 🌟 SD Kart Destekli Jetson Nano

SD kart destekli modellerde, Jetson Nano’yu kapatın, SD kartın takılı olmadığından emin olun ve açın. Önyüklemeyi kontrol edin:

```bash
lsblk
```

![Şekil 21: SSD Önyükleme Doğrulama](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/lsblk.png)

**sda1** yanında “**/**” görünüyorsa, SSD önyüklemesi başarılıdır.

### 🌟 SD Kart Desteksiz Jetson Nano

SD kart desteği olmayan modellerde, dahili depolamadaki tüm sistem dosyalarını silin. Cihaz kapanacaktır. SSD takılıyken yeniden başlatın; SSD’den önyükleme yapacaktır. Doğrulayın:

```bash
lsblk
```

**sda1** yanında “**/**” olduğundan emin olun.

## 🖼️ Jetson Nano’ya YOLOv5 Kurulumu

**Yararlanılan Video:** [5] https://youtu.be/oKaLyow7hWU

Gerçek zamanlı nesne algılama için **YOLOv5**’i kuralım! Depoyu kopyalayın:

```bash
git clone https://github.com/ultralytics/yolov5.git
```

**yolov5** dizinine gidin ve **requirements.txt** dosyasını inceleyin. **OpenCV 4.1.1**’i (listede 4.1.2 olarak görünse de) pip olmadan kuracağız, böylece CUDA ile GPU performansını maksimize edeceğiz.

### 🎯 1. Adım: OpenCV Yükleme

> **Not:** OpenCV’yi Nvidia SDK Manager ile yüklediyseniz bu adımı atlayın.

OpenCV deposunu kopyalayın:

```bash
git clone https://github.com/JetsonHacksNano/buildOpenCV.git
```

**buildOpenCV** dizinine gidin ve SD kart destekli olmayan modeller için “**NUM_JOBS**” değerini 1 yapın (Şekil 22).

![Şekil 22: NUM_JOBS Düzenleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_jobs.png)

Dosyayı kaydedin ve çalıştırın:

```bash
cd buildOpenCV
./buildOpenCV
```

### 🎯 2. Adım: Ek Kütüphaneleri Yükleme

**python3-pip**’i yükleyin:

```bash
sudo apt install python3-pip
```

Gerekli kütüphaneleri yükleyin:

```bash
pip3 install -U PyYAML==5.3.1
pip3 install tqdm
pip3 install cython
pip3 install -U numpy==1.18.5
sudo apt install build-essential libssl-dev python3-dev
pip3 install cycler==0.10
pip3 install kiwisolver==1.3.1
pip3 install pyparsing==2.4.7
pip3 install python-dateutil==2.8.2
pip3 install --no-deps matplotlib==3.2.2
sudo apt install gfortran
sudo apt install libopenblas-dev
sudo apt install liblapack-dev
pip3 install scipy==1.4.1
sudo apt install libjpeg-dev
pip3 install pillow==8.3.2
pip3 install typing-extensions==3.10.0.2
```

### 🎯 3. Adım: PyTorch ve Torchvision Yükleme

Jetson Nano’nun ARM mimarisi özel bir PyTorch kurulumu gerektirir. Nvidia forumundaki talimatları takip edin: [6] https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

![Şekil 23: PyTorch Sürümleri](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/torchvision.png)

Python 3.6 için **PyTorch 1.10**’u seçin (Şekil 24).

![Şekil 24: PyTorch ve Torchvision Uyumluluğu](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/python%20torchvision.png)

PyTorch wheel dosyasını indirin (Şekil 25):

```bash
wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O torch-1.10.0-cp36-cp36m-linux_aarch64.whl
```

Bağımlılıkları yükleyin:

```bash
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev
```

PyTorch wheel dosyasını yükleyin:

```bash
pip3 install --no-deps torch-1.10.0-cp36-cp36m-linux_aarch64.whl
```

**Torchvision**’ı yükleyin:

```bash
sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
git clone --branch v0.11.1 https://github.com/pytorch/vision torchvision
cd torchvision
export BUILD_VERSION=0.9.0
python3 setup.py install --user
```

**Seaborn**’u yükleyin:

```bash
pip3 install --no-deps seaborn==0.11.0
```

YOLOv5’i test edin:

```bash
cd yolov5
python3 detect.py --source data/images --weights yolov5s.pt
```

![Şekil 26: YOLOv5 Test Sonuçları](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sonu.png)

Önceden eğitilmiş **yolov5s.pt** modeli, insanlar ve otobüs gibi nesneleri doğru bir şekilde algıladı (Şekil 26).

### 📷 Gerçek Zamanlı İşleme için RealSense Kütüphanesi

Gerçek zamanlı görüntü işleme için **RealSense SDK**’yı yükleyin:

```bash
git clone https://github.com/jetsonhacks/installRealSenseSDK.git
cd installRealSenseSDK
```

**buildLibrealsense** dosyasını düzenleyin, “**NUM_PROCS**” değerini 1 yapın (Şekil 27).

![Şekil 27: NUM_PROCS Düzenleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_proc.png)

Derleme komutunu çalıştırın:

```bash
./buildLibrealsense.sh
```

Yüklemeyi doğrulayın:

```bash
python3
import pyrealsense2
```

Hata alırsanız (Şekil 28), Python yolunu güncelleyin.

![Şekil 28: Pyrealsense Hata](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense.png)

**.bashrc** dosyasını düzenleyin, **/usr/local/lib**’i **/usr/local/lib/python3.6/pyrealsense2** ile değiştirin (Şekil 29).

![Şekil 29: Python Yolu Güncelleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pythonpath.png)

Değişiklikleri uygulayın:

```bash
source ~/.bashrc
```

Tekrar doğrulayın:

```bash
python3
import pyrealsense2 as rs
```

Alt satıra geçerse kurulum başarılıdır (Şekil 30).

![Şekil 30: Başarılı Pyrealsense İçe Aktarma](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense2.png)

**libcanberra-gtk**’yı yükleyin:

```bash
sudo apt install libcanberra-gtk*
```

### 🎥 Kamera ile YOLOv5 Testi

Gerçek zamanlı algılama için:

```bash
cd yolov5
python detect.py --weights yolov5s.pt --source 0
```

**.pt** dosyası eğitilmiş modeli içerir. **yolov5s.pt** ile insanlar, bilgisayarlar gibi önceden eğitilmiş modeller test edilir. **Teknofest Tarımsal İnsansız Aracı CORE Ekibi** olarak, yabancı bitki algılama ve ilaçlama için özel bir **.pt** dosyası eğittik (Şekil 31).

![Şekil 31: Özel YOLOv5 Algılama](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/yabanci-bitki.jpg)

## 📚 Kaynakça

1. https://releases.ubuntu.com/18.04/
2. https://developer.nvidia.com/drive/sdk-manager  
   https://youtu.be/0nplGFQ07po
3. https://github.com/55selcukozdemir/web_self-car/blob/main/README.md
4. https://youtu.be/53rRMr1IpWs
5. https://youtu.be/oKaLyow7hWU
6. https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048