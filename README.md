# include<stdio.h>
# include<stdlib.h>
# include<time.h>
# include<iostream>
using namespace std;

int main() {
	bool isSame = false;
	const int length = 4;
	int a = 0, b = 0, guessNumber, countLength = 0;
	int com[length] = {10, 10, 10, 10}, guess[length];
	srand(time(NULL));
	while (countLength <= 3) {
		com[countLength] = rand()%10;
		for (int i = 0; i < 4; i++) {
			if (countLength == i) { continue; }
			if (com[countLength] == com[i]) {
				isSame = true;
				break;
			}
		}
		if (isSame) { isSame = false;  continue; }
		else { isSame = false;  countLength++; }
	}
	cout << com[0] << com[1] << com[2] << com[3] << endl;
	cout << "Please enter a number between 0000 ~ 9999, need to be four different digits: " << endl;
	while (true) {
		cin >> guessNumber;
		if (guessNumber <= 1000 || guessNumber >= 10000) { 
			cout << "Please enter a number between 0000 ~ 9999. Try it again" << endl;
			continue; 
		}
		guess[0] = guessNumber / 1000;
		guess[1] = (guessNumber / 100) % 10;
		guess[2] = (guessNumber / 10) % 10;
		guess[3] = guessNumber % 10;
		for (int i = 0; i <= 3; i++) {
			for (int j = 0; j <= 3; j++) {
				if (com[i] == guess[j]) {
					if (i == j) { a++; break; }
					else { b++; break; }
				}
				else {}
			}
		}
		cout << "It is " << a << "A" << b << "B. ";
		if (a == 4) {
			cout << "Well done!" << endl;
			break;
		}
		else {
			cout << "Please guess again!" << endl;
		}
		a = 0;
		b = 0;
	}
	system("pause");
	return 0;
}
