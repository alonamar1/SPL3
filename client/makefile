CFLAGS := -c -Wall -Weffc++ -g -std=c++11 -Iinclude
LDFLAGS := -lboost_system -lpthread

all: bin/StompEMIClient.exe checkMemo

bin/StompEMIClient.exe: bin/ConnectionHandler.o bin/StompClient.o bin/event.o bin/dataBaseClient.o bin/StompProtocol.o bin/Task.o
	g++ -o bin/StompEMIClient.exe bin/ConnectionHandler.o bin/StompClient.o bin/event.o bin/dataBaseClient.o bin/StompProtocol.o bin/Task.o $(LDFLAGS)

bin/ConnectionHandler.o: src/ConnectionHandler.cpp
	g++ $(CFLAGS) -o bin/ConnectionHandler.o src/ConnectionHandler.cpp

bin/StompClient.o: src/StompClient.cpp
	g++ $(CFLAGS) -o bin/StompClient.o src/StompClient.cpp

bin/event.o: src/event.cpp
	g++ $(CFLAGS) -o bin/event.o src/event.cpp

bin/dataBaseClient.o: src/dataBaseClient.cpp
	g++ $(CFLAGS) -o bin/dataBaseClient.o src/dataBaseClient.cpp

bin/StompProtocol.o: src/StompProtocol.cpp
	g++ $(CFLAGS) -o bin/StompProtocol.o src/StompProtocol.cpp

bin/Task.o: src/Task.cpp
	g++ $(CFLAGS) -o bin/Task.o src/Task.cpp

run: bin/StompEMIClient.exe
	./bin/StompEMIClient.exe

.PHONY: clean

checkMemo:
	valgrind --leak-check=full --show-reachable=yes --track-origins=yes ./bin/StompEMIClient.exe

clean:
	rm -f bin/*
