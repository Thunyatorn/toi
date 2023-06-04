# TOI18 gecko

[💎 problem.pdf](./toi18_gecko.pdf)

[🎉 solution.cpp](./toi18_gecko.cpp)

<img width="350" alt="image" src="https://github.com/krist7599555/toi/assets/19445033/38b4d87c-0304-4d26-90a0-9ddb8706e481">

ShortestPath (Dijkstra's algorithm) + Backtrack of DFS

ต้องมองให้ออกว่า เดินจากตุ๊กแกไปหาแมลงมุม มีค่าเท่ากับเดินจากแมลงมุมไปหาตุ๊กแก

แต่ถ้าเดินจากแมลงมุมจะทำได้ง่ายกว่า เพราะจะหาได้ชัดว่าต้องใช้ไม้กี่อัน แล้วก็ใช้ทำ backtrack ตอนย้อนหลับมาได้ด้วย
