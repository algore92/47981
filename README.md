47981
=====
+# Project: MarkSort

+# Makefile created by Dev-C++ 4.9.9.2

+

+CPP  = g++.exe

+CC   = gcc.exe

+WINDRES = windres.exe

+RES  = 

+OBJ  = main.o $(RES)

+LINKOBJ  = main.o $(RES)

+LIBS =  -L"C:/Dev-Cpp/lib"  

+INCS =  -I"C:/Dev-Cpp/include" 

+CXXINCS =  -I"C:/Dev-Cpp/lib/gcc/mingw32/3.4.2/include"  -I"C:/Dev-Cpp/include/c++/3.4.2/backward"  -I"C:/Dev-Cpp/include/c++/3.4.2/mingw32"  -I"C:/Dev-Cpp/include/c++/3.4.2"  -I"C:/Dev-Cpp/include" 

+BIN  = MarkSort.exe

+CXXFLAGS = $(CXXINCS)  

+CFLAGS = $(INCS)  

+RM = rm -f

+

+.PHONY: all all-before all-after clean clean-custom

+

+all: all-before MarkSort.exe all-after

+

+

+clean: clean-custom

+  ${RM} $(OBJ) $(BIN)

+

+$(BIN): $(OBJ)

+  $(CPP) $(LINKOBJ) -o "MarkSort.exe" $(LIBS)

+

+main.o: main.cpp

+  $(CPP) -c main.cpp -o main.o $(CXXFLAGS)

59  MarkSort/MarkSort.dev
... 	... 	

@@ -0,0 +1,59 @@

  	1 	

+[Project]

  	2 	

+FileName=MarkSort.dev

  	3 	

+Name=MarkSort

  	4 	

+UnitCount=1

  	5 	

+Type=1

  	6 	

+Ver=1

  	7 	

+ObjFiles=

  	8 	

+Includes=

  	9 	

+Libs=

  	10 	

+PrivateResource=

  	11 	

+ResourceIncludes=

  	12 	

+MakeIncludes=

  	13 	

+Compiler=

  	14 	

+CppCompiler=

  	15 	

+Linker=

  	16 	

+IsCpp=1

  	17 	

+Icon=

  	18 	

+ExeOutput=

  	19 	

+ObjectOutput=

  	20 	

+OverrideOutput=0

  	21 	

+OverrideOutputName=

  	22 	

+HostApplication=

  	23 	

+Folders=

  	24 	

+CommandLine=

  	25 	

+UseCustomMakefile=0

  	26 	

+CustomMakefile=

  	27 	

+IncludeVersionInfo=0

  	28 	

+SupportXPThemes=0

  	29 	

+CompilerSet=0

  	30 	

+CompilerSettings=

  	31 	

+

  	32 	

+[Unit1]

  	33 	

+FileName=main.cpp

  	34 	

+CompileCpp=1

  	35 	

+Folder=

  	36 	

+Compile=1

  	37 	

+Link=1

  	38 	

+Priority=1000

  	39 	

+OverrideBuildCmd=0

  	40 	

+BuildCmd=

  	41 	

+

  	42 	

+[VersionInfo]

  	43 	

+Major=0

  	44 	

+Minor=1

  	45 	

+Release=1

  	46 	

+Build=1

  	47 	

+LanguageID=1033

  	48 	

+CharsetID=1252

  	49 	

+CompanyName=

  	50 	

+FileVersion=

  	51 	

+FileDescription=Developed using the Dev-C++ IDE

  	52 	

+InternalName=

  	53 	

+LegalCopyright=

  	54 	

+LegalTrademarks=

  	55 	

+OriginalFilename=

  	56 	

+ProductName=

  	57 	

+ProductVersion=

  	58 	

+AutoIncBuildNr=0

  	59 	

+

99  MarkSort/main.cpp
... 	... 	

@@ -0,0 +1,99 @@

  	1 	

