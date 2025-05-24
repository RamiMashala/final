#include <iostream>
#include <cmath> 
#include <string>
#include <random>
#include <ctime>
#include <algorithm>
using namespace std;
// Global variables
string num_answer;

// Function prototypes
void Geometry();
void Equation();
void Calculations();
void entername();
void welcome();
void exit();
void pointincrease(int &score);
void pointdecrease(int &score);
void finalmessage(int score);
void instructions();

// Main function
int main() {
	srand(time(0));
	welcome();
	int mode;
	cin >> mode;
	if (mode < 1 || mode > 3) {
		cout << endl << "Invalid game mode. Please enter a valid game mode : ";
		cin >> mode;
	}
	switch (mode) {
			case 1: {
				Calculations();
				break;
			}
			case 2: {
				Equation();
				break;
			}
			case 3: {
				Geometry();
				break;
			}
	}
	return 0;
}
// Function definitions
void exit() {
	if (num_answer == "exit" || num_answer == "Exit" || num_answer == "EXIT") {
		cout << "Thanks for playing!" << endl;
		return;
	}
}
void welcome() {
	cout << "Welcome to the Math Quiz Game!" << endl;
	cout << "You will be asked math questions." << endl;
	cout << "there will be a multiple of difficulty levels." << endl;
	cout << "Harder questions will give you more points." << endl;
	cout << "You can type (exit / Exit / EXIT) to quit the game at any time." << endl;
	cout << endl << "+ = addition" << endl;
	cout << "- = subtraction" << endl;
	cout << "* = multiplication" << endl;
	cout << "/ = division" << endl;
	cout << "^ = power" << endl;
	cout << endl << "consider pi = 3" << endl;
	cout << "Let's start!" << endl;
	entername();
	cout << "choose the game mode:" << endl;
	cout << "1. Calculations\n2.Equations\n3.Geometry" << endl;
}
void entername() {
	cout << endl << "Please enter your name: ";
	string name;
	cin >> name;
	cout << endl << "Hello " << name << "!" << endl;
}
void Calculations() {
	int difficulty, score = 0;
	cout << "You will be asked multiple questions." << endl;
	cout << endl << "choose the difficulty level (1-3):" << endl;
	cout << "1. Easy" << endl;
	cout << "2. Medium" << endl;
	cout << "3. Hard" << endl;
diff:
	cin >> difficulty;
	if (difficulty < 1 || difficulty > 3) {
		cout << endl << "Invalid difficulty level. Please enter a valid difficulty level : ";
		goto diff;
	}
	switch (difficulty) {
	case 1: {
		int num1, num2;
		char operation;
		cout << endl << "You have chosen Easy difficulty." << endl;
		instructions();
		cout << "The questions will be in the form of addition / subtraction" << endl;
		while (score >= 0 && score < 10) {
			num1 = rand() % 100 + 1;
			num2 = rand() % 100 + 1;
			operation = rand() % 2 + 1;
			if (operation == 1) {
				cout << "What is " << num1 << "+" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == num1 + num2) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << num1 + num2 << ".\n";
					pointdecrease(score);
				}
			}
			else if (operation == 2) {
				if (num1 < num2) {
					swap(num1, num2);
				}
				cout << "What is " << num1 << "-" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == num1 - num2) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << num1 - num2 << ".\n";
					pointdecrease(score);
				}
			}
		}
		finalmessage(score);
	}
	case 2: {
		int num1, num2;
		char operation;
		cout << "You have chosen Medium difficulty." << endl;
		instructions();
		cout << "The questions will be in the form of addition / subtraction / multiplication" << endl;
		while (score >= 0 && score < 10) {
			num1 = rand() % 1000 + 1;
			num2 = rand() % 1000 + 1;
			operation = rand() % 3 + 1;
			if (operation == 1) {
				cout << "What is " << num1 << "+" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == num1 + num2) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << num1 + num2 << ".\n";
					pointdecrease(score);
				}
			}
			else if (operation == 2) {
				if (num1 < num2) {
					swap(num1, num2);
				}
				cout << "What is " << num1 << "-" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == num1 - num2) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << num1 - num2 << ".\n";
					pointdecrease(score);
				}
			}
			else if (operation == 3) {
				if (num2 > 10) {
					num2 = num2 % 10;
				}
				cout << "What is " << num1 << "x" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == num1 * num2) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << num1 * num2 << ".\n";
					pointdecrease(score);
				}
			}
		}
		finalmessage(score);
	}
	case 3: {
		int num1, num2;
		char operation;
		cout << "You have chosen Hard difficulty." << endl;
		instructions();
		cout << "The questions will be in the form of multiplication / power" << endl;
		while (score >= 0 && score < 10) {
			num1 = rand() % 100 + 1;
			num2 = rand() % 100 + 1;
			operation = rand() % 2 + 1;
			if (operation == 1) {
				cout << "What is " << num1 << "x" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == num1 * num2) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << num1 * num2 << ".\n";
					pointdecrease(score);
				}
			}
			else if (operation == 2) {
				num1 = num1 % 10;
				num2 = num2 % 5;
				if (num2 == 0) {
					num2 = 2;
				}
				cout << "What is " << num1 << "^" << num2 << "? ";
				cin >> num_answer;
				exit();
				int answer = stoi(num_answer);
				if (answer == pow(num1, num2)) {
					pointincrease(score);
				}
				else {
					cout << "Wrong. The correct answer is " << pow(num1, num2) << ".\n";
					pointdecrease(score);
				}
			}
		}
		finalmessage(score);
	} 
	}
}
void Equation() {
	int score = 0;
	cout << "You have choosen Equations mode." << endl;
	instructions();
	cout << "The equations will be in the form of (Ax + B = 0)" << endl;
	while (score >= 0 && score < 10) {
		int A = rand() % 10 + 1;
		int B = rand() % 10 + 1;
		if (rand() % 2 == 0) {
			B = -B;
		}
		if (rand() % 2 == 0) {
			A = -A;
		}
		if (A == 0) {
			A = 1;
		}
		if (B == 0) {
			B = 1;
		}
		if (A % B != 0) {
			A = A * B;
		}
		if (B % A != 0) {
			B = B * A;
		}
		int x = -B / A;
		cout << "What is the value of x in the equation " << A << "x + " << B << " = 0 ? ";
		cin >> num_answer;
		exit();
		int answer = stoi(num_answer);
		if (answer == x) {
			pointincrease(score);
		}
		else {
			cout << "Wrong. The correct answer is " << x << ".\n";
			pointdecrease(score);
		}
	}
	finalmessage(score);
}
void Geometry() {
	int score = 0;
	cout << "You have choosen Equations mode." << endl;
	instructions();
	cout << "The equations will be in the form of (Ax + B = 0)" << endl;
	while (score >= 0 && score < 10) {
		int nu1 = rand() % 10 + 1;
		int nu2 = rand() % 10 + 1;
		int nu3 = rand() % 10 + 1;
		int shape = rand() % 7 + 1;
		if (shape == 1) {
			cout << "What is the area of a square with side length " << nu1 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == nu1 * nu1) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << nu1 * nu1 << ".\n";
				pointdecrease(score);
			}
		}
		if (shape == 2) {
			cout << "What is the area of a rectangle with length " << nu1 << " and width " << nu2 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == nu1 * nu2) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << nu1 * nu2 << ".\n";
				pointdecrease(score);
			}
		}
		if (shape == 3) {
			cout << "What is the area of a triangle with base " << nu1 << " and height " << nu2 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == (nu1 * nu2) / 2) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << (nu1 * nu2) / 2 << ".\n";
				pointdecrease(score);
			}
		}
		if (shape == 4) {
			cout << "What is the volume of a cube with side length " << nu1 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == nu1 * nu1 * nu1) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << nu1 * nu1 * nu1 << ".\n";
				pointdecrease(score);
			}
		}
		if (shape == 5) {
			cout << "What is the volume of a rectangular prism with length " << nu1 << ", width " << nu2 << " and height " << nu3 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == nu1 * nu2 * nu3) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << nu1 * nu2 * nu3 << ".\n";
				pointdecrease(score);
			}
		}
		if (shape == 6) {
			cout << "What is the circumference of a circle with radius " << nu1 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == 2 * 3 * nu1) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << 2 * 3 * nu1 << ".\n";
				pointdecrease(score);
			}
		}
		if (shape == 7) {
			cout << "What is the area of a circle with radius " << nu1 << "? ";
			cin >> num_answer;
			exit();
			int answer = stoi(num_answer);
			if (answer == 3 * nu1 * nu1) {
				pointincrease(score);
			}
			else {
				cout << "Wrong. The correct answer is " << 3 * nu1 * nu1 << ".\n";
				pointdecrease(score);
			}
		}
	}
	finalmessage(score);
}
void pointincrease(int &score) {
	cout << "Correct!\n";
	cout << "You have earned 1 point.\n";
	score += 1;
	cout << "Your total score is " << score << ".\n";
}
void pointdecrease(int &score) {
	cout << "You have lost 1 point.\n";
	if (score > 0) {
		score -= 1;
	}
	else {
		score = 0;
	}
	cout << "Your total score is " << score << ".\n";
}
void finalmessage(int score){
	cout << "Congratulations! You have completed the game!" << endl;
	cout << "Your final score is " << score << "." << endl;
	cout << "Thanks for playing!" << endl;
}
void instructions() {
	cout << "You will be asked multiple questions." << endl;
	cout << "You will earn 1 point for each correct answer." << endl;
	cout << "You will lose 1 point for each wrong answer." << endl;
}
