package s;

interface PaymentMethod {
    void pay(double amount);
}

class UpiPayment implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Paid " + amount + " via UPI");
    }
}

class CreditCardPayment implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Paid " + amount + " via Credit Card");
    }
}

class PayPalPayment implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Paid " + amount + " via PayPal");
    }
}

class OrderService {
    private final PaymentMethod paymentMethod;

    OrderService(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod;
    }

    void completeOrder(double amount) {
        paymentMethod.pay(amount);
    }
}

public class DependencyInversionPrinciple {
    public static void main(String[] args) {
        PaymentMethod payment = new UpiPayment(); // You can switch to CreditCardPayment or PayPalPayment
        OrderService service = new OrderService(payment);
        service.completeOrder(500); // Example amount
    }
}
