# leetcode---20



用Stack的思维：

      def isValid(s):
          d = {'(':')', '{':'}','[':']'}
           （手动建对应项）
          stack = []
           （手动建stack空集，待会可以运用到相关功能）
          for i in s:
              if i in d:
                  # 如果在key里面，代表有左括号！丢进篓子里
                  stack.append(i)
              elif len(stack) == 0 or d[stack.pop()] != i:  
                  # 这里是两种情况合并起来了：1）第一个就不是左括号，不在key里面，所以空集
                  # 2）输入的第二个和第一个不匹配。  ——而这两种都属于错的
                  # stack.pop（）既可以去掉上一个，又可以表示那个被删掉的值。（删了，所以还是空集：所以最后一步要确认是空集）
                  # 应该要： d["("] = ")"。 要删掉的原因是:[()]，这种情况，把中间的删除，才能验证后面的【】。
                  return False
          return len(stack) == 0 
          # finally check if the stack still contains unmatched left bracket

      s = "()[]{}"
      print(isValid(s))
