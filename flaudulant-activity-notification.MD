## Fraudulent Activity Notifications (HackerRank)

<https://www.hackerrank.com/challenges/fraudulent-activity-notifications>

---
```C++
// Complete the activityNotifications function below.
int activityNotifications(vector<int> expenditure, int d) {
    int notice_count = 0;
    int idx_1 = (d + 1) / 2;
    int idx_2 = (d + 2) / 2;

    int num_count[200] = {0, };
    for (int i = 0; i < d; ++i) {
        ++num_count[expenditure[i]];
    }

    for (int i = d; i < expenditure.size(); ++i) {
        ++num_count[expenditure[i]];
        int curr = 0, med_1 = -1, med_2 = -1;
        for (int j = 0; j < 200; ++j) {
            curr += num_count[j];
            if (med_1 == -1 && curr >= idx_1) {
                med_1 = j;
            }
            if (med_2 == -1 && curr >= idx_2) {
                med_2 = j;
            }
            if (med_1 != -1 && med_2 != -1) {
                break;
            }
        }
        
        if (expenditure[i] >= (med_1 + med_2)) {
            ++notice_count;
        }
        
        --num_count[expenditure[i - d]];
    }
    return notice_count;
}
```
