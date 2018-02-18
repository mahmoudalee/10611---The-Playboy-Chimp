# 10611---The-Playboy-Chimp

#include <iostream>
#include <algorithm>

using namespace std;

int ladies[50000];

int bsf(int s, int e, int key)
{

	int res = -1;
	while (s <= e)
	{
		int mid = s + (e - s) / 2;

		if (ladies[mid] >= key)
			e = mid - 1;
		else
		{
			s = mid + 1;
			res = mid;
		}
	}
	return res;
}

int bsl(int s, int e, int key)
{

	int res = -1;
	while (s <= e)
	{
		int mid = s + (e - s) / 2;
		if (ladies[mid] <= key)
			s = mid + 1;
		else if (ladies[mid] > key)
		{
			e = mid - 1;
			res = mid;
		}
	}
	return res;
}

int main()
{

	int lady;
	cin >> lady;
	for (int i = 0; i < lady; i++)
	{
		cin >> ladies[i];
	}
	int q;
	cin >> q;
	for (int i = 0; i < q; i++)
	{
		int tall;
		cin >> tall;

		// 1 4 5 7

		int f1 = bsf(0, lady - 1, tall);
		int f2 = bsl(0, lady - 1, tall);
		if (f1 == -1)
			cout << "X ";
		else
			cout << ladies[f1] << ' ';
		if (f2 == -1)
			cout << 'X' << endl;
		else
			cout << ladies[f2] << endl;
	}
	return 0;
}
