# AON
AON Mohammed  

// See https://aka.ms/new-console-template for more information
using System;

namespace SimpleLoginSystem
{
    class Program
    {
         
        const string USERNAME = "your_username";
        const string PASSWORD = "your_password";
        
        static void Main(string[] args)
        {
            Console.WriteLine("Welcome to the Simple Login System!");

            
            Console.Write("Enter username: ");
            string inputUsername = Console.ReadLine();

           
            Console.Write("Enter password: ");
            string inputPassword = Console.ReadLine();

            if (string.IsNullOrEmpty(inputUsername) || string.IsNullOrEmpty(inputPassword))
            {
                Console.WriteLine("Username or password cannot be empty.");
                return;
            }

            if (inputUsername != USERNAME || inputPassword != PASSWORD)
            {
                Console.WriteLine("Invalid username or password. Access denied.");
                return;
            }

            // Step 4: Generate OTP
            string otp = GenerateOTP();
            Console.WriteLine("Your one-time password (OTP) is: " + otp);

            // Step 5: Prompt user for OTP
            Console.Write("Enter the OTP: ");
            string inputOtp = Console.ReadLine();

            // Step 6: Validate OTP
            if (inputOtp == otp)
            {
                Console.WriteLine("Success! You are logged in.");
            }
            else
            {
                Console.WriteLine("Invalid OTP. Access denied.");
            }
        }

       
        static string GenerateOTP()
        {
            Random rand = new Random();
            int otp = rand.Next(100000, 1000000); 
            return otp.ToString();
        }
    }
}

