#include <iostream>
#include <unordered_map>
#include <cctype>
#include <string>

using namespace std;

// Morse code dictionary
unordered_map<char, string> morseCode = {
    {'A', ".-"}, {'B', "-..."}, {'C', "-.-."}, {'D', "-.."}, {'E', "."},
    {'F', "..-."}, {'G', "--."}, {'H', "...."}, {'I', ".."}, {'J', ".---"},
    {'K', "-.-"}, {'L', ".-.."}, {'M', "--"}, {'N', "-."}, {'O', "---"},
    {'P', ".--."}, {'Q', "--.-"}, {'R', ".-."}, {'S', "..."}, {'T', "-"},
    {'U', "..-"}, {'V', "...-"}, {'W', ".--"}, {'X', "-..-"}, {'Y', "-.--"},
    {'Z', "--.."}, {'0', "-----"}, {'1', ".----"}, {'2', "..---"}, {'3', "...--"},
    {'4', "....-"}, {'5', "....."}, {'6', "-...."}, {'7', "--..."}, {'8', "---.."},
    {'9', "----."}, {' ', "/"}, {'.', ".-.-.-"}, {',', "--..--"}, {'?', "..--.."},
    {'\'', ".----."}, {'!', "-.-.--"}, {'/', "-..-."}, {'(', "-.--."}, {')', "-.--.-"},
    {'&', ".-..."}, {':', "---..."}, {';', "-.-.-."}, {'=', "-...-"}, {'+', ".-.-."},
    {'-', "-....-"}, {'_', "..--.-"}, {'"', ".-..-."}, {'$', "...-..-"}, {'@', ".--.-."}
};

char dot = 46;    // ASCII 46 for dot
char dash = 45;   // ASCII 45 for dash

string textToMorse(const string& text) {
    string morse;
    for (char c : text) {
        char upperC = toupper(c);
        if (morseCode.find(upperC) != morseCode.end()) {
            for (char mc : morseCode[upperC]) {
                morse += (mc == '.') ? dot : dash;
            }
            morse += ' '; // Space between letters
        }
    }
    return morse;
}

int main() {
    string input;
    
    cout << "Enter a message to translate to Morse code: ";
    getline(cin, input);
    
    string morse = textToMorse(input);
    
    cout << "\nMorse Code:\n" << morse << endl;
    
    return 0;
}
