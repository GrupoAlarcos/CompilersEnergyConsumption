compile:
	/usr/lib/jvm/java-16-openjdk-amd64/bin/javac -d .  nbody.java
measure:
	sudo modprobe msr
	sudo ../../RAPL/main "/usr/local/src/jdk1.8.0_121/bin/java   nbody 50000000" Java n-body

run:
	/usr/lib/jvm/java-16-openjdk-amd64/bin/java   nbody 50000000

mem:
	/usr/bin/time -v /usr/local/src/jdk1.8.0_121/bin/java   nbody 50000000

valgrind:
	valgrind --tool=massif --stacks=yes /usr/local/src/jdk1.8.0_121/bin/java   nbody 50000000
