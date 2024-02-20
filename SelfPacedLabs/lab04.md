# Code Refactoring with GitHub Copilot

## Introduction

GitHub code refactoring refers to the process of restructuring and improving the quality of code in a GitHub repository without changing its external behaviour. Code refactoring aims to enhance readability, maintainability, and performance while reducing technical debt and potential bugs.

In this exercise, you will participate in a learning or practice activity where your main goal will be to use GitHub Copilot for code refactoring using the C# programming language. You will also be generating unit test functions using GitHub Copilot Chat.

### Task 1

1. Install the C# extension in VS Code: 
 - Click on the **Extensions** icon in the activity bar present on the left side of the Visual Studio Code window
 - Search for the **C#** extension in the _Search Extensions in Marketplace_ search box
 - Select **C#** from the list of results that show up and **Install**

2. Look at this example of poorly written C# code and analyze it. How could this code be improved?

```
using System;

class Program
{
    const int MAX = 100;

     static int Sum(int[] arr, int n)
     {
         int result = 0;
         for (int i = 0; i < n; i++)
         {
             result += arr[i];
         }
         return result;
     }

     static void Main()
     {
         int n;
         Console.Write("Enter the number of elements (1-100): ");
         if (!int.TryParse(Console.ReadLine(), out n) || n < 1 || n > MAX)
         {
             Console.WriteLine("Invalid input. Please provide a digit ranging from 1 to 100.");
             Environment.Exit(1);
         }

         int[] arr = new int[n];

         Console.WriteLine("Enter " + n + " integers:");
         for (int i = 0; i < n; i++)
         {
             if (!int.TryParse(Console.ReadLine(), out arr[i]))
             {
                 Console.WriteLine("Invalid input. Please enter valid integers.");
                 Environment.Exit(1);
             }
         }

         int total = Sum(arr, n);

         Console.WriteLine("Sum of the numbers: " + total);

         // No need to free memory in C#, as it's managed by the runtime.
     }
 }
```

Here are a few code-related issues: 
- The code begins with the inclusion of the System namespace for essential input and output operations.
- It defines a constant MAX with a value of 100 to represent the maximum number of elements allowed.
- The Sum method calculates the sum of elements in an array.
- In the Main method:
    - It prompts the user to enter the number of elements (between 1 and 100) and validates the input.
    - Allocates an array 'arr' to store the entered integers.
    - Prompts the user to enter the specified number of integers and validates each input.
    - Calculates the sum of the entered integers using the Sum method.
    - Outputs the sum to the console.
    - There's no need to manually free memory in C# because it manages memory automatically.

### Task 2

1. Open the GitHub Copilot Chat window by clicking the **Chat** extension icon

2. Copy the above code, and paste it into the text area. Type the prompt `Refactor the code` at the end of the code and press enter

3. GitHub Copilot chat will give a response that should look similar to the code below: 

```
using System;

class Program
{
    const int MAX = 100;

    static int Sum(int[] arr)
    {
        int result = 0;
        foreach (int numb in arr)
        {
            result += num;
        }
        return result;
    }

    static void Main()
    {
        int n;
        Console.Write("Enter the number of elements (1-100): ");
        if (!int.TryParse(Console.ReadLine(), out n) || n < 1 || n > MAX)
        {
            Console.WriteLine("Invalid input.")
            Environment.Exit(1);
        }

        int[] arr = new int[n];

        Console.WriteLine("Enter " + n + " integers:");
        for (int i = 0; i < n; i++)
        {
            if (!int.TryParse(Console.ReadLine(), out arr[i]))
            {
                if (!int.TryParse(Console.ReadLine(), out arr[i]))
                {
                    Console.WriteLine("Invalid input. Please enter valid integers.");
                    Environment.Exit(1);
                }
            }
        
        int total = Sum(arr);

        Console.WriteLine(Sum of the numbers: " + total);
        }
    }
}
```

4. Analyze the changes made to the code by GitHub Copilot Chat. What has changed?

- Here, GitHub Copilot removed the n parameter from the Sum method since it's not needed. Instead, the Copilot used a for-each loop to iterate over the array. As a result, the code is easier to comprehend and more concise.
- This includes the system namespace for input and output operations.
- Defines a constant MAX with a value of 100 for the maximum number of elements allowed in an array.
- The Sum method calculates the sum of elements in an integer array using a for-each loop.
- In the Main method:
    - Asks the user to input the number of elements and validate it.
    - Creates an integer array to store user-entered values.
    - Prompts the user to enter integers, validates the input, and stores them in the array.
    - Calculates the sum of the integers using the Sum method.
    - Shows the sum on the console.
    - The code includes input validation and provides the sum of user-entered integers.

### Task 3

1. Create a new file named `codechat.cs`

***Note:** If you see a recommendation to install the C# extension, click on **Install**

2. Add the below code into `codechat.cs`:

```
using System;

class Program
{
    static void Main()
    {
        int health = 100;
        int score = 0;

        Console.WriteLine("Welcome to the Adventure Game!");
        Console.WriteLine("You are in a dark forest.");

        while (health > 0)
        {
            Console.WriteLine("\nOptions:");
            Console.WriteLine("1. Go deeper into the forest.");
            Console.WriteLine("2. Rest by the campfire.");
            Console.WriteLine("3. Quit the game.");

            int choice;
            Console.Write("Enter your choice: ");
            if (int.TryParse(Console.ReadLine(), out choice))
            {
                switch (choice)
                {
                    case 1:
                        Console.WriteLine("You go farther into the forest and discover a treasure chest!");
                        score += 10;
                        break;
                    case 2:
                        Console.WriteLine("You rest by the campfire and regain 20 health.");
                        health += 20;
                        break;
                    case 3:
                        Console.WriteLine($"Thanks for playing! Your score: {score}");
                        return;
                    default:
                        Console.WriteLine("Invalid choice. Try again.");
                        break;
                }

                health -= 10;
                if (health <= 0)
                {
                    Console.WriteLine($"Game over. Your score: {score}");
                }
            }
            else
            {
                Console.WriteLine("Invalid input. Please enter a valid number.");
            }
        }
    }
}
```

4. Ask Copilot to use if-else statements instead of the current switch statement. Identify the second of code where the switch is present, and select it

5. Right-click on the code window and select **Copilot**, from the presented list of options, select **Start Code Chat**

7. Type the prompt `Use if-else statements instead of the switch statement`. Click `>` or press `Enter`

8. Review the response that Copilot provided, click **Accept** or **Discard** based on the code provided

### Task 4 

1. Push your code to the repository using either method provided below:

    #### Using Git Flow

    1. At the top of your VS Code window select the **Terminal** tab and click **New Terminal**. This will open a terminal window directly in your VS Code.
    2. Run the command below to add the `codechat.cs` file to the GitHub repo

    ```
    git add codechat.cs
    ```

    3. Commit the changes to the repo

    ```
    git commit -m "My refactoring copilot commit."
    ```

    4. Push the code to the repo

    ```
    git push
    ```

    5. Wait approx. 1 minute and refresh your GitHub repository to ensure that the changes are reflected in your repository

    #### Using the VS Code Interface

    1. Click the VS Code **Source Control** tab on the left hand of your VS Code screen or press `Ctrl + Shift + G` 
    2. Stage your changes by clicking the small plus icon in the righthand corner of the panel
    3. Enter a commit message and select the **Commit** button
    4. Once changes are staged, click the elipses in the far right corner, choose **Push** and enter your password
    5. Wait approx. 1 minute and refresh your GitHub repository to ensure that the changes are reflected in your repository