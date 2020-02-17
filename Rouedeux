/*
Rouedeux Esoteric Language
By Matthew S.
*/

#include <iostream>
#include <string>
#include <vector>
using namespace std;

const char roue[27] = { ' ', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z' };
int roueptr = 0;
vector<char> tape;
int tapelength = 0;
int tapeptr = 0;

string program = " ";

vector<char> lexical;

void lexicalanalysis(string ex) { // parses through input and determines if it consists of eligible characters. It then puts these in the variable 'lexical'.
	int length = ex.size();
	int i, x;
	char regex[9] = { 'E', 'T', 'P', 'W', 'R', 'O', 'Q', 'I', 'S' };
	for (i = 0; i < length; i++) {
		char currentchar = ex[i];
		bool found = false;
		if (currentchar == (' ')) {
			found = true;
			continue;
		}
		else {
			for (x = 0; x < sizeof(regex); x++) {

				if (currentchar == regex[x]) {
					lexical.push_back(currentchar);
					found = true;
				}
			}
		}
		if (!found) {
			cout << "The character at " << i + 1 << " is not an eligible character. Now exiting program." << endl;
			exit(0);
		}
	}
}

void execute(vector<char> lex) {
	int length, i;
	int loopcount = 0;
	for (i = 0; i < lex.size(); i++) {
		switch (lex[i]) {
		case 'R': {//moves wheel to the right
			if (roueptr != 26) {
				roueptr++;
			}
			else {
				roueptr = 0;
			}
		}
				break;
		case 'T': // moves the tape to the right 
			if (tapeptr != tapelength) {
				tapeptr++;
			}
			else {
				tapeptr = 0;
			}
			break;
		case 'E': // expands the tape by one
			tapelength++;
			tape.push_back(' ');
			break;
		case 'W': // current wheel letter written into current tape cell 
			tape[tapeptr] = roue[roueptr];
			break;
		case 'P': // prints letter in current cell
			cout << tape[tapeptr];
			break;
		case 'O': // beginning of loop
			if (roue[roueptr] == ' ') {
				int loop = 1;
				while (loop > 0) {
					i++;
					if (lex[i] == 'Q') {
						loop--;
					}
					if (lex[i] == 'O') {
						loop++;
					}
				}
			}
			break;
		case 'Q': // loops
			if (roue[roueptr] != ' ') {
				int loop = 1;
				while (loop > 0) {
					i--;
					if (lex[i] == 'Q') {
						loop++;
					}
					if (lex[i] == 'O') {
						loop--;
					}
				}
			}
			break;
		case 'I':
			char g;
			cin >> g;
			if (g != ' ' && g != 'A' && g != 'B' && g != 'C' && g != 'D' && g != 'E' && g != 'F' 
				&& g != 'G' && g != 'H' && g != 'I' && g != 'J' && g != 'K' && g != 'L' && g != 'M'
				&& g != 'N' && g != 'O' && g != 'P' && g != 'Q' && g != 'R' && g != 'S' && g != 'T'
				&& g != 'U' && g != 'V' && g != 'W' && g != 'X' && g != 'Y' && g != 'Z') {
				cout << "The input is invalid. Now exiting program.";
				exit(0);
			}
			else {
				tape[tapeptr] = g;
			}
			break;
		case 'S': {
			bool set = false;
			int counter = 0;
			while (!set) {
				if (tape[tapeptr] == roue[counter]) {
					roueptr = counter;
					set = true;
				}
				else {
					counter++;
				}
			}
		}
			break;
		default: {
			cout << "Something went wrong in the program at character " << i << ". Now terminating program." << endl;
			exit(0);
			}
		}
	}
}

int main() {
	tape.push_back(' '); // The tape starts with one cell.
	
	cout << "Rouedeux Interpreter" << endl << "Input your program: ";
	
	cin >> program;
	cout << "\n";
	
	lexicalanalysis(program);
	execute(lexical);

	cout << "\n\nProgram executed successfully." << endl;

	return 0;
}
