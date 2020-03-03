## Frequency Queried @ HackerRank

<https://www.hackerrank.com/challenges/frequency-queries>

```C++
// Complete the freqQuery function below.
void Insert(unordered_map<int, int>& dictionary, vector<int>& counter, int target) {
    if (dictionary.find(target) == dictionary.end()) {
        dictionary.emplace(target, 0);
    }

    ++dictionary[target];
    if (counter.size() < dictionary[target]) {
        counter.resize(dictionary[target]);
    }
    --counter[dictionary[target] - 1];
    ++counter[dictionary[target]];
}

void Delete(unordered_map<int, int>& dictionary, vector<int>& counter, int target) {
    if (dictionary.find(target) == dictionary.end()) {
        return;
    }

    if (dictionary[target] > 0) {
        --counter[dictionary[target]];
        --dictionary[target];
        ++counter[dictionary[target]];
    }
}

int IsThereNOccurred(const vector<int>& counter, int n) {
    if (counter.size() < n) {
        return 0;
    }

    return (0 < counter[n]) ? 1 : 0;
}

vector<int> freqQuery(vector<vector<int>> queries) {
    unordered_map<int, int> dictionary;
    vector<int> occurrence_counter;
    vector<int> count_query;

    for (const auto& query: queries) {
        switch (query[0]) {
            case 1:
            Insert(dictionary, occurrence_counter, query[1]);
            break;

            case 2:
            Delete(dictionary, occurrence_counter, query[1]);
            break;
            
            case 3:
            count_query.push_back(IsThereNOccurred(occurrence_counter, query[1]));
            break;
        }
    }

    return count_query;
}
```
