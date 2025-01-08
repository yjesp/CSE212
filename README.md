using System;
using System.Collections.Generic;

public class Program
{
    // 1. Function to calculate multiples of a given number
    public static double[] MultiplesOf(double start, int count)
    {
        // Step 1: Initialize an array to store the results
        double[] multiples = new double[count];
        
        // Step 2: Use a loop to calculate the multiples
        for (int i = 0; i < count; i++)
        {
            // Multiply the starting number by (i + 1) to get the ith multiple
            multiples[i] = start * (i + 1);
        }
        
        // Step 3: Return the resulting array
        return multiples;
    }

    // 2. Function to rotate a list to the right
    public static List<int> RotateListRight(List<int> data, int amount)
    {
        // Step 1: Handle edge cases where the list is empty or no rotation is needed
        if (data == null || data.Count == 0 || amount == 0) return data;

        // Step 2: Calculate the effective rotation amount (to handle cases where amount exceeds list size)
        int rotation = amount % data.Count;

        // Step 3: Split the list into two parts
        List<int> lastPart = data.GetRange(data.Count - rotation, rotation); // Last part
        List<int> firstPart = data.GetRange(0, data.Count - rotation); // First part

        // Step 4: Combine the parts to create the rotated list
        lastPart.AddRange(firstPart);

        // Step 5: Return the resulting list
        return lastPart;
    }

    // Main function to test both methods
    public static void Main(string[] args)
    {
        // Test: MultiplesOf function
        Console.WriteLine("Testing MultiplesOf:");
        double[] multiplesResult = MultiplesOf(3, 5);
        Console.WriteLine("Result: " + string.Join(", ", multiplesResult)); // Expected output: 3, 6, 9, 12, 15

        // Test: RotateListRight function
        Console.WriteLine("\nTesting RotateListRight:");
        List<int> data = new List<int> {1, 2, 3, 4, 5, 6, 7, 8, 9};
        List<int> rotatedResult = RotateListRight(data, 5);
        Console.WriteLine("Result: " + string.Join(", ", rotatedResult)); // Expected output: 5, 6, 7, 8, 9, 1, 2, 3, 4
    }
}
