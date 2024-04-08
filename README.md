# CTDL-DT
#include<bits/stdc++.h>
using namespace std;
struct sinhvien{
	char hoten[100];
	char gt[100];
	int namsinh;
	float diemtk;
};
void bubble_sort( sinhvien a[], int n){
	for(int i=0;i<n-1;i++){
		for (int j=n-1;j>i;j--){
			if (a[j].diemtk>a[j-1].diemtk){
				swap(a[j].diemtk,a[j-1].diemtk);
				swap(a[j].gt,a[j-1].gt);
				swap(a[j].hoten,a[j-1].hoten);
				swap(a[j].namsinh,a[j-1].namsinh);
			}
		}
	}
}
void selection_sort(sinhvien a[],int n){
	for(int i=0;i<n-1;i++){
		int m=i;
		for(int j=i+1;j<n;j++){
			if (a[j].diemtk>a[m].diemtk){
				m=j;
				if(m!=i){
					swap(a[m].diemtk,a[i].diemtk);
					swap(a[m].gt,a[i].gt);
					swap(a[m].hoten,a[i].hoten);
					swap(a[m].namsinh,a[i].namsinh);
				}
			}
		}
	}
}
void insertion_sort(sinhvien a[], int n){
	for (int i=1;i<n;i++){
		float tam=a[i].diemtk;
		int j=i-1;
	while (j>-1&& a[j].diemtk>tam){
		a[j+1].diemtk==a[j].diemtk;
	}
	a[j+1].diemtk=tam;	
}
}
void search(sinhvien a[], int n,int k,char*t){
 	int i=0;
 	while ( i<n&&a[i].diemtk!=k&& strcmp(a[i].hoten,t)!=0){
 		i++;
	 }
	 if (i<n){
	 	cout<<t<<" Diem tong ket: "<<k<<" Dung thu "<<i<<endl;
	 }
	 else
	 {
	 	cout<<"Khong ton tai";
	 }
 }
 void binary_search( sinhvien a[],int l,int r,float k){
	if (l>r){
		cout<<"Day rong ";
	}
	else
	{
		int m=(l+r)/2;
		if (a[m].diemtk==k){
			cout<<"Diem tong ket la: "<<k<<" Dung thu "<<m<<endl;
		}
		else if (a[m].diemtk>k){
			return binary_search(a,l,m,k);
		}
		else{
			return binary_search(a,m+1,r,k);
		}
	
	}
}
main(){
	sinhvien a[1000];
	int n;
	cout<<"\nNhap so luong sinh vien: ";
	cin>>n;
	for (int i=0;i<n;i++){
		cout<<"Ho va Ten cua SINH VIEN "<<i<<" la: "<<endl;
		fflush(stdin);gets(a[i].hoten);
		cout<<"Gioi tinh cua SINH VIEN "<<i<<" la: "<<endl;
	    fflush(stdin);gets(a[i].gt);
		cout<<"Nam sinh cua SINH VIEN "<<i<<" la: "<<endl;
		cin>>a[i].namsinh;
		cout<<"Diem tong ket cua SINH VIEN "<<i<<" la: "<<endl;
		cin>>a[i].diemtk;
	}
	bubble_sort(a,n);
	cout<<"Danh sach sau khi sap xep diem tong ket: "<<endl;
	for (int i=0;i<n;i++){
		cout<<setw(10)<<a[i].hoten<<setw(10)<<a[i].gt<<
		setw(10)<<a[i].namsinh<<setw(10)<<a[i].diemtk<<endl;
	}
	char ten[100];
	float k;
	cout<<"Nhap Ho va Ten sinh vien can tim: ";
	fflush(stdin);gets(ten);
	cout<<"Nhap diem tong ket cua sinh vien can tim: ";
	cin>>k;
	cout<<"Bang phuong tim kiem tuan tu"<<endl;
	search(a,n,k,ten);
	cout<<"Bang phuong tim kiem nhi phan"<<endl;
	binary_search(a,0,n-1,k);
	
}
