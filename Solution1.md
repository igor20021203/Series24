#include <iostream>
#include <math.h>
using namespace std;

/*
	Дано целое число N и набор из N целых чисел, содержащий по крайней мере два нуля. Вывести сумму чисел из данного набора, 
	расположенных между последними двумя нулями (если последние нули идут подряд, то вывести 0). 
*/

int main()
{
	setlocale(LC_ALL, "ru");

	float exit;
	int n, a, summ = 0, summ1 = 0, summ2 = 0, summ3 = 0, res = 0, count = 0, x = 0, y = 0;

	cout << "Введите N: ";
	cin >> n;

	for (int i = 1; i <= n; i++)
	{
		cin >> a;

		if (a == 0 && i != n)
			++count;

		if (count >= 3)
		{
			if (count % 2 == 1 && count != 0)
			{
				summ += a;
				x = summ;
				summ1 = 0;
			}
			else if (count % 2 == 0 && count != 0)
			{
				summ1 += a;
				y = summ1;
				summ = 0;
			}
		}
		else if (count < 2 && count > 0)
			summ2 += a;
		else if (count < 3 && count > 1)
			summ3 += a;

		if (i == n)
		{
			if (a == 0)
			{
				++count;

				if (count % 2 == 0)
					res = summ;
				else if (count % 2 == 1)
					res = summ1;
			}
			else
			{
				if (count % 2 == 0)
					res = x;
				else if (count % 2 == 1)
					res = y;
			}

			if (count == 2)
				res = summ2;
			else if (count == 3)
				res = summ3;
		}
	}

	cout << "Сумма = " << res << endl;

	cout << endl;
	cout << "Для завершения программы введите любое число: ";
	cin >> exit;
}
