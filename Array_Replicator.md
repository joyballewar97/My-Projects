# My-Projects
using System;

namespace ArrayReplicator
{
    class Program
    {
        static void Main(string[] args)
        {
            // Get the length of the array from the user
            int arrayLength = GetIntFromUser("Enter the length of the array: ");

            // Create the original array with the specified length
            int[] Original = CreateIntArray(arrayLength);

            // Fill the original array with values entered by the user
            for (int i = 0; i < Original.Length; i++)
            {
                Original[i] = GetIntFromUser("Enter a value for the array: ");
            }

            // Copy the original array to a new array
            int[] Copied = CopyArray(Original);

            // Write the original and copied arrays to the console
            WriteArrays(Original, Copied);
        }

        // Function to get an integer input from the user
        public static int GetIntFromUser(string message)
        {
            Console.WriteLine(message);
            int input = 0;
            bool success = false;

            // Parse the user input to an integer, or repeat if input is invalid
            while (!success)
            {
                try
                {
                    input = int.Parse(Console.ReadLine());
                    success = true;
                }
                catch (Exception)
                {
                    Console.WriteLine("Invalid input. Please enter an integer: ");
                }
            }

            return input;
        }

        // Function to create an integer array of the specified length
        public static int[] CreateIntArray(int arrayLength)
        {
            int[] array = new int[arrayLength];
            return array;
        }

        // Function to copy an integer array to a new array
        public static int[] CopyArray(int[] Original)
        {
            int[] Copied = new int[Original.Length];
            Array.Copy(Original, Copied, Original.Length);
            return Copied;
        }

        // Function to write the original and copied arrays to the console
        public static void WriteArrays(int[] Original, int[] Copied)
        {
            // Check if the original and copied arrays have the same length
            if (Original.Length != Copied.Length)
            {
                throw new Exception("Arrays are not the same size.");
            }

            // Write the original array to the console
            Console.WriteLine("Original Array: ");
            for (int i = 0; i < Original.Length; i++)
            {
                Console.Write(Original[i] + " ");
            }
            Console.WriteLine();

            // Write the copied array to the console
            Console.WriteLine("Copied Array: ");
            for (int i = 0; i < Copied.Length; i++)
            {
                Console.Write(Copied[i] + " ");
            }
        }
    }
}
