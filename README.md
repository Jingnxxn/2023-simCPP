## 2023-simCPP
==============
#오퍼레이터 오버로딩 실습 과제
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
```ruby
----------------------
