from collections import deque

class Solution:
    def max_of_subarrays(self, arr, k):
        
        dq = deque()   # stores indices
        result = []

        for i in range(len(arr)):
            
            # 1️⃣ Remove indices out of this window
            if dq and dq[0] == i - k:
                dq.popleft()

            # 2️⃣ Remove smaller elements from back
            while dq and arr[dq[-1]] < arr[i]:
                dq.pop()

            # 3️⃣ Add current index
            dq.append(i)

            # 4️⃣ Window formed → record max
            if i >= k - 1:
                result.append(arr[dq[0]])

        return result# Data-structure-practical-program16
