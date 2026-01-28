# Control-Flow-Obfuscator
The Control-Flow-Obfuscator is a header-only obfuscation library for C/C++ that provides compile-time code protection. <br />
It enables control flow flattening, string encryption, call hiding, and anti-reverse engineering features. <br />
Can be used both in usermode and Windows kernel drivers with all compiler compatibility. <br />

# Configuration
Configure obfuscation intensity in the header:
```cpp
#define CONST_ENCRYPTION       1    // Enable string encryption (C++)
#define CFLOW_BRANCHING        1    // Control flow obfuscation
#define INDIRECT_BRANCHING     1    // Break decompilers
#define FAKE_SIGNATURES        1    // PE signature spoofing
#define KERNEL_MODE            1    // Kernel-safe mode
```

**Basic Setup**
```cpp
#define MY_PROJECT_ROOT  // Enables obfuscation
#include "obfusheader.h"

int entry_point() {
    // Fake signatures applied when FAKE_SIGNATURES=1
    // Your code here
    return 0;
}
```

**Bogus Code Injection (Kernel)**
```cpp
OBFUSCATE_BEGIN
    // Your code
OBFUSCATE_END
```

# Obfuscation Features
**Core Protection Methods**
- Control Flow Protection - Branching obfuscation with compile-time randomization
- Indirect Branching - Breaks IDA/Ghidra decompilers with invalid opcodes
- Loop Obfuscation - for/while/return statement junk code injection
- Call Hiding - Function pointer shuffling with decoy arrays
- String Encryption - Compile-time XOR encryption (C++ only)
- Constant Encryption - Normal & Thread-local decryption modes
- Volatile Storage - Essential bytes stored in static memory

**Anti-Reverse Engineering**
- Fake PE Signatures - Mimics Denuvo, VMProtect, Themida, Enigma, SecuROM
- Binary Watermarking - Embeds messages visible in IDA/Ghidra output
- Segfault Triggers - Intentional crashes on tampering detection
- Decoy Functions - Fake function arrays for call masking
