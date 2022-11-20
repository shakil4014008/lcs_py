# lcs_py

````py
Given two sequences, find the length of longest subsequence present in both of them. Both the strings are of uppercase.

Example 1:

Input:
A = 6, B = 6
str1 = ABCDGH
str2 = AEDFHR
Output: 3
Explanation: LCS for input Sequences
“ABCDGH” and “AEDFHR” is “ADH” of
length 3.
Example 2:

Input:
A = 3, B = 2
str1 = ABC
str2 = AC
Output: 2
Explanation: LCS of "ABC" and "AC" is
"AC" of length 2.
Your Task:
Complete the function lcs() which takes the length of two strings respectively and two strings as input parameters and returns the length of the longest subsequence present in both of them.

Expected Time Complexity : O(|str1|*|str2|)
Expected Auxiliary Space: O(|str1|*|str2|)

Constraints:
1<=size(str1),size(str2)<=103


class Solution: 
  def __init__(self):
      self.dic = {} # global dictionary for dp arrangement
  
  def lcs(self, x, y, s1, s2):
      if (x,y) in self.dic: # reuse if already exist the tuple (x,y) index
          return self.dic[(x,y)]

      ans = -1
      if 0 in (x, y): # base case
          self.dic[(x,y)] = 0
          ans = 0 
      elif s1[x-1] == s2[y-1]:
          ans = 1+ self.lcs(x-1, y-1, s1, s2)
    
      else:
          sc1 = self.lcs(x-1, y, s1, s2)
          sc2 = self.lcs(x, y-1, s1, s2)
          ans = max(sc1, sc2)
      self.dic[(x,y)] = ans # update dictionary
      return ans

````
