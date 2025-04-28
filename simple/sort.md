```
#include<iostream> // cout
#include<vector> // vector
#include<algorithm> // sort
using namespace std; // vector, sort, cout
int main() {
	vector <int> v = { 1, 2, 5, 4, 3 };
	sort(v.begin(), v.end());
	for (auto i : v) {
		cout << i << ' ';
	}
}
```
