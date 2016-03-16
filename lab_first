

#include "stdafx.h" 
#include <iostream> 
#include <stdio.h> 
#include <string> 
#include <conio.h> 
#include <windows.h> 
#include <stdlib.h> 
#include <fstream> 
using namespace std;
class Matrix
{
public:
	Matrix();
	Matrix(Matrix &a);
	~Matrix();
	Matrix(int _lines, int _columns);
	void read_matrix(string s);
	void print_matrix();
	Matrix operator + (Matrix array);
	Matrix operator * (Matrix array);
	int* operator [](int i);
	Matrix operator =(Matrix &a);
	int get_cout_columns();
	int get_cout_lines();
	void reset();
private:
	int lines;
	int columns;
	int **nom;
};
Matrix::Matrix()
{
	lines = 0;
	columns = 0;
	nom = new int*[0];
	nom[0] = new int[0];

};

Matrix::~Matrix()
{
	for (int i = 0; i < lines; i++)

		delete[] nom[i];
	delete[] nom;

}

Matrix::Matrix(Matrix &copy)
{
	lines = copy.lines;
	columns = copy.columns;
	nom = new int*[lines];
	for (int i = 0; i < lines; i++)
	{
		nom[i] = new int[columns];
	}
	for (int i = 0; i < lines; i++)
		for (int j = 0; j < columns; j++)
			nom[i][j] = copy.nom[i][j];

}


Matrix::Matrix(int _lines, int _columns)
{
	lines = _lines;
	columns = _columns;
	nom = new int*[lines];
	for (int i = 0; i < lines; i++)
	{
		nom[i] = new int[columns];
	}

}

void Matrix::read_matrix(string s)
{
	ifstream fin(s);
	for (int i = 0; i < lines; i++)
		for (int j = 0; j < columns; j++)
			fin >> nom[i][j];
	fin.close();

}
void Matrix::print_matrix()
{
	for (int i = 0; i < lines; i++) {

		for (int j = 0; j < columns; j++)
			cout << nom[i][j] << " ";
		cout << endl;
	}
}
Matrix Matrix::operator = (Matrix &a)
{
	for (int i = 0; i < lines; i++)

		delete[] nom[i];
	delete[] nom;
	lines = a.lines;
	columns = a.columns;
	nom = new int*[lines];
	for (int i = 0; i < lines; i++)
	{
		nom[i] = new int[columns];
	}
	for (int i = 0; i < lines; i++)
		for (int j = 0; j < columns; j++)
			nom[i][j] = a.nom[i][j];

	return *this;
}


Matrix Matrix::operator + (Matrix array)
{

	Matrix result(*this);
	for (int i = 0; i < result.lines; i++)
		for (int j = 0; j < result.columns; j++)
			result.nom[i][j] += array.nom[i][j];
	return(result);
}

Matrix Matrix::operator * (Matrix array)
{

	Matrix result(lines, array.get_cout_columns());
	result.reset();
	for (int i = 0; i < lines; i++)
		for (int j = 0; j < array.get_cout_lines(); j++)
			for (int t = 0; t < columns; t++)
				result.nom[i][j] += nom[i][t] * array.nom[t][j];
	return result;
}

int* Matrix::operator [] (int i)
{
	int *temp = new int[columns];
	for (int j = 0; j < columns; j++)
		temp[j] = nom[i - 1][j];
	return(temp);

}
int Matrix::get_cout_columns()
{
	return(columns);
}

int Matrix::get_cout_lines()
{
	return(lines);
}
void Matrix::reset()
{
	for (int i = 0; i < lines; i++)
		for (int j = 0; j < columns; j++)
			nom[i][j] = 0;
}
int main(void)
{
	setlocale(LC_ALL, "Russian");

	Matrix matrix(5, 5);
	Matrix matrix1(5, 5);
	Matrix matrix2(5, 5);
	string s;
	cout << "Введить путь к файлу '*.txt' " << endl;
	cin >> s;
	matrix.read_matrix(s);
	matrix.print_matrix();
	int *line_matrix;
	line_matrix = matrix[2];
	cout << "Вторая строка матрицы:" << endl;
	for (int i = 0; i < matrix.get_cout_columns(); i++)
		cout << line_matrix[i] << " ";

	cout << endl;
	matrix1 = matrix * matrix;
	cout << "Матрица после произведения:" << endl;
	matrix1.print_matrix();
	matrix2 = matrix + matrix;
	cout << "Матрица после сложения:" << endl;
	matrix2.print_matrix();

	system("pause");


}
