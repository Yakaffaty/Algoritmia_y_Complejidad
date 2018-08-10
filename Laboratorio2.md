
# Problema 1

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Diagnostics;

namespace MergeSort
{
    class Program
    {
        static void Main(string[] args)
        {
            //Aca se tiene que insertar el array desordenado
            int[] arr = new int[] { 3, 39, 61, 91, 57, 22, 75, 89, 9, 90, 63, 78, 28, 73, 20 };
            MergeSort(arr);
            Array.Reverse(arr);
            Console.WriteLine("Vector Ordenado de Menos a Mayor");
            for (int i = 0; i < arr.Length; i++)
                Console.Write(arr[i] + " ");
            Console.ReadLine();
        }

        public static void MergeSort(int[] x)
        {
            MergeSort(x, 0, x.Length - 1);
        }

        static private void MergeSort(int[] x, int i, int j)
        {
            if (i == j)
                return;
            int mitad = (i + j) / 2;
            MergeSort(x, i, mitad);
            MergeSort(x, mitad + 1, j);
            int[] aux = Merge(x, i, mitad, mitad + 1, j);
            Array.Copy(aux, 0, x, i, aux.Length);
        }


        static private int[] Merge(int[] x, int i1, int j1, int i2, int j2)
        {
            int a = i1;
            int b = i2;
            int[] result = new int[j1 - i1 + j2 - i2 + 2];

            for (int i = 0; i < result.Length; i++)
            {
                if (b != x.Length)
                {
                    if (a > j1 && b <= j2)
                    {
                        result[i] = x[b];
                        b++;
                    }
                    if (b > j2 && a <= j1)
                    {
                        result[i] = x[a];
                        a++;
                    }
                    if (a <= j1 && b <= j2)
                    {
                        if (x[b] <= x[a])
                        {
                            result[i] = x[b];
                            b++;
                        }
                        else
                        {
                            result[i] = x[a];
                            a++;
                        }
                    }
                }
                else
                {
                    if (a <= j1)
                    {
                        result[i] = x[a];
                        a++;
                    }
                }
            }
            return result;
        }
    }
}
```

# Problema 2

# Problema 3 
