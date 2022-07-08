# Individual-work

#include "stdafx.h"

#include <iostream>

using namespace std;

int main()

{

    setlocale (LC_ALL, "Russian");
    
    int m1[256][256], x[256], m2[256][256], m3[256][256], n, temp, t=0, f; //Идентифицируем переменные
    
    cout<<"Введите количество городов"<<endl;
    
    cin>>n; //Вводим кол-во городов
    
    cout<<"Укажите длину путей. Если путь отсутствует, поставьте 0"<<endl;
    
    for (int i=0; i<n; i++) //Начинаем цикл для указания пути из города в город
    
    {
        for (int j=0; j<n; j++)
        {
            m1[i][j]=0;
        }
    }
    for (int i=0; i<n; i++)
    {
        for (int j=0; j<n; j++)
        {
            if (i!=j)
            {
                if (m1[i][j]==0)
                {
                    cout<<"Из города "<<i+1<<" в город "<<j+1<<' '; 
                    cin>>m1[i][j]; 
                    m1[j][i]=m1[i][j]; 
                }
            }
        }
    }
    cout<<"Получим нашу схему городов"<<endl;
    for (int i=0; i<n; i++) //Начинаем цикл для построения схемы городов (Или же весовой матрицы)
    {
        for (int j=0; j<n; j++)//Построение матрицы
        {
            cout<<m1[i][j]<<" "; //Вывод в консоль конечного результата
            if (j==n-1)
            {
                cout<<endl;
            }
        }
    }
    cout<<endl;
    cout<<"Введите город, с которого начнём путешесвтие"<<endl;
    cin>>f; //Выбираем первый город (f)
	cout << "Все комбинации" << endl;
    for (int i=0; i<n; i++) //Цикл, для построения всех возможных комбинаций перемещения
    {
        x[i]=i+1;
    }
    for(int i=0;i<n;i++)
        {
                for(int j=0;j<n-1;j++)
                {
                        temp=x[j];
                        x[j]=x[j+1];
                        x[j+1]=temp;
 
                        for(int k=0;k<n;k++)
                        {
                            cout<<x[k]; //Вывод в консоль первых вариантов
                          m2[t][k]=x[k];
                          
                        }
                        t++;
                        cout<<endl; 
                }
				cout<<endl;
        }
    t=0;
    for (int i=0; i<n; i++)
    {
        if (m2[i][0]==f)
            {
                for (int j=0; j<n; j++)
                {
                    m3[t][j]=m2[i][j];
                }
                m3[t][n]=f;
                t++;
             }
    }
    for (int i=0; i<t; i++)
    {
        for (int j=0; j<n+1; j++)
        {
            cout<<m3[i][j]; //Вывод в консоль вторых вариантов(Коротких)
            if (j==n)
            {
                cout<<endl;
            }
        }
    }
    system ("pause");
    return 0;
}
