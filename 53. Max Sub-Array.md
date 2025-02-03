# **2️⃣ Maximum Subarray (LeetCode 53)**  

#### **First Intuition: Brute Force Approach**  
To find the maximum sum subarray, I immediately thought:  
> "Why not just check **all possible subarrays** and find the max sum?"  

So, I nested two loops—one to pick the start index and another to track the sum from that point. This worked, but when I submitted...  

❌ **TLE (Time Limit Exceeded)!**  
> "Ah F#ck, so there’s gotta be a better way…"  

#### **Understanding Why Brute Force Fails**  
- It checks **every subarray**, which means **O(n²) complexity**—way too slow for large inputs.  
- **Is there a way to avoid rechecking the same elements?**  

#### **Optimized Approach - Kadane’s Algorithm**  
I read about **Kadane’s Algorithm** and the **core intuition made sense**:  
1. **Track `curr_sum` (best sum ending at this index)**  
2. **Decide:**  
   - Extend the previous sum (`curr_sum + nums[i]`)  
   - Or start fresh at `nums[i]` (if extending is worse)  
3. **Keep track of the global max (`max_sum`)**  

This way, I don’t need to check all subarrays—**I build the best sum dynamically**!  

#### **Struggles While Writing Kadane’s**  
1. **First Issue:** I initialized `max_sum = '-inf'` instead of `float('-inf')`.   
   - Ah, right, `'-inf'` as a string isn’t what I want.   
2. **Second Issue:** Used `for i in nums:` but also accessed `nums[i]`, causing an **index error**.   
   - Ohhh… I need an index loop or just iterate over values directly.  
3. **Third Issue:** **Edge cases failed** for `nums = [-1, -2]`.  
   - Why? I was setting `max_sum = 0`, but what if all numbers are negative?  
   - Fix: **Initialize `max_sum = nums[0]` instead of 0** to handle single-element and all-negative cases.  

#### **Final Optimization - Why Did This Run in 8ms Instead of 96ms?**  
I found an **even faster** O(n) solution where:  
- **Reset `curr_sum = 0` when it drops below 0** (instead of tracking individual elements).  
- Fewer operations, simpler logic, **same result**—but **much faster**.  
- Even though both are O(n), fewer updates = lower runtime!  

---

### **Reflections & Takeaways**  
✔️ Brute force is useful to **understand the problem**, but not always practical.  
✔️ Edge cases expose weaknesses early—**debugging teaches more than coding!**  
✔️ Even within the same time complexity, **simpler logic can make a huge difference**.  
✔️ Every problem is a journey from **confusion → questioning → understanding → solving**—and that’s where real learning happens.  

---

This was fun! Excited for the next one. 🚀