+/*

  	2 	

+  Joseph Reimbold

  	3 	

+  11/19/2013

  	4 	

+  Sorting Functions

  	5 	

+*/

  	6 	

+

  	7 	

+//Libraries

  	8 	

+#include <cstdlib>

  	9 	

+#include <iostream>

  	10 	

+#include <ctime>

  	11 	

+using namespace std;

  	12 	

+

  	13 	

+//Global Constants

  	14 	

+

  	15 	

+//Function Prototypes

  	16 	

+void filArry(int [],int);

  	17 	

+void prntAry(int [],int,int);

  	18 	

+void swap1(int &,int &);

  	19 	

+void swap2(int &,int &);

  	20 	

+void swap3(int [],int,int);

  	21 	

+void copy(int [],int [],int);

  	22 	

+void sortPos(int [],int,int);

  	23 	

+void markSort(int [],int);

  	24 	

+

  	25 	

+//Execution Begins Here

  	26 	

+int main(int argc, char *argv[])

  	27 	

+{

  	28 	

+    //Declare Variables and initialize the

  	29 	

+    //random number seed

  	30 	

+    const int SIZE=100;

  	31 	

+    int array[SIZE],aCopy[SIZE];

  	32 	

+    srand(static_cast<unsigned int>(time(0)));

  	33 	

+    

  	34 	

+    //Fill the Array

  	35 	

+    filArry(array,SIZE);

  	36 	

+    

  	37 	

+    //Print Array

  	38 	

+    prntAry(array,SIZE,10);

  	39 	

+    

  	40 	

+    //Sort the array

  	41 	

+    markSort(array,SIZE);

  	42 	

+    

  	43 	

+    //Print the Sorted Array

  	44 	

+    prntAry(array,SIZE,10);

  	45 	

+    

  	46 	

+    //Exit Stage Right

  	47 	

+    system("PAUSE");

  	48 	

+    return EXIT_SUCCESS;

  	49 	

+}

  	50 	

+void markSort(int a[],int n){

  	51 	

+     for(int i=0;i<n-1;i++){

  	52 	

+             sortPos(a,n,i);

  	53 	

+     }

  	54 	

+}

  	55 	

+

  	56 	

+void sortPos(int a[],int n,int pos){

  	57 	

+     if(pos>n-1)return;

  	58 	

+     for(int i=pos+1;i<n;i++){

  	59 	

+             if(a[pos]>a[i])swap3(a,pos,i);

  	60 	

+     }

  	61 	

+}

  	62 	

+

  	63 	

+void copy(int a[],int b[],int n){

  	64 	

+     for(int i=0;i<n;i++){

  	65 	

+             b[i]=a[i];

  	66 	

+     }

  	67 	

+}

  	68 	

+

  	69 	

+void swap3(int a[],int pos1,int pos2){

  	70 	

+     int temp=a[pos1];

  	71 	

+     a[pos1]=a[pos2];

  	72 	

+     a[pos2]=temp;

  	73 	

+}

  	74 	

+

  	75 	

+void swap2(int &a,int &b){

  	76 	

+     a=a^b;

  	77 	

+     b=a^b;

  	78 	

+     a=a^b;

  	79 	

+}

  	80 	

+

  	81 	

+void swap1(int &a,int &b){

  	82 	

+     int temp=a;

  	83 	

+     a=b;

  	84 	

+     b=temp;

  	85 	

+}

  	86 	

+

  	87 	

+void prntAry(int a[],int n,int perLine){

  	88 	

+     for(int i=0;i<n;i++){

  	89 	

+             cout<<a[i]<<" ";

  	90 	

+             if(i%perLine==(perLine-1))cout<<endl;

  	91 	

+     }

  	92 	

+     cout<<endl;

  	93 	

+}

  	94 	

+

  	95 	

+void filArry(int a[],int n){

  	96 	

+     for(int i=0;i<n;i++){

  	97 	

+             a[i]=rand()%900+100;

  	98 	

+     }

  	99 	

+}
