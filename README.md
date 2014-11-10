how to use:
1. copy lunatik to lib
2. edit lib/Kconfig,add LUNATIK config as show below.

config LUNATIK
	tristate "Enable Lunatik Lua Engine"
	default y
	help
	  Enables the Lunatik Lua engine which allows execution of Lua code
	  in the context of the kernel. This enables a new syscall (#350) with the signature
	  sys_lua(char *code, size_t code_len, char *result, size_t result_len).

3. run : make ARCH=arm menuconfig
config Lunatik to compile as Module

  Library routines  ---> 
     <M> Enable Lunatik Lua Engine 
     
4. run : make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- modules SUBDIRS=lib/lunatik
    if everything is ok,you will see a file called luak.ko in lib/lunatic directory

5. how to use.

insmod luak.ko
cat /proc/kmsg
echo "print('hello,world')" > /sys/class/lunak/eval

and you will see the output as show below:

<4>[ 4772.403753] hello,world


that's it,you have successfully run lua script in linux kernel on arm platform!



