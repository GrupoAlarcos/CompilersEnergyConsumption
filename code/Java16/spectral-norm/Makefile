compile:
	/usr/lib/jvm/java-16-openjdk-amd64/bin/javac -d .  spectralnorm.java
measure:
	sudo modprobe msr
	sudo ../../RAPL/main "/usr/local/src/jdk1.8.0_121/bin/java   spectralnorm 5500" Java spectral-norm

run:
	/usr/lib/jvm/java-16-openjdk-amd64/bin/java   spectralnorm 5500

mem:
	/usr/bin/time -v /usr/local/src/jdk1.8.0_121/bin/java   spectralnorm 5500

valgrind:
	valgrind --tool=massif --stacks=yes /usr/local/src/jdk1.8.0_121/bin/java   spectralnorm 5500
