# Sort

**정렬?** 물건을 크기 순으로 오름차순 또는 내림차순으로 나열하는 것이다.

- 정렬의 대상을 record(레코드)라고 한다.
- 레코드는 필드(field)의 단위로 나뉘어진다.

→ 정렬이란 결국 레코드들을 키 값의 순서로 재배열하는 것이다.

### 선택 정렬

---

데이터 중 크기를 비교하여 교환할 원소를 선택 후 자리에 교환하는 방식이다.

- 자연어
  ```c
  1. 인덱스 중 가장 작은 수가 있는 인덱스 찾기
  2. 가장 작은 수와 0번째 인덱스의 수 교환
  3. 0번째 인덱스 정렬 완료
  4. n-1 번 반복 (0부터 n-2까지)
  ```
- 의사코드
  ```c
  selection_sort(A, n) :

  for i ← 0 to n-2 do
     least ← A[i], A[i+1], ... , A[n-1] 중에 가장 작은 값의 인덱스;
     A[i]와 A[least]를 교환(이동);
     i++;
  ```
- 알고리즘

  ```c
  #include<stdio.h>
  #include<stdlib.h>
  #define MAX_SIZE 10

  int arr[MAX_SIZE];
  void selection_sort(int arr[], int n) {
  	int least, tmp;
   // 선택정렬 알고리즘
  	for(int i=0;i<n-1;i++) {
  		least = i;
  		for(int j=i+1;j<n;j++){
  			if(arr[least] > arr[j]) least = j;
  		}
  	tmp = arr[i];
  	arr[i] = arr[least];
  	arr[least] = tmp;
  	}
  }
  int main() {
  	srand(time(NULL)); // 씨드 변경 함수
  	int n = MAX_SIZE;
  	for (int i = 0; i < n; i++) {
  		arr[i] = rand() % 100; // 랜덤값 반환 함수
  	}
  	selection_sort(arr, n);
  	//정렬된 배열 출력
  	for(int i=0;i< n;i++){
  		printf("%d ", arr[i]);
  }
    return 0;
  }
  ```

- 장점 : 자료 이동 횟수가 미리 결정된다.
- 단점 : 정렬 시간이 오래 걸린다.
- 빅오 : O(n^)

### 삽입 정렬

---

정렬되어 있는 부분집합에 정렬할 새로운 원소의 위치를 찾아 삽입하는 방식이다.

- 자연어
  ```c
  1. 삽입할 데이터를 배열의 마지막 인덱스부터 비교하며 위치 찾기
  2. 위치를 찾을 때 삽입할 원소가 더 작다면 앞으로 이동하며 위치를 찾기
  3. n-1번 반복
  ```
- 의사코드
  ```c
  insertion_sort(A, n) :

  for i ← 1 to n-1 do
     key ← A[i];
     j ← i-1;
     while j>=0 and A[j] > key do
        A[j+1] ← A[j];
        j ← j-1;
     A[j+1] ← key;
  ```
- 알고리즘

  ```c
  #include<stdio.h>
  #include<stdlib.h>
  #define MAX_SIZE 10

  int arr[MAX_SIZE];
  void insertion_sort(int arr[], int n) {
  	int key,i,j;
  	for(i=1;i<MAX_SIZE;i++){
  			key = arr[i];
  			for(j = i-1;j>=0 && arr[j]>key;j--) arr[j+1] = arr[j];
  			arr[j+1] = key;
  	}
  }

  int main() {
  	srand(time(NULL));
  	int n = MAX_SIZE;
  	for (int i = 0; i < n; i++) {
  		arr[i] = rand() % 100;
  	}

  	insertion_sort(arr, n);

  	//정렬된 배열 출력
  	for(int i=0;i<n;i++) {
  		printf("%d ", arr[i]);
  	}
    return 0;
  }
  ```

- 장점 : 최선의 경우 시간이 매우 적게 걸린다.
- 단점 : 반대의 경우는 시간이 매우 오래 걸린다.

### 버블 정렬

---

서로 인접한 데이터들을 비교하며 각 단계마다 가장 큰 데이터를 뒤로 보내며 정렬하는 방식이다.

