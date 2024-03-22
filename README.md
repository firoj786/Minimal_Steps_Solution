# Minimal_Steps_Solution

import java.util.HashMap;
import java.util.Map;

public class MinimalStepsSolution {

    public static void main(String[] args) {
    
        MinimalStepsSolution solution = new MinimalStepsSolution();
        
        // Test cases
        System.out.println("Minimal steps for ABCDABCE: " + solution.minimalSteps("ABCDABCE"));
        
        System.out.println("Minimal steps for ABСАВСЕ: " + solution.minimalSteps("ABСАВСЕ"));
        
        // Test whether all tests pass
        
        if (solution.doTestsPass()) {
        
            System.out.println("All tests passed.");
            
        } else {
        
            System.out.println("Tests failed.");
        }
    }

    public boolean doTestsPass() {
    
        return minimalSteps("ABCDABCE") == 8 && minimalSteps("ABСАВСЕ") == 7;
        
    }

    public int minimalSteps(String s) {
    
        if (s == null || s.isEmpty()) {
        
            return 0;
        }

        int steps = 0;
        
        Map<Character, Integer> charCounts = new HashMap<>();

        for (int i = 0; i < s.length(); i++) {
        
            char c = s.charAt(i);
            
            int count = charCounts.getOrDefault(c, 0) + 1;
            
            charCounts.put(c, count);

            if (count == 1 || count == 2) {
            
                steps++; // Increment steps for unique character or first repeating character
                
            } else if (count > 2) { // Decrement for every occurrence after the second
            
                steps -= 2;
                
            }
            
        }


        return steps;
        
    }
    }


Approach:

The code aims to calculate the minimal steps required to transform a given 

string into a specific pattern based on certain rules:

For each unique character encountered, one step is added.

For the first repeating character encountered, another step is added.

For every subsequent occurrence of a character after the second one, two steps are subtracted.

Algorithm:

1. Initialize a variable steps to keep track of the minimal steps required.

2. Create a HashMap called charCounts to store the count of each character encountered in the input string.
  
3. Iterate through each character of the input string.
   
4. For each character:
   
. Retrieve its count from the charCounts map. If the character is not present in the map, the count is initialized to 0.

. Increment the count for the current character in the charCounts map.

. Based on the count of the character, adjust the steps variable:

  .  If the count is 1 or 2, increment steps (for unique characters or the first repeating character).
  
  . If the count is greater than 2, decrement steps by 2 for every subsequent occurrence of the character after the second one.
  
 .  Return the final value of steps after processing all characters.
 
   
    Complexity Analysis:

Time Complexity: The algorithm iterates through each character of the input

string once, resulting in a time complexity of O(n), where n is the length of the input string.

Space Complexity: The algorithm utilizes extra space for storing character counts in the HashMap.

The space complexity is O(c), where c is the number of unique characters in the input string. 

In the worst case, if all characters are unique, the space complexity is O(n).


