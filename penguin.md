# h0 - Getting started

a) Right in the beginning I created the Github repository called linux-course.
b) I then created a file named penguin.md in the linux-course repository.
c) Final step was to publish the site to Laksu, which I did as insructed. 

## End of h0

# h1 - Have to start somwhere

My setup has Windows 11 Home (64 bit) with AMD Ryzen 5 5600X 6-Core Processor (3.70 GHz) and 16 Gb or RAM


a) First task: Enable VT-X in BIOS
- At first I had to enable VT-X in my computers BIOS, which was a real troble.
- I then discovered the problem was, that the instruction was for Intel, and I'm using AMD with Asus motherboard. When I realized that VT-X is called SVM in this combination I have, it was a peace of cake to change the settings and then boot up my computer. 

b) Second task: Download VirtualBox. 
- I went to https://www.virtualbox.org/wiki/Downloads and selected "windows host" to start download.
- Then I proceeded with the installation setup and after selecting the correct location for the program, I finished the Install. 

c) Third task: Download and install Debian.
- I went to https://www.debian.org/download and clicked on "debian-13.3.0-amd64-netinst.iso." to start the download.
<img width="613" height="218" alt="image" src="https://github.com/user-attachments/assets/bb5263aa-dba1-4548-9d92-7f366824ef12" />

- I followed the instructions from: https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md (Phase 3, How to create a new virtual machine to Virtualbox?)
- The process went trough as instructed and I was able to launch Debian installation on VirtualBox
<img width="440" height="367" alt="Eka käynnistys" src="https://github.com/user-attachments/assets/39332947-12e6-46f7-8c22-ae28c83aa892" />

- I went trough the Live Install process as instructed on https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md (Phase 4 How to install Debian to the VM?).
- After selecting right location, language and options the installation was ready.
<img width="631" height="476" alt="Asennusten jälkeen " src="https://github.com/user-attachments/assets/5a383cb5-5333-4c9e-9084-0e8c7746ad25" />


## h1 - Sources:
https://www.asus.com/fi/support/faq/1045141/

https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md

https://terokarvinen.com/linux-palvelimet/

https://www.debian.org/download

https://www.virtualbox.org/wiki/Downloads

## End of h1
 

