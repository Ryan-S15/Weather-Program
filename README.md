#include <iostream>
#include <cmath>
#include <limits>
using namespace std;

// Function prototypes (declarations)
double calculateWindChill(double temp, double windSpeed);
double calculateCloudBase(double temp, double dewPoint);

int main() {
    double temperature, windSpeed, dewPoint;

    // Temperature input
    while (true) {
        cout << "Enter temperature (F): ";
        cin >> temperature;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
        } else {
            break;
        }
    }

    // Wind speed input
    while (true) {
        cout << "Enter wind speed (mph): ";
        cin >> windSpeed;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
        } else {
            break;
        }
    }

    // Dew point input
    while (true) {
        cout << "Enter dew point (F): ";
        cin >> dewPoint;

        if (cin.fail()) {
            cout << "Invalid input. Please enter a number.\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
        } else {
            break;
        }
    }

    double windChill = calculateWindChill(temperature, windSpeed);
    double cloudBase = calculateCloudBase(temperature, dewPoint);

    cout << "\nWind Chill: " << windChill << " F" << endl;
    cout << "Estimated Cloud Base: " << cloudBase << " feet" << endl;

    return 0;
}

// Function definitions

double calculateWindChill(double temp, double windSpeed) {
    return 35.74 + (0.6215 * temp) - (35.75 * pow(windSpeed, 0.16))
           + (0.4275 * temp * pow(windSpeed, 0.16));
}

double calculateCloudBase(double temp, double dewPoint) {
    return ((temp - dewPoint) / 4.4) * 1000;
}
