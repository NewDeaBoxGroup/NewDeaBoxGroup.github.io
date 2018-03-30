---
title: "OS부팅하기"
author: PatrickNaver
date: 2018-03-30 23:02
category: Report
tags: ["OS", "어셈블리어", "부팅"]
description:  OS 부팅하기
---

이글은  부팅까지만 다룹니다.<br>
커널로드 능력부족으로 못했음.<br>
<br>
우선 부팅용으로 쓸 디스크를 포맷해줍니다.(저는 SD카드를 사용했으며 NTFS파일시스템으로 포맷하였습니다.)<br>
<img src="https://postfiles.pstatic.net/MjAxODAzMzBfMjgg/MDAxNTIyNDE3NTUzODE5.FWyHJ8QTHllyy6hyU72ytfeCGYgXE5zQWFn01URuOscg.wQVPbDEfcKFGH5iX1-OGyQUidrgOlwhAiafZe-KHl9Mg.PNG.macaga4847/Cap_2018-03-30_22-44-58-165.png?type=w773">
<br>
그리고 VBR에 써줄코드를 작성하고 어셈블러로 기계어로 변환시켜 줍니다.
<br>
<img src="https://postfiles.pstatic.net/MjAxODAzMTdfMTc5/MDAxNTIxMjkxMzYwNjYw.uDmndyBlfkmnG44sI6txuDWhidujbAjlblZYjDHtxkQg.Mv3-4xyhdhY9IIR9gwJb_XUyy2eGFbxdJHL4RHKg6OMg.PNG.macaga4847/Cap_2018-03-17_21-55-50-014.png?type=w773">
<br>
위의 소스는 Hi라고 그냥 두글자 띄우는 겁니다. 끝!<br>
그리고 위코드를 어셈블 해줍니다.<br>
저는 nasm 어셈블러 이용했습니다.<br>
<br>
nasm기준으로 nasm 원본코드 위치 -f bin -o 어셈블후의 파일위치 이렇게 써주시면 기계어로 변환됩니다.<br>
그후 디스크 VBR에 적어주셔야 합니다.<br>
저는 HxD(헥스에디터)를 이용했습니다.<br>
<img src="https://postfiles.pstatic.net/MjAxODAzMTdfMTMw/MDAxNTIxMjk0NDM4NTAw.EWumtUFeHMxNjozuLGtvWy7UbbNVopk3SVybRXeg-Log.T9yw6fDEaLbU_E90-A2euFnhTqxt-dIY1LfJbRwUB9Qg.PNG.macaga4847/Cap_2018-03-17_22-45-53-930.png?type=w773">
헥스에디터를 이용해 VBR에 써주었습니다.<br>
하지만 그전에 MBR에있는 파티션 테이블의 BOOT FLAG를 변경해주어야 합니다.<br>
<img src="https://postfiles.pstatic.net/MjAxODAzMTdfMjI2/MDAxNTIxMjk1Mjk5MDE2.lUvrf0WF89aSeyaUWysvzjIsGw5BBXj-ju6mHz-ds80g.x5GXiHqkXdQO9A1_qLn2l-FAP2RKoOcuDUH6tIs-eIQg.PNG.macaga4847/Cap_2018-03-17_23-01-05-575.png?type=w773">
<br>BOOT FLAG까지 바꾸고...(00=>80)<br>
부팅!<br>
<img src="https://postfiles.pstatic.net/MjAxODAzMTdfMTMz/MDAxNTIxMjk1OTY0NTI3.89u_6UJGYbQH9gMibaSWrLu1x1ePc9pAT4XuvN61NQog.v8HnpKz8X2cn1TCWv5IKAzBENcSgS3CAfGhi661ZcLAg.JPEG.macaga4847/20180317_231008.jpg?type=w773">
<br>
성공!
