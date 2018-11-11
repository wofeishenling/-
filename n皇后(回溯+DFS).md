```c++
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
using namespace std;
bool isVaild(int currow, int curcol, vector<int> & pos)
{
	for (int i = 0; i < pos.size(); i++)
	{
		if (pos[i] != -1)
		{
			if (pos[i] == curcol || abs(pos[i] - curcol) == abs(i - currow))
				return false;
		}
	}
	return true;
}
void DFS(vector<int>& pos, vector<vector<string> >& res, int row)
{
	int n = pos.size();
	if (row == pos.size())
	{
		vector<string> out(n, string(n, '.'));
		for (int i = 0; i < n; ++i) {
			out[i][pos[i]] = 'Q';
		}
		res.push_back(out);
	}
	else
	{
		for (int i = 0; i < pos.size(); i++)
		{
			if (isVaild(row, i, pos))
			{
				pos[row] = i;
				DFS(pos, res, row + 1);
				pos[row] = -1;
			}
		}
	}
}
int main()
{
	int n;
	cin >> n;
	vector<int> pos(n, -1);
	vector<vector<string> > res;
	DFS(pos, res, 0);
	system("pause");
	return 0;
}
```
