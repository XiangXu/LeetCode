# Letter Combinations of a Phone Number

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Example:  

Input: "23"  
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]

## First solution

Runtime: **0 ms**

Memory: **38 MB**

```java
class Solution 
{
    private String[] keyboard = new String[]{"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz", ""};
    
    
    public List<String> letterCombinations(String digits) 
    {
        if(digits == null || digits.length() == 0)
            return Collections.emptyList();
        
        List<String> result = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        
        dfs(0, digits, sb, result);
        
        return result;
    }
    
    private void dfs(int index, String digits, StringBuilder sb, List<String> result)
    {
        if(index == digits.length())
        {
            result.add(sb.toString());
            return;
        }
        
        String letters = keyboard[digits.charAt(index) - '0'];
        for(char c : letters.toCharArray())
        {
            sb.append(c);
            dfs(index+1, digits, sb, result);
            sb.deleteCharAt(sb.length() - 1);
        }
    }
}   
```

**Time Complexity: O(n<sup>4</sup>)** 

pqrs will be 4.

**Space Complexity: O(n)**
