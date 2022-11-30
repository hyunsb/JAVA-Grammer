# 이분 검색 (Binary Search)
정렬된 배열 또는 리스트에 적합한 고속 탐색 방법이다.

![image.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8b68cdbd-61d0-4b0d-bfad-0d8ab22cd77d/image.gif)

## ⚙ Process
1. 배열 혹은 리스트를 정렬한다.
2. left = 배열의 첫번째 인덱스,  right = 마지막 인덱스를 각각 저장한다.
3. mid 값을 구한다. (left + right) / 2
4. mid 인덱스와 탐색 값을 비교하여 rt 혹은 lt 값을 변경한다.

## ✅ JAVA Code

```java
// n(배열의 길이), m(탐색 값), num(탐색 대상 배열)
public int binarySearch(int n, int key, int[] num){
        int answer = 0;

        Arrays.sort(num);
        int lt = 0, rt = num.length-1;
        while (lt <= rt){
            int mid = (lt + rt) / 2;

            if(num[mid] == key) {
                answer = mid + 1;
                break;
            }

            if(num[mid] > key) rt = mid - 1;
            else lt = mid + 1;
        }

        return answer;
    }
```

**key > mid** :  구하고자 하는 값이 중간값보다 높다면 lt **를 mid +1**로 만들어 줌 (왼쪽 반을 버림)

**key < mid** : 구하고자하는 값이 중간값 보다 낮다면 rt **를 mid-1**로 만들어 줌 (오른쪽 반을 버림)

**key == mid** : 구하고자 하는 값을 찾음 중간값 리턴