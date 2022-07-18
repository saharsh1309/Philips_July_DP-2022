# Philips_July_DP-
//C# Code
class Checker
{
    static bool batteryIsOk(float temperature, float soc, float chargeRate) {
        if(temperature < 0 || temperature > 45) {
            Console.WriteLine("Temperature is out of range!");
            return false;
        } else if(soc < 20 || soc > 80) {
            Console.WriteLine("State of Charge is out of range!");
            return false;
        } else if(chargeRate > 0.8) {
            Console.WriteLine("Charge Rate is out of range!");
            return false;
        }
        return true;
    }

Observation: 
This piece of code violates the SRP as it is handling 3 major responsibilities wherein it checks whether the tempeature, state of charge, and charge rate is in range or not. Extraction, as part of refactoring is a good way of distributing these multiple responsibilities and making the code more readable.
The method has 3 arguments in its definition which is an early indicator towards the violation of SRP as there might be multiple logics to process and handle those parameters to derive a result. Method ideally should not have more than one argument.
Also, if the validation logic for these parameters is changed then the whole method has to be changed, it's not closed for modification.

Refactoring: 

class Checker
{
    static bool batteryIsOk(float temperature, float soc, float chargeRate) {
        return IsTemperatureInRange(temperature) && IsStateOfChargeInRange(soc) && IsChargeRateInRange(chargeRate);
    }
    
    private static bool IsTemperatureInRange(float temperature)
    {
        if(temperature < 0 || temperature > 45) {
            Console.WriteLine("Temperature is out of range!");
            return false;
            }
        return true;
    }

    private static bool IsStateOfChargeInRange(float soc)
    {
            if(soc < 20 || soc > 80) {
            Console.WriteLine("State of Charge is out of range!");
            return false;
            }
        return true;
    }

    private static bool IsChargeRateInRange(float chargeRate)
    {
        if(chargeRate > 0.8) {
            Console.WriteLine("Charge Rate is out of range!");
            return false;
        }
        return true;
    }

}
