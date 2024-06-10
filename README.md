# Trapping-rain-water
Given array elements find the maximum water that can be trapped between the elements
//Trapping rain water problem
#include<iostream>
#include<bits/stdc++.h>
using namespace std;

int main(){
	int n;
	cout<<"Enter size of array: ";
	cin>>n;
	int arr[n];
	for(int i=0;i<n;i++){
		cin>>arr[i];
	}
	//1 st approach
//	int res=0;
//	for(int i=1;i<n-1;i++){
//		int lmax=arr[i];
//		for(int j=0;j<i;j++){
//			lmax=max(lmax,arr[j]);
//		}
//		int rmax=arr[i];
//		for(int j=i+1;j<n;i++)
//		{
//			rmax=max(rmax,arr[j]);
//		}
//		res+=min(lmax,rmax)-arr[i];
//	}
//	cout<<"Max water stored is: "<<res;
	
	//2 nd approach
	int res=0;
	int lmax[n],rmax[n];
	lmax[0]=arr[0];
	rmax[n-1]=arr[n-1];
	for(int i=0;i<n;i++){
		lmax[i]=max(lmax[i-1],arr[i]);
	}
	for(int i=n-2;i>=0;i--){
		rmax[i]=max(rmax[i+1],arr[i]);
	}
	for(int i=1;i<n;i++){
		res+=min(lmax[i],rmax[i])-arr[i];
	}
	cout<<"Max water stored is: "<<res;
	return 0;
}	
