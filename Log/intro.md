## DAPlink 自制 记录
#### 介绍

![daklink](./images/intro-1.png)

DAPLink是ARM官方开源的一款调试烧录器，以前叫CMSIS DAP，现在改名叫DAPLink，同时在功能上也大大提高了。DAPLINK可以调试arm cortex全系列mcu，所以相比STLINK和jlink这方面更有优势。 官方的维护一直在更新，未来也会扩充更多功能进来。

#### 资源

官方Git源 [https://github.com/ARMmbed/DAPLink](https://github.com/ARMmbed/DAPLink)

#### 开始

[http://www.eemaker.com/daplink-yuanmabianyi.html](http://www.eemaker.com/daplink-yuanmabianyi.html)

1. 在本地新建目录 F:\DAP-LINK\software
2. 右键执行Git Bash
3. 键入 **git clone <源>** 把整个 daplink 源 clone 下来
4. 在 ..\software\DAPlink\ 文件夹下使用pip命令
5. 依次执行以下命令
```python
pip install virtualenv
virtualenv venv
##更新需要的工具，并且产生MDK工程,需要如下四条指令，有的指令执行时间稍久，等待一下
venv/Scripts/activate.bat
pip install -r requirements.txt
progen generate -t uvision
venv/Scripts/deactivate.bat
```
6. 编译 执行上述步骤后 我们的工程文件已经出现 在 projectfiles目录下

#### 芯片选型
由于2019年智能车制作的时，打算整个团队从K6x芯片转到LPC546xx芯片下，从NXP官方申请了样片。
2020年计划使用i.mx系列芯片，LPC芯片可能暂时用不上了，可以拿来制作DAPlink。
**但还需要考虑基础电路元件成本和编程时间成本。**

~~编译之后发现没有LPC54608这一项的工程~~

那么查看一下编译的流程 发现所有编译的工程都存在于 project.yaml 文件中

那么 观察目录，发现需要支持 GPIO,UART,USB,FLASH,IAP,UUID等功能，移植暂时无望，卒。

#### 那么进行CMSIS-DAP的移植（测试一下）
update soon.