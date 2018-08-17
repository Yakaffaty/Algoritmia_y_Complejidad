## Problema 2
Cuando el arbol se separa en 2, no habra cambios en las posiciones, pero de igual manera tienen que haber funciones recursivas
que igual tomaran un pivote. Por lo tanto corre en O(n^2)

arr[] = {13,19,9,5,12,8,7,4,21,2,6,11}
Index:    0  1 2 3  4 5 6 7 8  9 10 11
low =  0, high = 11, pivote = arr[h] = 11
Index == -1

Se mueve de los elementos j = low a high - 1
j = 0 | se queda igual porque arr[j] > pivot

j = 1 : se queda igual porque arr[j] > pivot

j = 2: como arr[j] <= pivot, i == 0 y arr[i] == arr[j]
arr[] = {9,19,13,5,12,8,7,4,21,2,6,11}

j = 3: como arr[j] <= pivot, i == 1 y arr[i] == arr[j]
arr[] = {9,5,13,19,12,8,7,4,21,2,6,11}


j = 4 : se queda igual porque arr[j] > pivot

j = 5 : como arr[j] <= pivot, i == 2 y arr[i] == arr[j]
arr[] = {9,5,8,19,12,13,7,4,21,2,6,11}

j = 6 : se queda igual porque arr[j] > pivot

j = 7 :  como arr[j] <= pivot, i == 3 y arr[i] == arr[j]
arr[] = {9,5,8,4,12,13,7,19,21,2,6,11}

j = 8 : se queda igual porque arr[j] > pivot

j = 9 : como arr[j] <= pivot, i == 4 y arr[i] == arr[j]
arr[] = {9,5,8,4,2,13,7,19,21,12,6,11}

j = 10 : como arr[j] <= pivot, i == 5 y arr[i] == arr[j]
arr[] = {9,5,8,4,2,6,7,19,21,12,13,11}

j = high -1 
then arr[i+1] == pivot 
arr[] = {9,5,8,4,2,6,7,11,21,12,13,19}
ahora todos los elementos menores a 11 estan a la izquierda y los mayores a la derecha 


No se usa heapsort porque en caso de haber cambios inescesarios igual los hace. Por otro lado quicksort se salta estos cambios. 
Esto quiere decir que quicksort es superior porque no pierde el tiempo cambiando numeros que ya estan en orden. 


## Problema 3

```python
def partition(arr,j,i):
   pivot = arr[j]

   low = j+1
   high = i
   done = False
   while not done:

       while low <= high and arr[low] <= pivot:
           low = low + 1

       while arr[high] >= pivot and high >= low:
           high = high -1

       if high < low:
           done = True
       else:
           temp = arr[low]
           arr[low] = arr[high]
           arr[high] = temp

   temp = arr[j]
   arr[j] = arr[high]
   arr[high] = temp
   return high


def quickSort(arr,low,high):
    if low < high:
 
        pi = partition(arr,low,high)
        quickSort(arr, low, pi-1)
        quickSort(arr, pi+1, high)
 

arr = [5,10,15,32,55,21,40,2,3,76,89,28,9,7]
n = len(arr)
quickSort(arr,0,n-1)
print ("Sorted array is:")
for i in range(n):
    print ("%d" %arr[i]),


```
