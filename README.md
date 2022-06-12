# Alacrity
A functional programming language designed to control the C/C++ software compilation process.

## Demo
```
def major: Int = 2;
def minor = 1; // auto inference

def enable_gpu: Option = ("use gpu to calculate",
        if (os.current == "Windows") true else false);
def buffer_size: Macro = 512; // BUFFER_SIZE

if (enable_gpu) {
    print("enable gpu");
    def GPU_ENABLE = Void; // It is a macro.
}

def filelist: List[Path] = list(@"./") :: compress.filelist;

def compiler: Compiler = new Compiler(@"compiler path here");

lazy def compress_program: Executable =
    compile[Executable](compiler, filelist);

def getDependency(name: String, url: String): SLib = {
    def lib = find(name);
    if (lib != null) lib else os.current match {
        case "Windows": curl(url);
        case _: error("not supported yet");
    } as SLib;
}

def res = link(compress_program, GetDependency("SomeLib", "http://foo.bar));
execute(res);
```

## Types
- Void
- Object
- Int <: Object
- String <: Object
- Boolean <: Object
- Macro <: Object
- List[T] <: Object
- Map[T1, T2] <: Object
- Binary <: Object
- Record <: Object
- (arg) => ret <: Object
- Path <: String
- Option <: Boolean
- Executable <: Binary
- SLib <: Binary
- DLib <: Binary
- Compiler <: Executable