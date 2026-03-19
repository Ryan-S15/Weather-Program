#include <iostream>
#include <cmath>
using namespace std;

// Function prototypes
void programIntro(); // Function used to display my program intro 

void getInput(double &temperature, double &windSpeed, double &dewPoint); // Function used to gather temp, wind speed, and dew point input from the user. 

void calculateValues(double &temperature, double &windSpeed, double &dewPoint, // function used to claculate the wind chill and cloud base
                     double &windChill, double &cloudBase);
                     
void displayOutput(double &windChill, double &cloudBase); // function used to display the cloud base and wind chill to the user

int main() {
    double &temperature, &windSpeed, &dewPoint; // declartions of all variables used in code
    double &windChill, &cloudBase;

    programIntro(); // text box intro to my program

    getInput(temperature, windSpeed, dewPoint); // gets temperature, windspeed, and dew point and stores them for calculations

    calculateValues(temperature, windSpeed, dewPoint, windChill, cloudBase); // Calculates windchill and cloud base using stored variables from earlier

    displayOutput(windChill, cloudBase); // displays the final cloud base and wind chill from the calculations

    return 0;
}

// Function definitions

// Text used to describe what the program does and what the user will be doing
void programIntro() {
    cout << "Weather Calculator Program\n";
    cout << "This program calculates wind chill and estimated cloud base.\n";  
    cout << "You will enter temperature, wind speed, and dew point.\n\n";
}

void getInput(double &temperature, double &windSpeed, double &dewPoint) {

    while (true) {
        cout << "Enter temperature (F): "; // gets temperature input from user
        cin >> temperature;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n"; //checks for invalid anwsers 
            cin.clear();
            cin.ignore(1000, '\n');
        } else {
            break;
        }
    }

    while (true) {
        cout << "Enter wind speed (mph): "; // gets input for wind speed from user
        cin >> windSpeed;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n"; //checks for invalid anwsers 
            cin.clear();
            cin.ignore(1000, '\n');
        } else {
            break;
        }
    }

    while (true) {
        cout << "Enter dew point (F): "; // gets dew point input from user
        cin >> dewPoint;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n"; //checks for invalid anwsers 
            cin.clear();
            cin.ignore(1000, '\n');
        } else {
            break;
        }
    }
}

void calculateValues(double &temperature, double &windSpeed, double &dewPoint, // proper calculations for wind chill and cloud basse
                     double &windChill, double &cloudBase) {

    windChill = 35.74 + (0.6215 * temperature)
              - (35.75 * pow(windSpeed, 0.16))
              + (0.4275 * temperature * pow(windSpeed, 0.16));

    cloudBase = ((temperature - dewPoint) / 4.4) * 1000;
}

void displayOutput(double &windChill, double &cloudBase) { // Displays the final wind chill and cloud base to the user

    cout << "\nResults:\n";
    cout << "Wind Chill: " << windChill << " F" << endl;
    cout << "Estimated Cloud Base: " << cloudBase << " feet" << endl;
}
