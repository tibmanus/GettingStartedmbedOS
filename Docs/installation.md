# Installation

mbed OS works on your board, so you don't install it on your computer. What you need is a tool that takes your application code and the mbed OS code, then builds it into a single file that you can put on your board. That tool is called yotta, so yotta is what you need to install on your computer.

Once you've installed yotta, you can start building your applications. We explain the full process [in our review of yotta projects](Full_Guide/app_on_yotta.md).

There are two ways to install yotta: a regular local installation on your computer, or a Docker container.

## Regular local installation

For a full installation of yotta, see the instructions on the [yotta documentation site](http://yottadocs.mbed.com/#installing).

## yotta in a Docker container

Docker containers let you run an application such as yotta, with all of its dependencies (like Python), without installing anything directly on your machine. This protects you from version conflicts and other installation problems. 

We’ve built a yotta Docker container - a yocker - and a bash script (yotta.sh). The script allows you to use the yotta Docker container to mimic a yotta installation on your system; yotta will be fully functional.

### Prerequisites

[Please install Docker](https://www.docker.com/docker-toolbox).

### Installation

1. Start Docker. 

1. In the prompt, run:
	
	```
	docker pull mbed/yotta
	```

1. Save the [yotta script](https://github.com/ARMmbed/GettingStartedmbedOS/blob/master/Docs/Scripts/yotta.sh) on your computer. You’ll need to refer to its path when you use it in Docker later, so remember where it is.

### Using the yotta Docker and script to build projects

There is one difference between a regular installation and a Docker Container: in Docker, you'll have to precede each yotta command with the path to the bash script you saved in the previous section. For example:
	
```
../<path containing script>/yotta target frdm-k64f-gcc 	//sets the target
../<path containing script>/yotta build			//builds our project for the target
```

**Note:** If you saved your script under a name other than ``yotta``, you may need to enter the script’s full name, including extension. Our example will become ``../<path containing script>/<name.extension> target frdm-k64f-gcc``.

If you want to use yotta commands without specifying the full path to the script, you can add the yotta script’s path to your system’s ``path`` variable (Windows) or create a symbolic link (symlink) to your bin directory (Linux and Mac OS X). For example, to create a symlink: 
	
```
ln -s <path to your yotta.sh> /usr/bin/yotta
```

Now you can use yotta directly:
	
```
git clone <mbedos project>
cd <mbedos project>
yotta target frdm-k64f-gcc
yotta build
```


