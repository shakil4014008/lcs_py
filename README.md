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
 
class solution: 
  def __init__(self):
      self.dic = {}
  
  def lcs(self, x, y, s1, s2):
      if (x,y) in self.dic:
          return self.dic[(x,y)]

      ans = -1
      if 0 in (x, y): 
          self.dic[(x,y)] = 0
          ans = 0 
      elif s1[x-1] == s2[y-1]:
          ans = 1+ self.lcs(x-1, y-1, s1, s2)
    
      else:
          sc1 = self.lcs(x-1, y, s1, s2)
          sc2 = self.lcs(x, y-1, s1, s2)
          ans = max(sc1, sc2)
      self.dic[(x,y)] = ans
      return ans


x = solution()
print(x.lcs(6,5, "ABCDAE", "ABCDE"))

````
