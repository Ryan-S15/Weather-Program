#include <iostream>
#include <cmath>
using namespace std;

// Function prototypes
void programIntro();
void getInput(double &temperature, double &windSpeed, double &dewPoint);
void calculateValues(double temperature, double windSpeed, double dewPoint,
                     double &windChill, double &cloudBase);
void displayOutput(double windChill, double cloudBase);

int main() {
    double temperature, windSpeed, dewPoint;
    double windChill, cloudBase;

    programIntro();

    getInput(temperature, windSpeed, dewPoint);

    calculateValues(temperature, windSpeed, dewPoint, windChill, cloudBase);

    displayOutput(windChill, cloudBase);

    return 0;
}

// Function definitions

void programIntro() {
    cout << "Weather Calculator Program\n";
    cout << "This program calculates wind chill and estimated cloud base.\n";
    cout << "You will enter temperature, wind speed, and dew point.\n\n";
}

void getInput(double &temperature, double &windSpeed, double &dewPoint) {

    while (true) {
        cout << "Enter temperature (F): ";
        cin >> temperature;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n";
            cin.clear();
            cin.ignore(1000, '\n');
        } else {
            break;
        }
    }

    while (true) {
        cout << "Enter wind speed (mph): ";
        cin >> windSpeed;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n";
            cin.clear();
            cin.ignore(1000, '\n');
        } else {
            break;
        }
    }

    while (true) {
        cout << "Enter dew point (F): ";
        cin >> dewPoint;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n";
            cin.clear();
            cin.ignore(1000, '\n');
        } else {
            break;
        }
    }
}

void calculateValues(double temperature, double windSpeed, double dewPoint,
                     double &windChill, double &cloudBase) {

    windChill = 35.74 + (0.6215 * temperature)
              - (35.75 * pow(windSpeed, 0.16))
              + (0.4275 * temperature * pow(windSpeed, 0.16));

    cloudBase = ((temperature - dewPoint) / 4.4) * 1000;
}

void displayOutput(double windChill, double cloudBase) {

    cout << "\nResults:\n";
    cout << "Wind Chill: " << windChill << " F" << endl;
    cout << "Estimated Cloud Base: " << cloudBase << " feet" << endl;
}
