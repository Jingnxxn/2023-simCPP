## 2023-simCPP
-------------
오퍼레이터 오버로딩 실습 과제
-------------
```ruby
#include <iostream>
using namespace std;
class CPnt{
  int w, h;
public:
  CPnt(int _w, int _h){ w=_w; h=_h; }
  CPnt(){w=0;h=0;}
  void Pr ()  { cout << w*h << '\n'; }

  void PrPt ()  { cout << w << ' ' << h << '\n'; }
  CPnt operator+(CPnt r){
      CPnt t;
      t.w = w + r.w;
      t.h = h + r.h;
      return(t);
  }

};
int main ()
{
  CPnt p1(1, 1), p2(2,2), p3;

  p3 = p1.operator+(p2);
  p3.PrPt ();
  p3.Pr();
  return 0;

}
```
----------------------------
OOP를 표현할 수 있는 예제를 만드시오.
----------------------------
도형 클래스 CPoly로부터 두 정수를 상속 받고, 면적 계산하는 과정을 함수 오버라이딩을 통해 다형성(Polymorphism) 을 구현하고 사각형의 가로 세로를 변수로 가지는 클래스를 정의하고, 가로와 세로 값을 출력하는 << 오퍼레이터를 오버로딩 하시오. 
"+ 사각형의 넓이와 둘레를 구해보았습니다."
```ruby
#include <iostream>
using namespace std;

class CPoly { 
protected:
    int w, h;  // 상속
public:
    CPoly(int _w, int _h) {
        w = _w;
        h = _h;
    }
    virtual int Area() = 0; // 가상 함수를 사용하여 다형성 구현
};

class CRect : public CPoly { 
public:
    CRect(int _w, int _h) : CPoly(_w, _h) {}  // 상속받은 변수 초기화
    int Area() override { // 면적 계산 함수 오버라이딩
        return w * h;
    }
    int Perimeter() { // 사각형의 둘레를 계산하는 함수
        return 2 * (w + h);
    }
    friend ostream& operator<<(ostream& os, CRect& r) { // << 연산자 오버로딩
        os << "가로: " << r.w << ", 세로: " << r.h;
        return os;
    }
};

int main() {
    CRect r(5, 10); 
    cout << r << endl; // 가로와 세로 값을 출력
    cout << "면적: " << r.Area() << endl; // 면적 계산 결과 출력
    cout << "둘레: " << r.Perimeter() << endl; // 둘레 계산 결과 출력
    return 0;
}
```
----------------------------
전위 ++ 연산자 오버로딩, 후위 ++ 연산자 오버로딩의 예를 만들고 설명을 적으시오.
----------------------------

```ruby
#include <iostream>
using namespace std;
class Counter {
    int count;
public:
    Counter() {
        count = 0;
    }
    void operator++() {  // 전위 ++ 연산자 오버로딩
        count++;
    }
    void operator++(int) {  // 후위 ++ 연산자 오버로딩
        count++;
    }
    void display() {
        cout << "Count: " << count << endl;
    }
};
int main() {
    Counter c1, c2;
    ++c1;  // 전위 ++ 연산자 사용
    c1.display();  // 출력: Count: 1
    c2++;  // 후위 ++ 연산자 사용
    c2.display();  // 출력: Count: 1
    return 0;
}
```
전위 ++ 연산자와 후위 ++ 연산자는 C++에서 매우 중요한 연산자 중 하나이다. 전위 ++ 연산자는 변수를 1 증가시키고, 그 값을 반환하는 연산자이다. 후위 ++ 연산자는 변수를 1 증가시키지만, 증가하기 전의 값을 반환하는 연산자이다. 위 코드에서는 Counter 클래스를 정의하고, 전위 ++ 연산자와 후위 ++ 연산자를 오버로딩하여 사용하였다. 전위 ++ 연산자는 함수 이름 앞에 ++를 붙이고, 후위 ++ 연산자는 함수 이름 뒤에 ++를 붙이고 int 타입의 매개변수를 추가한다. 후위 ++ 연산자의 경우 매개변수는 오버로딩된 함수를 구별하기 위한 것으로, 실제로 사용되지는 않는다.

-----------------------------------
##STL로 stack을 5개 만들고, 50, 40, 30, 20, 10을 저장하고, 출력 하는 것을 iterator를 활용하시오.
-----------------------------------

```ruby
#include <iostream>
#include <stack>

using namespace std;

int main() {
  // 5개의 스택 생성
  stack<int> s1, s2, s3, s4, s5;

  // 스택에 데이터 추가
  s1.push(50);
  s1.push(40);
  s1.push(30);
  s1.push(20);
  s1.push(10);

  s2.push(50);
  s2.push(40);
  s2.push(30);
  s2.push(20);
  s2.push(10);

  s3.push(50);
  s3.push(40);
  s3.push(30);
  s3.push(20);
  s3.push(10);

  s4.push(50);
  s4.push(40);
  s4.push(30);
  s4.push(20);
  s4.push(10);

  s5.push(50);
  s5.push(40);
  s5.push(30);
  s5.push(20);
  s5.push(10);

  // 스택의 모든 요소 출력
  stack<int> stacks[] = {s1, s2, s3, s4, s5};
  for (int i = 0; i < 5; i++) {
    stack<int> s = stacks[i];
    cout << "Stack " << i+1 << ": ";
    while (!s.empty()) {
      cout << s.top() << " ";
      s.pop();
    }
    cout << endl;
  }

  return 0;
}
```

---
##ChatGPT를 활용하여 STL의 자료구조와 알고리즘을 분류하고, 자료구조 예제 1개와 알고리즘 1개를 만들고 토의를 하시오.
---

```ruby
자료구조 예제: vector
c++
Copy code
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<int> v;

    v.push_back(10);
    v.push_back(20);
    v.push_back(30);

    cout << "vector의 크기: " << v.size() << endl;

    for (int i = 0; i < v.size(); ++i) {
        cout << v[i] << " ";
    }

    return 0;
}
```
이 코드에서는 vector를 생성하고, push_back() 함수를 이용하여 10, 20, 30을 순서대로 추가한다. 그리고 size() 함수를 이용하여 vector의 크기를 출력하고, for문을 이용하여 vector에 저장된 값을 출력한다.

```ruby
알고리즘 예제: sort
c++
Copy code
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main() {
    vector<int> v = {30, 10, 50, 20, 40};

    sort(v.begin(), v.end());

    for (int i = 0; i < v.size(); ++i) {
        cout << v[i] << " ";
    }

    return 0;
}
이 코드에서는 vector를 생성하고, 초기값으로 30, 10, 50, 20, 40을 저장한다. 그리고 sort() 함수를 이용하여 vector에 저장된 값을 오름차순으로 정렬한다. 마지막으로 for문을 이용하여 vector에 저장된 값을 출력한다.
```
------------------------------------------
##C++의 주요 특징 20가지의 제목을 적어 보고 토의 하시오.
-----------------------------------------
객체지향 프로그래밍
/일반화 프로그래밍 (Generic Programming)
/메모리 관리
/표준 라이브러리
/다중 상속
/예외 처리 (Exception Handling)
/인라인 함수 (Inline Functions)
/포인터 및 참조
/템플릿
/네임스페이스
/const 키워드
/함수 오버로딩
/연산자 오버로딩
/표준 입출력 스트림
/스마트 포인터 (Smart Pointers)
/캡슐화
/가상 함수 (Virtual Functions)
/다형성 (Polymorphism)
/런타임 다형성 (Runtime Polymorphism)
/컴파일 타임 다형성 (Compile-time Polymorphism)
