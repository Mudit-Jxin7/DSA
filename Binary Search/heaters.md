![heaters](https://github.com/Mudit-Jxin7/DSA/assets/97677133/71acff0a-0a67-49ce-9321-399f12853612)

Time = ```(N + M)LogM```

```class Solution {
public:
    pair<int, int> f(vector<int>& arr, int key) {
        int ceil = -1, floor = -1, s = 0, e = arr.size() - 1;
        while (s <= e) {
            int mid = s + (e - s) / 2;

            if (arr[mid] == key) {
                return {arr[mid], arr[mid]};
            } else if (arr[mid] > key) {
                e = mid - 1;
                ceil = arr[mid];
            } else {
                s = mid + 1;
                floor = arr[mid];
            }
        }

        return {floor, ceil};
    }

    int findRadius(vector<int>& houses, vector<int>& heaters) {
        sort(heaters.begin(), heaters.end());
        int ans = -1;
        for (int i = 0; i < houses.size(); i++) {
            int hp = houses[i];

            pair<int, int> p = f(heaters, hp);
            int left = (p.first == -1) ? INT_MAX : hp - p.first;
            int right = (p.second == -1) ? INT_MAX : p.second - hp;

            int mini = min(left, right);

            ans = max(mini, ans);
        }

        return ans;
    }
};
