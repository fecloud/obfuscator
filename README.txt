Low Level Virtual Machine (LLVM)
================================

This directory and its subdirectories contain source code for LLVM,
a toolkit for the construction of highly optimized compilers,
optimizers, and runtime environments.

LLVM is open source software. You may freely distribute it under the terms of
the license agreement found in LICENSE.txt.

Please see the documentation provided in docs/ for further
assistance with LLVM, and in particular docs/GettingStarted.rst for getting
started with LLVM and docs/README.txt for an overview of LLVM's
documentation setup.

If you are writing a package for LLVM, see docs/Packaging.rst for our
suggestions.


win7 mingw complie modify

CryptoUtils.cpp

#include <time.h>
void tritium_init_rand_key(char * buf,unsigned int buflen) {
    unsigned int i;
    srand(time(NULL));
    for (i = 0; i < buflen; i++) {
        buf[i] = char(rand() & 0xFF);
    }
}
 
#define __tritium__

bool CryptoUtils::prng_seed() {
#ifdef __tritium__
    //LLVMContext &ctx = llvm::getGlobalContext();
    tritium_init_rand_key(key, 16);
    DEBUG_WITH_TYPE("cryptoutils", dbgs() << "cryptoutils seeded with time srand and rand\n");
    memset(ctr, 0, 16);
    // Once the seed is there, we compute the
    // AES128 key-schedule
    aes_compute_ks(ks, key);
    seeded = true;
#else



std::string getClangToolFullVersion(StringRef ToolName) {
  std::string buf;
  llvm::raw_string_ostream OS(buf);
//#ifdef CLANG_VENDOR
//  OS << CLANG_VENDOR;
//#endif
//  OS << ToolName << " version " CLANG_VERSION_STRING " "
//     << getClangFullRepositoryVersion();

  // If vendor supplied, include the base LLVM version as well.
//#ifdef CLANG_VENDOR
//  OS << " (based on " << BACKEND_PACKAGE_STRING << ")";
//#endif
	OS << "Copyright (C) 2006 The Android Open Source Project";
  return OS.str();
}
