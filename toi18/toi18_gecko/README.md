<!-- @codegen_problem begin -->

# TOI18 gecko - จั๊กกิ้ม (Gecko)

[🏠 รวมเฉลย TOI18](../)

[💎 problem.pdf](./toi18_gecko.pdf)

[🎉 solution.cpp](./toi18_gecko.cpp)

<img width="700" src="https://github.com/krist7599555/toi/assets/19445033/cee65a0e-a8c1-4cfd-b4aa-e677ef607043" />
<!-- @codegen_problem end -->

ShortestPath (Dijkstra's algorithm) + Backtrack of DFS

ต้องมองให้ออกว่า เดินจากตุ๊กแกไปหาแมลงมุม มีค่าเท่ากับเดินจากแมลงมุมไปหาตุ๊กแก

แต่ถ้าเดินจากแมลงมุมจะทำได้ง่ายกว่า เพราะจะหาได้ชัดว่าต้องใช้ไม้กี่อัน แล้วก็ใช้ทำ backtrack ตอนย้อนหลับมาได้ด้วย
