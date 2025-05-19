import java.util.Scanner;

class Calculator {
	double a;
	double b;
	String operation;

	// Method to set inputs
	public void setInputs(double a, double b, String operation) {
		this.a = a;
		this.b = b;
		this.operation = operation.toLowerCase(); // Normalize input
	}

	// Method to perform calculation
	public double calculate() {
		switch (operation) {
		case "add":
		case "addition":
			return a + b;
		case "subtract":
		case "subtraction":
			return a - b;
		case "multiply":
		case "multiplication":
			return a * b;
		case "divide":
		case "division":
			if (b != 0) {
				return a / b;
			} else {
				throw new ArithmeticException("Cannot divide by zero.");
			}
		default:
			throw new IllegalArgumentException("Invalid operation type.");
		}
	}

	// Main method
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		System.out.print("Enter value for a: ");
		double a = scanner.nextDouble();

		System.out.print("Enter value for b: ");
		double b = scanner.nextDouble();

		scanner.nextLine(); // Consume newline
		System.out.print("Enter operation (add, subtract, multiply, divide): ");
		String operation = scanner.nextLine();

		Calculator calc = new Calculator();
		try {
			calc.setInputs(a, b, operation);
			double result = calc.calculate();
			System.out.println("Result: " + result);
		} catch (Exception e) {
			System.out.println("Error: " + e.getMessage());
		}

		scanner.close();
	}
}
