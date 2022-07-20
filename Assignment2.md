public class OnlineCart
{
    public void CheckOut(PaymentType paymentType)
    {
        switch(paymentType)
        {
            case PaymentType.CreditCard:
                    ProcessCreditCardPayment();
                    break;
            case PaymentType.Paypal:
                    ProcessPaypalPayment();
                    break;
            case PaymentType.GoogleCheckout:
                    ProcessGooglePayment();break;
            case PaymentType.AmazonPayments:P
                    ProcessAmazonPayment();
                    break;
        }
    }
    private void ProcessCreditCardPayment()
    {
        Print("Credit card payment chosen");
    }
    private void ProcessPaypalPayment(){
        Print("Paypal payment chosen");
    }
    private void ProcessGooglePayment()
    {
        Print("Google payment chosen");
    }
    private void ProcessAmazonPayment()
    {
        Print("Amazon payment chosen");
    }
}

Observation: The checkout method violates the SRP as it tries to handle and print messages for multiple payment gateways/mode.
Design with the fix:  Use a strategy pattern:


![image](https://user-images.githubusercontent.com/109504231/179925888-0697188d-fdf2-42bc-a170-bc548771ec8f.png)
<img width="599" alt="Assignment2" src="https://user-images.githubusercontent.com/109504231/179925921-7f0b2680-dde2-43eb-b9eb-d4640585cb60.PNG">



