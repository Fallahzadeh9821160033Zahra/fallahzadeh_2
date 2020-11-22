# fallahzadeh_2
My seccond repository on GitHub 
#include <iostream>
using namespace std;
class myarr{
	double *arr;
	int size;
public:
	myarr(double a[], int n){
		arr = new double[n];
		size = n;
		for (int i = 0; i<n; i++){
			arr[i] = a[i];
		}
	}
	myarr(myarr &A){
		delete[]arr;
		size = A.size;
		arr = new double[A.size];
		for (int i = 0; i < size; i++)
			arr[i] = A.arr[i];
	}
	myarr(int n = 1){
		size = n;
		arr = new double[n];
		for (int i = 0; i<n; i++)
			arr[i] = 0;
	}
	void print(void){
		for (int i = 0; i < size; i++)
			cout << i << "th :" << arr[i] << " ";
		cout << endl;
	}
	myarr add(myarr A){
		int n;
		if (A.size > size){
			n = size;
		}
		else n = A.size;
		myarr temp(n);
		int j = size, k = A.size;
		for (int i = 0; i < n; i++, j--, k--){
			temp.arr[i] = arr[i] + A.arr[i];
		}
		if (j != 0){
			for (int i = j; i < size; i++)
				temp.arr[i] = arr[i];
		}
		if (k != 0){
			for (int i = k; i < A.size; i++)
				temp.arr[i] = A.arr[i];
		}
		return temp;
	}
	myarr sub(myarr A){
		int n;
		if (A.size > size){
			n = size;
		}
		else n = A.size;
		myarr temp(n);
		int j = size, k = A.size;
		for (int i = 0; i < n; i++, j--, k--){
			temp.arr[i] = arr[i] - A.arr[i];
		}
		if (j != 0){
			for (int i = j; i < size; i++)
				temp.arr[i] = arr[i];
		}
		if (k != 0){
			for (int i = k; i < A.size; i++)
				temp.arr[i] = A.arr[i];
		}
		return temp;
	}
	myarr mul(myarr A){
		int n;
		if (A.size > size){
			n = size;
		}
		else n = A.size;
		myarr temp(n);
		for (int i = 0; i<n; i++)
			temp.arr[i] = arr[i] * A.arr[i];
		return temp;
	}
	~myarr(){
		delete[]arr;
	}
	myarr merg(myarr A){
		myarr temp;
		delete[]temp.arr;
		temp.size = size + A.size;
		temp.arr = new double[size + A.size];
		int j = 0;
		for (int i = 0; i < size; j++, i++)
			temp.arr[j] = arr[i];
		for (int i = 0; i < A.size; j++, i++)
			temp.arr[j] = A.arr[i];
		return temp;
	}
	myarr eshterak(myarr A){
		double B[100];
		int size = 0;
		for (int i = 0; i < size; i++){
			for (int j = 0; j < A.size; j++){
				if (arr[i] == A.arr[j]){
					B[size] = arr[i];
					size++;
					break;
				}
			}
		}
		myarr temp(B, size);
		return temp;
	}
	void operator = (myarr A){
		delete[]arr;
		size = A.size;
		arr = new double[A.size];
		for (int i = 0; i < size; i++)
			arr[i] = A.arr[i];
	}
};
void f1();
void f2();
void f3();
int main(void)
{
	f3();
	return 0;
}
void f3(){
	double tst[10];
	double tst2[10];
	for (int i = 0; i < 10; i++){
		tst[i] = i;
		tst2[i] = i * 2;
	}
	myarr a(tst, 10), b(tst2, 10);
	a = b;
	a.print();
}
void f2(void){
	double tst[10];
	double tst2[10];
	for (int i = 0; i < 10; i++){
		tst[i] = i;
		tst2[i] = i * 2;
	}
	myarr a(tst, 10), b(tst2, 10);
	a.print();
	b.print();
	a.merg(b).print();
	a.eshterak(b).print();
	a = b;
	b.print();
}
void f1(void){
	double tst[5];
	double tst2[5];
	for (int i = 0; i < 5; i++){
		tst[i] = i;
		tst2[i] = i * 2;
	}
	myarr a(tst, 5), d(tst2, 5), b(3), c;
	a.add(d).print();
	a.sub(d).print();
	a.mul(d).print();
}
