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
##1.도형 클래스 CPoly로부터 두 정수를 상속 받고, 면적 계산하는 과정을 함수 오버라이딩을 통해 다형성(Polymorphism) 을 구현하고 사각형의 가로 세로를 변수로 가지는 클래스를 정의하고, 가로와 세로 값을 출력하는 << 오퍼레이터를 오버로딩 하시오.
----------------------------
```ruby
#include <iostream>
using namespace std;

class CPoly { 
protected:
    int w, h; // 상속
public:
    CPoly(int _w, int _h) {
        w = _w;
        h = _h;
    }
    virtual int Area() = 0;  // 가상 함수를 사용하여 다형성 구현
};

class CRect : public CPoly { 
public:
    CRect(int _w, int _h) : CPoly(_w, _h) {} // 상속받은 변수 초기화
    int Area() override { // 면적 계산 함수 오버라이딩
        return w * h;
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
    return 0;
}
------------------------------------------------------
