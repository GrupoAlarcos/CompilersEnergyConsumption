compile:
	/usr/lib/jvm/java-8-openjdk-amd64/bin/javac -d .  fannkuchredux.java
measure:
	sudo modprobe msr
	sudo ../../RAPL/main "/usr/local/src/jdk1.8.0_121/bin/java   fannkuchredux 12" Java fannkuch-redux

run:
	/usr/lib/jvm/java-8-openjdk-amd64/bin/java   fannkuchredux 12

mem:
	/usr/bin/time -v  /usr/local/src/jdk1.8.0_121/bin/java   fannkuchredux 12

valgrind:
	valgrind --tool=massif --stacks=yes  /usr/local/src/jdk1.8.0_121/bin/java   fannkuchredux 12
