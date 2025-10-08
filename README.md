#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>
using namespace std;

// Function to convert Decimal to Binary
string decimalToBinary(int decimal) {
    if (decimal == 0) return "0";
    string binary = "";
    while (decimal > 0) {
        binary = to_string(decimal % 2) + binary;
        decimal /= 2;
    }
    return binary;
}

// Function to convert Binary to Decimal
int binaryToDecimal(string binary) {
    int decimal = 0;
    for (int i = 0; i < binary.length(); i++) {
        if (binary[i] == '1') {
            decimal += pow(2, binary.length() - 1 - i);
        } else if (binary[i] != '0') {
            cout << "Invalid binary input!" << endl;
            return -1;
        }
    }
    return decimal;
}

// Function to convert Decimal to Hexadecimal
string decimalToHexadecimal(int decimal) {
    if (decimal == 0) return "0";
    string hex = "";
    while (decimal > 0) {
        int remainder = decimal % 16;
        hex = (remainder < 10 ? (char)(remainder + '0') : (char)(remainder - 10 + 'A')) + hex;
        decimal /= 16;
    }
    return hex;
}

// Function to convert Hexadecimal to Decimal
int hexadecimalToDecimal(string hex) {
    int decimal = 0;
    for (int i = 0; i < hex.length(); i++) {
        char c = toupper(hex[i]);
        if (c >= '0' && c <= '9') {
            decimal = decimal * 16 + (c - '0');
        } else if (c >= 'A' && c <= 'F') {
            decimal = decimal * 16 + (c - 'A' + 10);
        } else {
            cout << "Invalid hexadecimal input!" << endl;
            return -1;
        }
    }
    return decimal;
}

int main() {
    srand(time(0)); // Seed for random number generation
    int choice;
    while (true) {
        cout << "\nConversion Menu:" << endl;
        cout << "1. Convert Decimal to Binary" << endl;
        cout << "2. Convert Binary to Decimal" << endl;
        cout << "3. Convert Hexadecimal to Decimal" << endl;
        cout << "4. Convert Decimal to Hexadecimal" << endl;
        cout << "5. Demo (Generate and convert random integers to binary)" << endl;
        cout << "6. Exit" << endl;
        cout << "Enter your choice (1-6): ";
        cin >> choice;

        if (choice == 1) {
            int decimal;
            cout << "Enter a decimal number: ";
            cin >> decimal;
            cout << "Binary representation: " << decimalToBinary(decimal) << endl;
        }
        else if (choice == 2) {
            string binary;
            cout << "Enter a binary number: ";
            cin >> binary;
            int result = binaryToDecimal(binary);
            if (result != -1) cout << "Decimal representation: " << result << endl;
        }
        else if (choice == 3) {
            string hex;
            cout << "Enter a hexadecimal number: ";
            cin >> hex;
            int result = hexadecimalToDecimal(hex);
            if (result != -1) cout << "Decimal representation: " << result << endl;
        }
        else if (choice == 4) {
            int decimal;
            cout << "Enter a decimal number: ";
            cin >> decimal;
            cout << "Hexadecimal representation: " << decimalToHexadecimal(decimal) << endl;
        }
        else if (choice == 5) {
            int randomNum = rand() % 100; // Random number between 0 and 99
            string binary = decimalToBinary(randomNum);
            cout << "Generated random integer: " << randomNum << endl;
            cout << "Binary representation: " << binary << endl;
        }
        else if (choice == 6) {
            cout << "Exiting the program..." << endl;
            break;
        }
        else {
            cout << "Invalid choice! Please enter a number between 1 and 6." << endl;
        }
    }
    return 0;
}# isat-subtask2
