<!-- @codegen_problem begin -->
# TOI19 energy - เติมพลังงาน (Energy)

[🏠 รวมเฉลย TOI19](../)

[💎 problem.pdf](./toi19_energy.pdf)

[🎉 solution.cpp](./toi19_energy.cpp)

<img width="700" src="https://github.com/krist7599555/toi/assets/19445033/1940644a-8b27-4212-9c61-8190b575be78" />
<!-- @codegen_problem end -->

ทำ Matrix Chain Multiplication ตรงๆนี้แหละ แต่เราต้องการการแบ่งที่ชั้นที่ `K` เราก็ทำ Matrix Chain Multiplication ทั้งหมด `K` ครั้ง โดนที่แต่ละครั้งให้ใช้ค่าจากชั้นก่อนเท่านั้น

```haskell
dp(hi, arr[l..r]) => int # วิธีทั้งหมดที่ใช้แบ่งช่วง arr[l..r] ได้ถึง hi ชั้น
dp( 0, arr[l..r]) => 1   # ชั้นแรกไม่ต้องเปรี่ยบเทียบแบ่งกับใคร ได้ 1 วิธีเสมอ
dp(hi, arr[l..r]) => sum l..r { |pivot|
  where diff(sum(arr[l..pivot]), sum(arr[pivot..r])) < max_diff
  dp(hi-1, arr[l..pivot]) + dp(hi-1, arr[pivot..r])
}
```
