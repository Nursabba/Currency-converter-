# Currency-converter-
package CodeAlpha;
import java.math.BigDecimal;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;
public class Currencyconverter {
    public static void main(String[] args) {
        Scanner sc= new Scanner(System.in);

        System.out.println("Welcome to Currency Converter!");
        System.out.print("Enter the source currency code (e.g., USD): ");
        String fromCurrency = sc.nextLine();

        System.out.print("Enter the target currency code (e.g., INR): ");
        String toCurrency = sc.nextLine();

        System.out.print("Enter the amount to convert: ");
        BigDecimal amount = sc.nextBigDecimal();

        // Simulate exchange rates (replace with actual rates if needed)
        Map<String, BigDecimal> exchangeRates = new HashMap<>();
        exchangeRates.put("USD", BigDecimal.valueOf(1.0));
        exchangeRates.put("INR", BigDecimal.valueOf(85.0));
        exchangeRates.put("EUR", BigDecimal.valueOf(88.0));
        // Add more exchange rates as needed

        // Perform currency conversion
        BigDecimal fromRate = exchangeRates.get(fromCurrency);
        BigDecimal toRate = exchangeRates.get(toCurrency);

        if (fromRate != null && toRate != null) {
            BigDecimal convertedAmount = amount.multiply(toRate).divide(fromRate, 2, BigDecimal.ROUND_HALF_UP);
            System.out.println(amount + " " + fromCurrency + " = " + convertedAmount + " " + toCurrency);
        } else {
            System.err.println("Invalid currency codes.");
        }
    }
}