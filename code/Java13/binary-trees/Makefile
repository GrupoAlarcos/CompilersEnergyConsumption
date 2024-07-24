compile:
	/usr/lib/jvm/java-13-openjdk-amd64/bin/javac -d .  binarytrees.java
measure:
	sudo modprobe msr
	sudo ../../RAPL/main "/usr/local/src/jdk1.8.0_121/bin/java binarytrees 21" Java binary-trees

run:
	/usr/lib/jvm/java-13-openjdk-amd64/bin/java binarytrees 21

mem:
	/usr/bin/time -v /usr/local/src/jdk1.8.0_121/bin/java binarytrees 21

valgrind:
	valgrind --tool=massif --stacks=yes /usr/local/src/jdk1.8.0_121/bin/java binarytrees 21
