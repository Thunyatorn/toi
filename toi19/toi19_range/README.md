# TOI19 range

[🎉 solution.cpp](./toi19_range.cpp)

<img width="350" alt="image" src="https://github.com/krist7599555/toi/assets/19445033/84d7f1c6-da5e-47ca-a795-7161b801600e">

## Observation 1 Segment Tree + Sort

คือข้อนี้มันมี solution อื่นที่ใช้ fenwick แหละ แต่ต้องกลับแกน มันจะนึกภาพออกยาก เพราะฉะนั้นหัดเขียน segment tree เอาหน่อยละกัน 🙄

ข้อนี้ถ้าใช้ segment tree ก็แก้ตรงๆว่า

`size(node {l, r}) = max(node { >=l, <=r }) + 1`

แต่เราต้องการหานิยามการเช็คไวๆว่า `[l1, r1]` กับ `[l2, r2]` เป็น subset ก้นหรือเปล่า ถ้าเก็บทั้ง l1, l2, r1, r2 มันจะยากไป เราเลยใช้การ sort เอา แล้ว query ย้อนกลับแทน

```text
         อยู่ตรงนี้ สนใจที่ช่วงปัจจุบัน [l1, r1]
         v
[l       r]

ค่าทั้งหมดในนี้สามารถเป็นลูกได้หมด [l2, r2]
[l,      r] <= จะไม่เกิดเคสนี้ที่ l1 == l2 && r1 == r2
[l,    r]
[l,  r]
[l,r]
  [l,    r] <= แต่จะเกิดเคสนี้คือ l1 < l2 && r1 == r2
               เราเลยต้องเรียง จาก l มากไปน้อย ถ้า r เท่ากัน
  [l,  r]
  [l,r]
     [l, r] <= แต่จะเกิดเคสนี้คือ l1 < l2 && r1 == r2
     [l,r]
      [l,r] <= แต่จะเกิดเคสนี้คือ l1 < l2 && r1 == r2
```

จากที่เราทำเรียงตาม `r` อยู่แล้วจึงไม่มีค่าไหนเลยที่ `>r` ปัจจุบัน

เราจึงนิยามตำแหน่งของช่วง interval ไว้แค่ที่ตำแหน่ง `l` ก็พอ เพราะถ้ามีช่วงไหนที่ `l2<l1` ก็แปลว่า `[l2, r2]` สามารถเป็นลูกของ `[l1, r1]` ได้

## Observation 2 Compress Index

แล้วก็มี trick อีกนิดนึงคือ ค่าช่วงมันเยอะมากๆ `1e9` ไม่สามารถจอง array ขนาดนั้นได้ แต่ข้อมูลมีแค่ `400,000` ตัว เลยสามารถ compress index ใหม่ได้ทำได้โดย

- sort ตำแหน่งทั้งหมด
- ทำให้ unique
- แล้วก็วน for ใส่เลขใหม่
- แทนที่ตำแหน่งเก่า ด้วยตำแหน่ง idx ที่เป็นค่านั้น

```cpp
std::vector<int> big_arr;

// copy
std::vector<int> compress(big_arr.begin(), big_arr.end());
// sort
std::sort(compress.begin(), compress.end());
// unique
std::erase(std::unique(compress.begin(), compress.end()), compress.end());
// replace old value with new idx
for (int& val : big_arr) {
  int idx = std::lower_bound(compress.begin(), compress.end(), val) - compress.begin();
  val = idx;
}
```

หรือใช้ map ทำก็ได้

```cpp
std::vector<int> big_arr;
std::map<int,int> compress;
// sort + unique
for (int val : big_arr) compress[val] = 0;
// assign index
int i = 0;
for (auto& p : compress) p.second = i++;
// replace old value with new idx
for (int& val : big_arr) {
  int idx = compress[val];
  val = idx;
}
```
