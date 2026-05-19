- Complex algorithm and Space inefficient.
- We are gonna divide the array into 2 parts({left -> mid} and {mid+1 -> right}).
- Then we are gonna merge the array's by comparing elements one by one 

```cpp
void Merge(vector<int> &arr,int left,int mid,int right){
	int n1 = mid - left +1;
	int n2 = right - mid;
	vector<int> arr1(n1),arr(n2);
	
	// Copy ele for swapping
	for(int i=0;i<n1;i++){
		arr1[i] = arr[l+i];
	}
	for(int i=0;i<n2;i++){
		arr2[i] = arr[i+mid+1];
	}
	int i =0,j=0;
	int k = left;
	
	// Sorting starts here
	while(i<n1 and j<n2){
		if(arr1[i] < arr2[j]){
			arr[k] = arr1[i];
			i++; 
		}	
		else{
			arr[k] = arr2[j];
			j++;	
		}
		k++;
	}
	
	// Copy Remaining ele (only one loop shall run)
	while(i<n1){
		arr[k] = arr1[i];
		k++;
	}
	while(j<n2){
		arr[k] = arr2[j];
		k++;
	}
}
void Divide(vector<int> &arr,int left,int right){
	if(l < r){
		int mid =(right+left)/2;
		Divide(arr,left,mid);
		Divide(arr,mid+1,right);
		Merge(arr,l,mid,r);
	}
}
```

> Time Complexity : O(nlogn)
> Space Complexity : O(n)