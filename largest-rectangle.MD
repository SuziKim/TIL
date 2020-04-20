### Largest Rectangle (HackerRank)

<https://www.hackerrank.com/challenges/largest-rectangle>

---

```C++
// Complete the largestRectangle function below.
long largestRectangle(vector<int> h) {
    long max_area = 0;

    for (size_t i = 0; i < h.size(); ++i) {
        long height = h[i];
        int width = 1;

        for (size_t j = i - 1; 0 <= j; --j) {
            if (h[j] < height) {
                break;
            }
            ++width;
        }
        for (size_t j = i + 1; j < h.size() ; ++j) {
            if (h[j] < height) {
                break;
            }
            ++width;
        }

        max_area = max(max_area, width * height);
    }

    return max_area;
}
```