- 자연어
  ```c
  1. 첫 번째 원소부터 마지막 원소까지 인접한 데이터를 비교
  2. 가장 오른쪽(가장 큰 원소)가 정렬됨
  3. 그 다음 큰 원소가 오른쪽-1에 정렬됨
  4. n-1번 반복
  ```
- 의사코드
  ```c
  Bubble_sort(A, n) :

  for i ← n-1 to 1 do
     for j ← 0 to i-1 do
        j와 j+1번째의 요소가 크기순이 아니면 교환
        j++;
     i--;
  ```
- 알고리즘

  ```c
  #include<stdio.h>
  #include<stdlib.h>
  #define MAX_SIZE 10

  int arr[MAX_SIZE];
  void Bubble_sort(int arr[], int n) {
    int tmp;
    for(int i=n-1;i>=1;i--){
      for(int j=0;j<i-1;j++){
        if(arr[j] > arr[j+1]) {
          tmp = arr[j];
          arr[j] = arr[j+1];
          arr[j+1] = tmp;
        }
      }
    }

  }

  int main() {
  	srand(time(NULL));
  	int n = MAX_SIZE;
  	for (int i = 0; i < n; i++) {
  		arr[i] = rand() % 100;
  	}

  	Bubble_sort(arr, n);

  	//정렬된 배열 출력
    for(int i=0;i<n;i++){
      printf("%d ",arr[i]);
    }
    return 0;
  }
  ```

- 장점 : 구현이 간단하고 단순하다.
- 단점 : 정렬 시간이 오래 걸린다.

### 퀵 정렬

---

평균적으로 매우 빠른 속도를 자랑하는 방식이다.

- 자연어
  ```c
  - quick_sort 함수
  1. 피벗을 기준으로 왼쪽 리스트와 오른쪽 리스트로 나누기 위해 partition() 함수를 호출
  2. 왼쪽 리스트와 오른쪽 리스트 각각 quick_sort() 함수를 호출
  ```
  ```c
  - partition 함수
  1. 피벗을 정하여 왼쪽부터 시작하는 low와 오른쪽부터 시작하는 high 변수를 선언
  2. low 변수는 arr[low] 값이 피벗보다 작으면 계속 증가
  3. high 변수는 arr[high] 값이 피벗보다 크면 계속 감소
  4. high가 low보다 크면 arr[low]와 arr[high] 값을 바꾸어주고 2~4번을 반복
  5. high가 low보다 작으면 피벗과 arr[high] 값을 교환하여 피벗이 기준이 되게 힘
  ```
- 알고리즘

  ```c
  #include<stdio.h>
  #include<stdlib.h>
  #define MAX_SIZE 10
  int arr[MAX_SIZE];
  int partition(int left, int right) {
  	int pivot = arr[left];
  	int low = left + 1;
  	int high = right;
  	int temp;
  	do {
  		while (arr[low] < pivot) {
  			low++;
  		}
  		while (arr[high] > pivot) {
  			high--;
  		}
  		if (low < high) {
  			// 값 교환
  			temp = arr[low];
  			arr[low] = arr[high];
  			arr[high] = temp;
  		}
  	} while (low < high);

  	// 값 교환(어떤 값들을 바꿔줘야할까요?)
  	temp = arr[left];
  	arr[left] = arr[high];
  	arr[high] = pivot;
  	return high;
  }

  void quick_sort(int left, int right) {
  	// left는 정렬해야 할 배열의 첫 인덱스 값, right는 마지막 인덱스 값
  	if (left < right) {
  		int q = partition(left, right); // partition함수는 피봇의 위치(인덱스)를 반환
  		quick_sort(left, q - 1);
  		quick_sort(q + 1, right); // 오른쪽 리스트 매개변수는?
  	}
  }

  int main() {
  	srand(time(NULL));
  	int n = MAX_SIZE;
  	for (int i = 0; i < n; i++)
  		arr[i] = rand() % 100;

  	quick_sort(0, n - 1);
  	for (int i = 0; i < n; i++)
  		printf("%d ", arr[i]);
  	return 0;
  }
  ```

- 장점 : 속도가 빠르고 추가 메모리 공간을 필요로 하지 않는다.
- 단점 : 최악의 경우에는 리스트가 불균형하게 나뉘어진다.
