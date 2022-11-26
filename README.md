# 0_CPP_Begginer46
/*
консольная программа, в которой создается и заполняется случайными числами массив и сортируется в порядке убывания значения элементов*/


#include<iostream>
#include<vector>
#include <stdlib.h>   
#include <time.h> 
using namespace std;


	int gener(int&, int&);  //создаю протатип функци генерации случайного числа с двумя аргументами
	                         // пользователь определяет вернию и нижную границу случайных чисел
	int sort1 (vector<int> &);// создаю протатив функции сортировки массива по возврастанию
	

	int main()
	{
		system("chcp 1251>nul");// строка для вывода русского языка
		srand(time(NULL)); // включение заголовочного файла <stdlib.h> для привезки генерации к часам машины
		                   // для генерации разной последовательной случайных чисел

		int max, min, S;
		cout << "сколько случаных чисел?" << endl;
		cin >> S;
		cout << "Введите нижнию границу случайных чисел" << endl;
		cin >> min;
		cout << "Введите верхняю границу случайных чисел" << endl;
		cin >> max;

		cout << "массив из случайных чисел: ";

		
		vector<int> arr;
		
		for (int i = 0; i < S; i++)      // цикл для заполнения массива случайными числами
		{
			int n = gener(min, max); // привязка результата функции генерации случайных чисел к переменной
			arr.push_back(n); // команда у вектора для добавления в конец массива случайного числа
			cout << arr[i] << " ";  
		}

		sort1(arr); // запуск функции сортировки вставками

		return 0;

	}

	int gener(int& min, int& max)
	{
		int n;
		n = min + rand() % (max - min + 1);  // способ генерации случайного числа в заданном диапазоне
		return n;
	}

	int sort1(vector<int>& arr) // прототип функции в качестве аргумента со ссылкой на массив
	{
		
		for(int i=1; i<arr.size();i++)  //запуск цикла для с прявязкой к колличества элементов массива
		{
			for (int j = i;j >0 && arr[j - 1] > arr[j]; j--)   // два условия,  элемент 1 меньше, чем элемент 0 и J больше ноля в, чтобы цикл невыпадал в отрицательные числа
			{
				swap(arr[j - 1], arr[j]);	
			}
		
		}
		cout << endl << "Отсортированый массив: по возрастанию ";
		for (int i = 0; i < arr.size(); i++)
		{
			
			cout << "  " << arr[i];
		}

		return 0;
	}
