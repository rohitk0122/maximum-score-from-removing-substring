# maximum-score-from-removing-substring
class Solution {
    public int maximumGain(String s, int x, int y) {
    int big = x > y ? x : y;
        int small = big == x ? y : x;
        char first = big == x ? 'a' : 'b';
        char second = first == 'a' ? 'b' : 'a';
        int points = 0;
        
        Stack<Character> stack1 = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == second && !stack1.isEmpty() && stack1.peek() == first) {
                stack1.pop();
                points += big;
            } else {
                stack1.push(c);
            }
        }
        
        Stack<Character> stack2 = new Stack<>();
        while (!stack1.isEmpty()) {
            char c = stack1.pop();
            if (c == second && !stack2.isEmpty() && stack2.peek() == first) {
                stack2.pop();
                points += small;
            } else {
                stack2.push(c);
            }
        }
        
        return points;
      
    }
}
