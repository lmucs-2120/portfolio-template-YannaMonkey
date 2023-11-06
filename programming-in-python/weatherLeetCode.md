https://leetcode.com/problems/daily-temperatures/description/
leet code problem we went over in class

many different ways to solve this problem.

# brute force
def dailyTemperatures1(temperatures: list[int]) -> list[int]:

    n = len(temperatures)
    answer = []

    for day in range(n):
        answer.append(0)
        for future_day in range(day + 1, n):
            if temperatures[future_day] > temperatures[day]:
                answer[day] = future_day - day
                break


    return answer

  using the stack
  
  # using a stack
def dailyTemperatures2(temperatures: list[int]) -> list[int]:
    n = len(temperatures)
    answer = [0] * n
    stack = []

    for curr_day, curr_temp in enumerate(temperatures):
        # Pop until the current day's temperature is not
        # warmer than the temperature at the top of the stack
        while stack and temperatures[stack[-1]] < curr_temp:
            prev_day = stack.pop()
            answer[prev_day] = curr_day - prev_day
        stack.append(curr_day)

    return answer

  this can be usefull with time complexity
