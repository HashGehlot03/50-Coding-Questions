## Generate all subsequences of given string

- String containig n characters has 2^n subsequences

```cpp

// This function is for generating subsequences of integer array but it works same for string subsequences
void generateSubseq(int i, vector<int> &output, vector<int> &arr)
{
    // Time Complexity - O(2^N)
    if (i == arr.size())
    {
        for (auto it : output)
            cout << it << " ";
        cout << endl;
        return;
    }
    output.push_back(arr[i]);
    generateSubseq(i + 1, output, arr);
    output.pop_back();
    generateSubseq(i + 1, output, arr);
}

int main()
{
    vector<int> arr = {1, 2, 3, 4};
    vector<int> ds;
    generateSubseq(0, ds, arr);
    return 0;
}

```
