- In this we take a sorted array and search for a specific element by comparing the middle element with the searching element and choose either left or right side based on output of comparison.

```cpp
int l = 0;
int r = arr.size()-1;
// s -> search ele

while(l<r){
	int mid = l + (r-l)/2;
	if(arr[mid] == s){
		cout << "Found";
		break;
	}
	else if(arr[mid] > s){
		r = mid-1;
	}
	else{
		l = mid+1;
	}
}
```

> Time Complexity :
> Space Complexity :