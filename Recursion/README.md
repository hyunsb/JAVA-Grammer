## 재귀함수(Recursion)

---

함수가 직접 또는 간접적으로 자기 자신을 호출하는 프로세스를 말합니다.

재귀함수의 종료지점을 유의하여 구현을 진행하여야 스택오버플로우가 발생하지 않으니 주의하여 구현해야합니다.

재귀함수는 스택프레임을 사용합니다.

<aside>
💡 스택프레임은 모든 함수의 호출과 함께 할당되며, 함수의 호출이 완료되면 완전 소멸한다.

</aside>

---

아래는 `자연수 N이 입력되면 재귀함수를 이용하여 1부터 N까지 출력하는 프로그램` 을 구현한 것입니다.

### ✅JAVA

```java
public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        DFS(sc.nextInt());
}

public static void DFS(int n){
    if (n==0) return;
    else {
        DFS(n-1);
        System.out.println(n);
    }
}
```

1. 입력값 `N`이 `0`이 될 때까지  `N-1`을 매개변수로 받는 자기 자신을 반복적으로 호출합니다.
2. 입력값이 `0` 이 되었을 시 `return` 을 해주어, 호출되었던 DFS 함수의 출력문이 실행됩니다.
3. 스택의 출력 순서대로 1, 2, … , n 을 출력하며 프로그램을 종료하고, 스택프레임은 소멸됩니다.

---

아래는 `입력받은 10진수를 2진수로 출력하는 프로그램`을 재귀함수로 구현한 것입니다.

### ✅JAVA

```java
public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);

    T.DFS(sc.nextInt());
}

public void DFS(int n){
    if(n==0) return;
    else {
        DFS(n/2);
        System.out.print(n%2);
    }
}
```

1. 입력값 `N`이 `0`이 될 때까지 `N/2`를 매개변수로 받는 자기 자신을 반복적으로 호출합니다.
2. 입력값이 `0` 이 되었을 시 `return` 을 해주어, 호출되었던 DFS 함수의 출력문이 실행됩니다.
3. 스택의 출력 순서대로 `N%2` 값인 1 or 0 을 출력하며 프로그램을 종료합니다.