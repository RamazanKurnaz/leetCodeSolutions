# My Leet Code Solutions

(With JS or TS)

## Remove Duplicates from Sorted Array II
Given an integer array nums sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

### Example 1:

#### Input: nums = [1,1,1,2,2,3]
#### Output: 5, nums = [1,1,2,2,3,_]
###### Explanation: Your function should return k = 5, with the first five elements of nums being 1, 1, 2, 2 and 3 respectively. It does not matter what you leave beyond the returned k (hence they are underscores).

<button onclick="toggleCode('code1')">Cevabı Gör</button>
<pre id="code1" style="display:none;">
/**
 * @param {number[]} nums
 * @return {number}
 */
function removeDuplicates(nums) {
    if (nums.length === 0) return 0;
    
    let writeIndex = 1;  // Start from index 1 because index 0 is always valid
    let count = 1;       // Count the occurrences of the current number
    
    for (let i = 1; i < nums.length; i++) {
        if (nums[i] === nums[i - 1]) {
            count++;
        } else {
            count = 1;  // Reset count for a new element
        }
        
        if (count <= 2) {
            nums[writeIndex] = nums[i];
            writeIndex++;
        }
    }
    
    return writeIndex;
}
</pre>

## Jump Games II
You are given a 0-indexed array of integers nums of length n. You are initially positioned at nums[0].

Each element nums[i] represents the maximum length of a forward jump from index i. In other words, if you are at nums[i], you can jump to any nums[i + j] where:

```0 <= j <= nums[i] and i + j < n```

Return the minimum number of jumps to reach nums[n - 1]. The test cases are generated such that you can reach nums[n - 1].

#### Example 1:

#### Input: nums = [2,3,1,1,4]
#### Output: 2
#### Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.

<button onclick="toggleCode('code2')">Cevabı Gör</button>
<pre id="code2" style="display:none;">
const canJump = (nums) => {
    let farthest = 0;
    
    for (let i = 0; i <= farthest; i++) {
        farthest = Math.max(farthest, i + nums[i]);
        if (farthest >= nums.length - 1) return true;
    }
    
    return false;
};
</pre>

<script>
function toggleCode(id) {
    const codeBlock = document.getElementById(id);
    if (codeBlock.style.display === "none") {
        codeBlock.style.display = "block";
    } else {
        codeBlock.style.display = "none";
    }
}
</script>
