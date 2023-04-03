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
##1.도형 클래스 CPoly로부터 두 정수를 상속 받고, 면적 계산하는 과정을 함수 오버라이딩을 통해 다형성(Polymorphism) 을 구현하시오. 

 

##2.사각형의 가로 세로를 변수로 가지는 클래스를 정의하고, 가로와 세로 값을 출력하는 << 오퍼레이터를 오버로딩 하시오.
