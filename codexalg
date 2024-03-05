#include <iostream>
#include <vector>
#include <iomanip>
#include <cmath>
using namespace std;

const double EPSILON = 1e-10;

int main() {
    int numberOfTestCases;
    cin >> numberOfTestCases;

    while (numberOfTestCases--) {
        int numberOfEquations;
        cin >> numberOfEquations;

        vector<vector<double>> coefficients(numberOfEquations, vector<double>());
        for (int i = 0; i < numberOfEquations; ++i) {
            int numberOfCoefficients;
            cin >> numberOfCoefficients;

            vector<double> equationCoefficients(numberOfCoefficients);
            for (int j = 0; j < numberOfCoefficients; ++j) {
                cin >> equationCoefficients[j];
            }
            coefficients[i] = equationCoefficients;
        }
        for (int i = 0; i < numberOfEquations - 1; ++i) {
            int maxRow = i;
            for (int k = i + 1; k < numberOfEquations; ++k) {
                if (fabs(coefficients[k][i]) > fabs(coefficients[maxRow][i])) {
                    maxRow = k;
                }
            }
            swap(coefficients[maxRow], coefficients[i]);

            if (fabs(coefficients[i][i]) < EPSILON) {
                cout << "NO" << endl;
                break;
            }

            for (int k = i + 1; k < numberOfEquations; ++k) {
                double factor = coefficients[k][i] / coefficients[i][i];
                for (size_t j = i; j < coefficients[k].size(); ++j) {
                    coefficients[k][j] -= factor * coefficients[i][j];
                }
            }
        }
        vector<double> solution(numberOfEquations);
        for (int i = numberOfEquations - 1; i >= 0; --i) {
            solution[i] = coefficients[i].back();
            for (int j = i + 1; j < numberOfEquations; ++j) {
                solution[i] -= coefficients[i][j] * solution[j];
            }
            solution[i] /= coefficients[i][i];
        }
        cout << "YES" << endl;
        cout << fixed << setprecision(2);
        for (int i = 0; i < numberOfEquations; ++i) {
            cout << setw(6) << solution[i];
            if (i < numberOfEquations - 1) cout << " ";
        }
        cout << endl;
    }

    return 0;
}
