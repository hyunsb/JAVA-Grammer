# 결정 알고리즘 (Decision Algorithm)
이분 검색(Binary Search) 기반으로 주어진 조건에서의 최대 혹은 최소값을 구하는 알고리즘이다.

## 예시 문제

### ✏️설명

> 지니레코드에서는 불세출의 가수 조영필의 라이브 동영상을 DVD로 만들어 판매하려 한다.
DVD에는 총 N개의 곡이 들어가는데, DVD에 녹화할 때에는 라이브에서의 순서가 그대로 유지되어야 한다.
순서가 바뀌는 것을 우리의 가수 조영필씨가 매우 싫어한다. 즉, 1번 노래와 5번 노래를 같은 DVD에 녹화하기 위해서는 1번과 5번 사이의 모든 노래도 같은 DVD에 녹화해야 한다.
또한 한 노래를 쪼개서 두 개의 DVD에 녹화하면 안된다. 지니레코드 입장에서는 이 DVD가 팔릴 것인지 확신할 수 없기 때문에 이 사업에 낭비되는 DVD를 가급적 줄이려고 한다.
고민 끝에 지니레코드는 M개의 DVD에 모든 동영상을 녹화하기로 하였다. 이 때 DVD의 크기(녹화 가능한 길이)를 최소로 하려고 한다.
그리고 M개의 DVD는 모두 같은 크기여야 제조원가가 적게 들기 때문에 꼭 같은 크기로 해야 한다.
>

### ✏️입력

> 첫째 줄에 자연수 N(1≤N≤1,000), M(1≤M≤N)이 주어진다.
>
>
> 다음 줄에는 조영필이 라이브에서 부른 순서대로 부른 곡의 길이가 분 단위로(자연수) 주어진다.
>
> 부른 곡의 길이는 10,000분을 넘지 않는다고 가정한다.
>

### ✏️출력

> 첫 번째 줄부터 DVD의 최소 용량 크기를 출력하시오.
>

## ✅ JAVA Code

```java
public int solution(int n, int m, int[] musicLength){
        int lt = Arrays.stream(musicLength).max().getAsInt();
        int rt = Arrays.stream(musicLength).sum();
        int answer = 0;

        while (lt <= rt){
            int mid = (lt + rt) / 2;
            if (count(musicLength, mid) <= m){
                answer = mid;
                rt = mid - 1;
            }
            else lt = mid + 1;
        }
        return answer;
    }
```

lt (left): 라이브에서 부른 곡의 길이 중 최대 값 (음악을 쪼개어 담을 수 있는 최소 값)
rt (right): 라이브에서 부른 곡의 길이의 합 (음악을 쪼개어 담을 수 있는 최대 값)

// 음악파일을 라이브 음악 만큼의 수로 쪼개어 저장한다고 가정할 시 lt가 DVD 최소 용량,
// 음악파일을 1개로 쪼개어(쪼개지 않음) 저장한다고 가정할 시 rt가 DVD 최소 용량이 된다.

기본적으로 이분 검색 알고리즘에 기반하여 탐색을 진행하는데 추가 조건(DVD 수)이 발생한다.

```java
public int count(int[] arr, int capacity){
    int count = 1;
    int sum = 0;
    for(int i : arr){
        if(sum + i > capacity) {
            count += 1;
            sum = i;
        }
        else sum += i;
    }
    return count;
}
```

배열과 DVD의 길이를 파라매터로 전달받는 메서드를 생성한다.

노래 길이 배열을 탐색하며 모든 노래를 DVD 길이에 맞추어 저장하려면 몇 개의 DVD가 생성되어야 하는지 카운팅한다.

```java
public static void main(String[] args) {
        _9_Decision_Algorithm_Music_Video T = new _9_Decision_Algorithm_Music_Video();
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int m = sc.nextInt();
        int[] musicLength = new int[n];
        for(int i=0; i<n; i++) musicLength[i] = sc.nextInt();

        System.out.println(T.solution(n, m, musicLength));
    }
```