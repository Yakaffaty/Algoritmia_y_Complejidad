
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
``` c#
using System;
using System.Collections.Generic;
using System.Linq; 
using System.Diagnostics;
namespace Heap
{
    class HeapTry
    {
        private static bool HeapIntent(int[] Arr, int i, int n)
        {
            if(i > (n-2)/2)
            {
                return true;
            }

            if (Arr[i] >= Arr[2 * i + 1] && Arr[i] >= Arr[2 * i + 2] && HeapIntent(Arr, 2 * i + 1, n) && HeapIntent(Arr, 2 * i + 2, n))
            {
                return true;
            }

            return false; 
 


        }

   


        static void Main(string[] args)
        {
            int[] heap = { 16, 14, 10, 8, 7, 9, 3, 2, 4, 1 };
            int n = heap.Length / 4;

            if(HeapIntent(heap,0,n)== true)
            {
                Console.WriteLine("Si es un heap");
            } else
            {
                Console.WriteLine("No es un heap");
            }

        }


    }
}
```
Este caso corre en O(n)
# Problema 3 
```
while ( i < = heapsize) {
 iz <- izquierda(i)
 der <- derecha(i)
 if (iz<=heapsize) and (A[iz]>A[i])
  mayor <- iz
 else
  mayor <- i 
 if (der<=heapsize) and (A[der]>A[mayor])
  mayor <- der
 if (mayor!= i)
 {
   exchange A[i] <-> A[mayor]
   i <- mayor
 } 
 else
  break
}
```
