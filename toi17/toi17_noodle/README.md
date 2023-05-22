# TOI17 noodle

[🎉 solution.cpp](./toi17_noodle.cpp)

BinarySearch + K-th Largest Element using Priority Queue

## Observe 1 - เราหาจำนวนร้านจาก `minimum_sum_noodle_pershop` ได้ไหม

เหมือนเป็นการคิดว่า ถ้าได้คำตอบมา เราเช็คได้ไหมว่าคำตอบนี้ทำได้หรือเปล่า

เรารู้ว่า shop นึงจะเลือกช่องรับเส้น k อัน เขาก็ต้องเลือกช่องรับเส้นที่ได้เส้นเยอะๆก่อน ถ้ากำหนดช่วงมาให้เราก็ sort เอาหา k ตัวมากสุดได้

แต่ถ้าเข้าไม่กำหนดช่วงมาให้ แต่มีผลรวมขั้นต่ำที่ต้องการมาให้ ก็ให้ทำแบบ greedy คือ

- `ถ้าจำนวนร้านที่ทดในใจ < k` ก็ทดจำนวนร้านเพิ่ม
- `ถ้าจำนวนร้านที่ทดในใจ >= k`
  - ถ้า `ผลรวม k ตัว มากสุด < minimum_sum_noodle_pershop` ก็ต้องรับเส้นเพิ่มจนกว่าจะพอ
  - ถ้า `ผลรวม k ตัว มากสุด >= minimum_sum_noodle_pershop` ก็ถือว่าตัดแบ่งร้านค้าตรงนี้ได้ และเริ่มทำร้านถัดไป

วิธีหา max k-th ตัวไวๆ แทนที่จะคิดว่าต้องเลือกตัวมากสุด `k` ตัว เป็น ลบตัวที่น้อยสุดไป `n-k` ครั้ง เลยสามารถทำได้โดยการสร้าง min heap (เพื่อหาตัวน้อยสุดได้ไวๆ) แล้ว pop ออก `n-k` คร้่ง ของที่เหลือในนั้นจะเป็น `max k-th ตัว`

> <https://www.geeksforgeeks.org/k-th-smallest-element-in-an-unsorted-array-using-priority-queue>

## Observe 2 - เรา binary search ได้

ให้ Binary Search หาเลยว่าถ้ากำหนด `ผลรวม noodle ขั้นต่ำของแต่งละร้าน (minimum_sum_noodle_pershop)`

- ถ้า `minimum_sum_noodle_pershop` น้อย ก็จะเปิดร้านได้หลายร้าน
- ถ้า `minimum_sum_noodle_pershop` เยอะ ก็จะเปิดร้านนิดเดียว

เราต้องการหา `minimum_sum_noodle_pershop` ตัวแรกที่ทำได้ `n_shop` พอดี

แล้วก็ตอบ
