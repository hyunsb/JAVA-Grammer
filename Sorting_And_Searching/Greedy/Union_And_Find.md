## 친구인가? (Disjoint-Set : Union&Find)

> 오늘은 새 학기 새로운 반에서 처음 시작하는 날이다.
현수네 반 학생은 N명이다. 현수는 각 학생들의 친구관계를 알고 싶다.
모든 학생은 1부터 N까지 번호가 부여되어 있고,
현수에게는 각각 두 명의 학생은 친구 관계 가 번호로 표현된 숫자쌍이 주어진다.
만약 (1, 2), (2, 3), (3, 4)의 숫자쌍이 주어지면 1번 학 생과 2번 학생이 친구이고,
2번 학생과 3번 학생이 친구, 3번 학생과 4번 학생이 친구이다.
그리고 1번 학생과 4번 학생은 2번과 3번을 통해서 친구관계가 된다.
학생의 친구관계를 나타내는 숫자쌍이 주어지면
특정 두 명이 친구인지를 판별하는 프로그램 을 작성하세요.
두 학생이 친구이면 “YES"이고, 아니면 ”NO"를 출력한다.
>

---

### 입력값

첫 번째 줄에 반 학생수인 자연수 N(1<=N<=1,000)과 숫자쌍의 개수인 M(1<=M<=3,000)이
주어지고, 다음 M개의 줄에 걸쳐 숫자쌍이 주어진다.
마지막 줄에는 두 학생이 친구인지 확인하는 숫자쌍이 주어진다.

### 출력값

첫 번째 줄에 “YES"또는 "NO"를 출력한다.

### 입력예제

9 7
1 2
2 3
3 4
1 5
6 7
7 8
8 9
3 8

친구 그룹의 번호를 저장하는 배열을 생성하고 그룹 번호를 저장하여

입력 값으로 받아온 두 학생이 친구 사이인지 판단한다.

`friendGroupNumber` :친구 그룹의 번호를 저장하는 배열

`Int Find(int student)` : 친구 그룹의 번호를 최신화하여 반환

`Void Union(int studentA, int studentB)` : 파라매터로 받아온 학생의 친구 그룹을 통합

`Boolean isFriends(int studentA, int studentB)` : 두 학생이 친구인지 판단하여 반환

```java
static int[] friendGroupNumber;
```

```java
// 친구 트리의 번호를 찾는 메서드
static int Find(int student){
    if(friendGroupNumber[student] == student)
        return friendGroupNumber[student];
    else return friendGroupNumber[student] = Find(friendGroupNumber[student]);
}
```

```java
// 친구 관계를 맺어 친구 트리 배열에 저장하는 메서드
static void Union(int studentA, int studentB){
    int studentGroupA = Find(studentA);
    int studentGroupB = Find(studentB);

    if(studentGroupA != studentGroupB)
        friendGroupNumber[studentGroupA] = studentGroupB;
}
```

```java
static boolean isFriends(int studentA, int studentB){
    return Find(studentA) == Find(studentB);
}
```

```java
public static void main(String[] args) {
    _6_Is_Friend_Disjoint_Set_Practice main = new _6_Is_Friend_Disjoint_Set_Practice();
    Scanner sc = new Scanner(System.in);

    int n = sc.nextInt();
    int m = sc.nextInt();

    friendGroupNumber = new int[n+1];
    for(int i=1; i<=n; i++)
        friendGroupNumber[i] = i;

    for(int i=0; i<m; i++)
        Union(sc.nextInt(), sc.nextInt());

    if(isFriends(sc.nextInt(), sc.nextInt()))
        System.out.println("YES");
    else System.out.println("NO");
}

```

---

### friendGroupNumber 상태변화

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3cbf895b-c98f-4c3a-9943-4cc8df2dfbcd/Untitled.png)

---

### 전체 소스코드

```java
class _6_Is_Friend_Disjoint_Set_Practice{
    static int[] friendGroupNumber;

    // 친구 트리의 번호를 찾는 메서드
    static int Find(int student){
        if(friendGroupNumber[student] == student)
            return friendGroupNumber[student];
        else return friendGroupNumber[student] = Find(friendGroupNumber[student]);
    }

    // 친구 관계를 맺어 친구 트리 배열에 저장하는 메서드
    static void Union(int studentA, int studentB){
        int studentGroupA = Find(studentA);
        int studentGroupB = Find(studentB);

        if(studentGroupA != studentGroupB)
            friendGroupNumber[studentGroupA] = studentGroupB;
    }

    static boolean isFriends(int studentA, int studentB){
        return Find(studentA) == Find(studentB);
    }

    public static void main(String[] args) {
        _6_Is_Friend_Disjoint_Set_Practice main 
						= new _6_Is_Friend_Disjoint_Set_Practice();
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int m = sc.nextInt();

        friendGroupNumber = new int[n+1];
        for(int i=1; i<=n; i++)
            friendGroupNumber[i] = i;

        for(int i=0; i<m; i++)
            Union(sc.nextInt(), sc.nextInt());

        if(isFriends(sc.nextInt(), sc.nextInt()))
            System.out.println("YES");
        else System.out.println("NO");
    }
}
```