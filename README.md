# LEETCODE-Array-995
Sure, let's do a step-by-step dry run of the `minKBitFlips` method in the `Solution` class using an example input.

We'll use the following example to illustrate the process:

```java
int[] nums = {0, 1, 0};
int k = 1;
```

Here's the method code again for reference:

```java
public int minKBitFlips(int[] nums, int k) {
    int n = nums.length;

    int flips = 0;
    int flipCountFromPastForCurri = 0;

    for (int i = 0; i < n; i++) {

        if (i >= k && nums[i - k] == 2) { // Was it flipped
            flipCountFromPastForCurri--;
        }

        if (flipCountFromPastForCurri % 2 == nums[i]) {
            if (i + k > n) {
                return -1;
            }
            flipCountFromPastForCurri++;
            nums[i] = 2; // Marking as flipped
            flips++;
        }
    }

    return flips;
}
```

Now let's go through the code step-by-step:

1. **Initialization**:
    - `n = 3` (length of `nums`)
    - `flips = 0` (counter for the number of flips)
    - `flipCountFromPastForCurri = 0` (tracks the number of flips affecting the current index `i`)

2. **Iteration over `nums`**:

    - **i = 0**:
        - `i >= k` condition is `false` since `0 < 1`, so we skip the inner `if`.
        - `flipCountFromPastForCurri % 2 == nums[i]` translates to `0 % 2 == 0` which is `true`.
        - `i + k > n` translates to `0 + 1 > 3` which is `false`.
        - `flipCountFromPastForCurri++` -> `flipCountFromPastForCurri = 1`.
        - `nums[0] = 2` to mark as flipped.
        - `flips++` -> `flips = 1`.
        - Updated `nums` array: `{2, 1, 0}`.

    - **i = 1**:
        - `i >= k` condition is `true` since `1 >= 1`.
        - `nums[i - k] == 2` translates to `nums[0] == 2` which is `true`.
        - `flipCountFromPastForCurri--` -> `flipCountFromPastForCurri = 0`.
        - `flipCountFromPastForCurri % 2 == nums[i]` translates to `0 % 2 == 1` which is `false`.
        - Skip the rest of the `if` block.

    - **i = 2**:
        - `i >= k` condition is `true` since `2 >= 1`.
        - `nums[i - k] == 2` translates to `nums[1] == 1` which is `false`.
        - Skip the inner `if` block.
        - `flipCountFromPastForCurri % 2 == nums[i]` translates to `0 % 2 == 0` which is `true`.
        - `i + k > n` translates to `2 + 1 > 3` which is `false`.
        - `flipCountFromPastForCurri++` -> `flipCountFromPastForCurri = 1`.
        - `nums[2] = 2` to mark as flipped.
        - `flips++` -> `flips = 2`.
        - Updated `nums` array: `{2, 1, 2}`.

3. **End of iteration**:
    - The final `flips` count is `2`.

Thus, the minimum number of `k`-bit flips required to make the array alternate between 0 and 1 starting from the first index is `2`.

So the method returns `2` for the given example.

The above dry run illustrates how the method processes each element of the input array `nums` and keeps track of the number of flips required to achieve the desired alternation.
