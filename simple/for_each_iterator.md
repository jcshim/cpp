#include<iostream> // cout
#include<vector> // vector
#include<algorithm> // sort
using namespace std; // vector, sort, cout
void pr(int n) {
	cout << n << ' ';
}
int main() {
	vector <int> v = { 1, 2, 5, 4, 3 };
	sort(v.begin(), v.end());
	//for (int i = 0; i < v.size(); i++) cout << v[i] << ' ';
	//for (auto i : v) cout << i << ' ';
	//for (auto it=v.begin(); it !=v.end(); ++it)  cout << *it << ' ';
	//for_each(v.begin(), v.end(), pr);
	//for_each(v.begin(), v.end(), [](int n) {cout << n << " "; });
}
