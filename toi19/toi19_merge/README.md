# TOI19 merge

[🎉 solution.cpp](./toi19_merge.cpp)

<img width="350" alt="image" src="https://github.com/krist7599555/toi/assets/19445033/23655709-695a-4a82-8d02-c39f97ccf9ac">

Binary Search โดยเช็คคำตอบแต่ละครั้งด้วย Binary Search บน Quicksum

ข้อนี้จะมี จะใช้ `X[]` และ `Y[]` มาแล้วหาลำดับที่ `n-th`

ถ้าโจทย์ถามแค่ว่า ให้ `int arr[]` มาหาว่า idx ที่เท่าไหร่ที่มีผลรวม `arr[1..idx] < val` ก็หาได้โดยการทำ quicksum ก่อน 1 รอบ แล้ว binary search บนนั้น

สำหรับโจทย์คราวนี้ก็แค่เปลี่ยนจากการใช้ `idx` เป็นการใช้ค่า `position` ที่ให้มาตอนแรกแทน

แต่ข้อนี้สมการยากขึ้นไปอีกเพราะ `Y[].position` จะเปลี่ยนไปตามแต่ละคำถามกลายเป็น `Y[].position * alpha + beta` แต่สมการ `y = ax + b` เป็นสมการ linear เพราะงั้นความสามารถในการ binary search ก็ยังใช้ได้อยู่ดี และหา inverse ได้ด้วย `y = ax + b กลับสมการ x = (y - b) / a`

สรุปเป็นสมการสั้นๆคือ

```cpp
binary_search([-infinity, infinity]) { |val|
  int count_x = binary_search(X[], val)
  int count_y = binary_search(Y[], (val / beta) - alpha)
  check(count_x + count_y < n_th)?
}
```
