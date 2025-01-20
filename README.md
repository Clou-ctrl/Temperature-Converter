# Temperature-Converter cpp
#include <iostream>
#include <iomanip>
#include <stdexcept>
using namespace std;

class TemperatureConverter {
    private:
        double temperature;
    public:
    
    TemperatureConverter(double temp = 0.0) : temperature(temp){}
    
    void setTemperature(double temp){
        temperature = temp;
    }
    double getTemperature() const {
        return temperature;
    }
    double celsiusToFahrenheit() const {
        return (temperature * 9.0 / 5.0 ) - 32.0;
    }
    double celsiusToKelvin() const{
        return temperature + 273.15;
    }
    double fahrenheitToCelsius() const {
        return (temperature - 32.0) * 5.0/9.0;
    }
    double fahrenheitToKelvin() const {
        return (temperature - 32.0) * 5.0/9.0 + 273.15;
    }
    double kelvinToCelsius() const {
        if (temperature < 0.0){
            throw
            invalid_argument("Temperature in Kelvin cannot be below or less than 0.");
        }return temperature - 273.15;
    }
    double kelvinToFahrenheit() const {
        if (temperature < 0.0){
            throw
            invalid_argument("Temperature in Kelvin cannot be below or less than 0.");
        }return (temperature - 273.15) * 9.0/5.0 + 32.0;
    } 
};
void displaymenu(){
    cout <<"\nTemperature Converter\n";
    cout <<"Please Choose Between 1-7 only (Example: 2)\n";
    cout <<"1 - Celsius to Fahrenheit\n";
    cout <<"2 - Celsius to Kelvin\n";
    cout <<"3 - Fahrenheit to Celsius\n";
    cout <<"4 - Fahrenheit to Kelvin\n";
    cout <<"5 - Kelvin to Celsius\n";
    cout <<"6 - Kelvin to Fahrenheit\n";
    cout <<"7 - Exit\n";
    cout <<"Enter your choice: ";
}
int main(){
    double temp;
    int choice;
    
    cout << fixed << setprecision(2);
    
    do{
        displaymenu();
        cin >> choice;
        
        if(choice == 7){
            cout <<"Exiting the program, GOODBYE!"<< endl;
            break;
        }
        cout <<"Enter the Temperature: ";
        cin >> temp;
        
        TemperatureConverter converter(temp);
        
        try{
            switch(choice){
                case 1:
                cout <<"Celsius to Fahrenheit: " << converter.celsiusToFahrenheit()<< "°F"<<endl;
                break;
                case 2:
                cout <<"Celsius to Kelvin: " << converter.celsiusToKelvin()<< "K"<<endl;
                break;
                case 3:
                cout <<"Fahrenheit to Celsius: " << converter.fahrenheitToCelsius()<< "°C"<<endl;
                break;
                case 4:
                cout <<"Fahrenheit to Kelvin: " << converter.fahrenheitToKelvin()<< "K"<<endl;
                break;
                case 5:
                cout <<"Kelvin to Celsius: " << converter.kelvinToCelsius()<< "°C"<<endl;
                break;
                case 6:
                cout <<"Kelvin to Fahrenheit: " << converter.kelvinToFahrenheit()<< "K"<<endl;
                break;
                default:
                cout <<"Invalid Input! Please try again!" << endl;
                break;
            }
        }catch (const invalid_argument& e){
            cout <<"Error: "<<e.what()<<endl;
        }
    }while (choice!=7);
        return 0;
}
