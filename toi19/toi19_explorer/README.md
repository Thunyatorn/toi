# TOI19 explorer

[💎 problem.pdf](./toi19_explorer.pdf)

[🎉 solution.cpp](./toi19_explorer.cpp)

<img width="350" alt="image" src="https://github.com/krist7599555/toi/assets/19445033/1c1e7a55-a123-4f21-8a60-cfc0eac008a3">

Math

ให้แปลงลำดับการเดินให้กลายเป็นกราให้ได้ก่อน โดยใช้ stack

เช่น `1 2 4 2 5 2 1 3 1`
เป็น

```text
1 => {2, 3}
2 => {4, 5}
3 => {}
4 => {}
5 => {}
```

แล้วแต่ละ node สามารถสลับลูกได้ตามใจ

- ถ้ามีลูก 0 ตัวก็สลับได้ `1` แบบ ()
- ถ้ามีลูก 1 ตัวก็สลับได้ `1 * ways(1st child)` แบบ (1)
- ถ้ามีลูก 2 ตัวก็สลับได้ `2 * ways(1st child) * ways(2nd child)` แบบ (12,21)
- ถ้ามีลูก 3 ตัวก็สลับได้ `6 * ways(1st child) * ways(2nd child) * ways(3rd child)` แบบ (123,132,213,231,312,321)
- ถ้ามีลูก n ตัวก็สลับได้ `factorial(n) * ∏ { i=1..n | ways(i-th child) }`

> - `∏` คือ N-ARY PRODUCT หมายถึงในเอาทุกตัวใน set มาคูณกัน
> - `∑` คือ N-ARY SUMMATION หมายถึงในเอาทุกตัวใน set มาบวกกัน

ตัวอย่างข้างบนจะเป็น

```text
1 => {2, 3}   = fac(2) * ways[2] * ways[3]   = 4 ways *
2 => {4, 5}   = fac(2) * ways[4] * ways[5]   = 2 ways
3 => {}       = fac(0)                       = 1 ways
4 => {}       = fac(0)                       = 1 ways
5 => {}       = fac(0)                       = 1 ways
```

ส่วนวิธีไล่ stack คือ

- ถ้าตัวถัดไปไม่เคยเดิน => เป็นลูก
- ถ้าตัวถัดเคยเดินมาแล้ว => เป็นพ่อ ให้เดินย้อนกลับไป

> แนะนำให้อ่านเรื่อง Tree Traversal Techniques เพิ่มเติม จะเป็นเรื่อง
>
> - Preorder Traversal (Parent ...Childs)
> - Postorder Traversal (...Childs Parent)
> - Inorder Traversal (ChildLeft Parent ChildRight)
>
> ในโจทย์ข้อนี้จะเป็นการผสม Preorder Traversal และ Postorder Traversal
> โดยถ้าให้รูปแบบการเดินมา 2 แบบข้างบน จะแปลงกลับเป็นกราฟได้
