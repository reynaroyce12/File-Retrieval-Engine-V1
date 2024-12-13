## File Retrieval Engine - Version 1

**This Program Does:**

This project implements a file retrieval engine that indexes text files in an input folder and performs search operations over the indexed data. The program supports the following:
- Indexing a directory and reading files within it.
- Searching for terms within indexed files, supporting both single-term queries and AND-based multiple term queries.
- Displays the time taken for indexing and search operations, along with the total bytes read.


#### A Few Points to Consider:
- The program uses **GCC** (G++) compiler and **CMake** for building and compilation.
- Indexing requires a folder path, and if the folder path is missing or invalid, the program will print error message.
- Search functionality handles **case-insensitive** queries and supports multi-term search using "AND" to find documents containing all the queried words.
- The engine processes only alphanumeric characters and ignores short words (length ≤ 2).
- if the search query is expressed with an AND query, the result will contain all the documents that contain **all** the terms from the AND query. 
- The results are sorted by the number of accumulated occurrences of all terms in each document, and only the top 10 documents are printed. 
- Validations are present in the program, so in the case of the below scenarios the progarm will print the appropriate messages to the user. 
    - Invalid Folder path
    - Folder does not exists
    - No folder path specifid
    - Missing search terms

#### The program also assumes that your enviroment already has the following installed and configured:

- GCC 14 C++ Compiler
- CMake (For generating build files)
- Git


## Folder and File Structure
The repository follows the below given folder and file structure:

```
CSC-435-PA2
├── app-cpp/
│   ├── include/
│   │   ├── AppInterface.hpp
│   │   ├── IndexStore.hpp
│   │   ├── ProcessingEngine.hpp
│   ├── src/
│   │   ├── AppInterface.cpp
│   │   ├── file-retrieval-engine.cpp
│   │   ├── IndexStore.cpp
│   │   ├── ProcessingEngine.cpp
├── CMakeLists.txt
```


## How to build and run the program

### 1. Creating the `build/` Directory 

For creating the build folder, navigate to the `app-cpp` folder and create the build folder by using the command below. This folder will contain the build files generated by CMake.

```` 
mkdir build
````

### 2. Run CMake commands to intiate the Build process

Navigate into the `build/` directory and run CMake commands to intialise the project.

````
cd build
cmake ..
````

### 3. Build the program

Navigate back into the `app-cpp` folder of the reposiory and run the build commands. 

```
cd ..
cmake --build build/
```

### 4. Execute the program

Once the build process is complete, run the program with the command provided below. Before running this command, make sure you are in the 'app-cpp' folder. 

This project's executable name is 'file-retrieval-engine'. And since the executable file will be present in the build folder, when using the command given below, you must specify the correct path to it.

```
./build/file-retrieval-engine
```

After running the previous command, the program will start to execute and you will see the below given prompt on the console window from which you can perform the specified operations.

```
./build/file-retrieval-engine
> <index | search | quit>
```

#### Example:

```
./build/file-retrieval-engine
> <index | search | quit>  index ../../datasets/dataset1
Indexing completed with a total execution time of 9 seconds. Total bytes read: 134247377
> <index | search | quit>  search worms

Search executed in 592 μs.
Search Results: ( Top 10 out of 10)

../../datasets/dataset1/folder7/folderB/Document10991.txt (Frequency: 26)
../../datasets/dataset1/folder3/Document10383.txt (Frequency: 22)
../../datasets/dataset1/folder4/Document10553.txt (Frequency: 18)
../../datasets/dataset1/folder3/Document1043.txt (Frequency: 13)
../../datasets/dataset1/folder4/Document10600.txt (Frequency: 8)
../../datasets/dataset1/folder3/folderA/Document10431.txt (Frequency: 6)
../../datasets/dataset1/folder2/folderA/Document10340.txt (Frequency: 5)
../../datasets/dataset1/folder8/Document1105.txt (Frequency: 4)
../../datasets/dataset1/folder4/Document10513.txt (Frequency: 4)
../../datasets/dataset1/folder3/Document1039.txt (Frequency: 4)
```