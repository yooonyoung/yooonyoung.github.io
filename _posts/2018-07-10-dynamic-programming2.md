---

layout: post

title: "백준 1463번 문제 : 1로 만들기"

---
문제 링크 : [백준 1463번 : 1로 만들기](https://www.acmicpc.net/problem/1463)<br><br>
이 문제는 어떤 수를 3가지 연산(3으로 나누기, 2로 나누기, 1을 빼기)을 사용하여 1로 만드는 가장 적은 연산 횟수를 출력하는 문제이다. 같은 수라도 1로 만들 수 있는 경우의 수가 여러 개인 경우가 있다. 예를 들어 주어진 수가 10일 경우


- 10->5->4->2->1
- 10->9->3->1



이렇게 두 가지 경우의 수가 나올 수 있는데, 이 중 2번째 경로의 연산 횟수인 3을 출력해야 한다.<br>
Dynamic Programming(DP)를 이용하여 풀 수 있는 문제이고, 나는 Top-down 방식 [^1] 을 사용하여 풀었다.<br>
주어진 수 N이 1인 경우를 제외하고, 나머지는 N-1, N/2, N/3 을 인수로 하는 재귀함수 호출을 통해 구할 수 있다.

- **3으로 나누어 떨어지는 경우 : d[N] = d[N/3] + 1**
- **2로 나누어 떨어지는 경우 : d[N] = d[N/2] + 1**
- **둘 다 안되는 경우 : d[N] = d[N-1] + 1**

일단 1을 빼는 연산을 진행하여 d[N]에 저장하고, 2로 나누는 연산 또는 3으로 나누는 연산을 진행했을 때의 값과 비교하여 더 작은 값을 d[N]에 저장하는 방식으로 구현했다.



소스코드(C++)
```c++
#include <iostream>
#include <algorithm>
using namespace std;

int d[1000001];

int divToOne(int n) {
	int temp;
	if (n == 1) { //n이 1일 때 끝
		return 0;
	}
	if (d[n] > 0) { // 이미 구한 값인지 확인
		return d[n];
	}

	d[n] = divToOne(n - 1) + 1; // 먼저 1을 빼는 연산 수행

	if (n % 2 == 0) { // 2로 나누는 연산
		temp = divToOne(n / 2) + 1;
		d[n] = min(d[n], temp); // 연산 횟수가 더 적은 것으로 결정
	}
	else if (n % 3 == 0) { // 3으로 나누는 연산
		temp = divToOne(n / 3) + 1;
		d[n] = min(d[n], temp);
	}
	return d[n];
}
int main() {
	int N;
	cin >> N;
	cout << divToOne(N);
}
```

[^1]: 큰 문제를 점점 작게 만들어나가는 방식(보통 재귀함수)



