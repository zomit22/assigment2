#include <iostream>
#include <algorithm>
using namespace std;

int sequentialSearch(int arr[], int n, int target) {
    int comparisons = 0;
    for (int i = 0; i < n; i++) {
        comparisons++;
        if (arr[i] == target) {
            cout << "Found at index " << i << " with " << comparisons << " comparisons.\n";
            return i;
        }
    }
    cout << "Not found with " << comparisons << " comparisons.\n";
    return -1;
}

int binarySearch(int arr[], int n, int target) {
    int comparisons = 0;
    int left = 0, right = n - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        comparisons++;
        
        if (arr[mid] == target) {
            cout << "Found at index " << mid << " with " << comparisons << " comparisons.\n";
            return mid;
        }
        
        if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    cout << "Not found with " << comparisons << " comparisons.\n";
    return -1;
}

int main() {
    int n, target;

    cout << "Enter the number of elements: ";
    cin >> n;

    int arr[n];

    cout << "Enter the elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cout << "Enter the target element: ";
    cin >> target;

    cout << "\nSequential Search:\n";
    sequentialSearch(arr, n, target);

    sort(arr, arr + n);

    cout << "\nBinary Search (after sorting the array):\n";
    binarySearch(arr, n, target);

    return 0;
}
