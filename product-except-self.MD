### Product of Array Except Self

<https://leetcode.com/problems/product-of-array-except-self/>

```C++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> products;
        products.push_back(1);
        for (int i = 0; i < nums.size() - 1; ++i) {
            products.push_back(products.back() * nums[i]);
        }
        
        int right_product = 1;
        for (int i = nums.size() - 1; 0 <= i; --i) {
            products[i] *= right_product;
            right_product *= nums[i];
        }
        
        return products;
    }
};
```
