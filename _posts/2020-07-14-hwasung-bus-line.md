---
layout: post
title: 화성시 최적 시내버스 노선 제시
date: 2020-07-14
image: /assets/images/blog/bus.png
author: yelim
---


<p>&nbsp;</p>
<div class="post_head" style="margin-left: 20px; line-height: 1.5;"><span style="font-size: 36px; color: #2c82c9;"><strong>Summary</strong></span></div>
<section class="post_info">
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>Subject</strong> : 화성시 관내 시내버스에 대한 노선 신설 또는 기존 노선의 개선 제안</span></p>
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>Tool </strong>: Python</span></p>
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>ML</strong> : KMeans++</span></p>
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>Key Packages</strong> : Networkx</span></p>
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>Data</strong></span></p>
<p style="margin-left: 40px; line-height: 1;"><span style="font-size: 15pt;">&lt;.csv&gt;</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">버스카드 태깅 정보</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">버스 정류장 정보</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">행정동별 유동인구 정보</span></p>
<p style="margin-left: 40px; line-height: 1;"><span style="font-size: 15pt;">&lt;.geojson&gt;</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">화성시 읍면동</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">100m x 100m 그리드 시간별 유동인구</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">거주인구</span></p>
<p style="margin-left: 60px; line-height: 1;"><span style="font-size: 15pt;">도로 네트워크 링크</span></p>
<p style="margin-left: 20px; line-height: 1;">&nbsp;</p>
</section>
<section class="key_points">
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>Key Points</strong></span></p>
<p style="margin-left: 40px;"><span style="font-size: 15pt;">1. 버스 노선 운행의 적합 여부를 확인하기 위해서는 굴곡도, 최단거리를 구해야 한다. 데이콘에서 제공한 geojson node link 파일은 오류가 많아서 최신 버전으로 도로 네트워크를 구성했습니다.</span></p>
<p style="margin-left: 40px;"><span style="font-size: 15pt;">2. 데이터를 훈련해 스코어를 갱신하는 주제가 아닌 만큼, 자신만의 기준으로 수정해야 할 노선을 논리적으로 선정하는 것이 중요했습니다. 이를 위해 엘보우 기법으로 클러스터링 한 후 가장 적게 클러스터링 된 노선 Top10을 선택했습니다. 또한 이 중에서 중복도가 높은 노선에 가중치를 두어 최종 수정 노선을 선택했습니다.</span></p>
</section>
<p style="line-height: 1.5;">&nbsp;</p>
<section class="results">
<p style="margin-left: 20px; line-height: 1;"><span style="font-size: 15pt;"><strong>Results</strong></span></p>
<p style="margin-left: 40px;"><span style="font-size: 15pt;">1. 수정이 시급한 노선은 1000번, 81번이었습니다.&nbsp;</span></p>
<p style="margin-left: 40px;"><span style="font-size: 15pt;">2. 1000번은 1001번, 1004번 그리고 330번과 중복되는 정류장이 많았고 근방 100m의 거주 인구와 출퇴근/비출퇴근 시간에 탑승 인원 또한 많았기에 선정되었습니다. 81번은 80번과 중복되는 정류장이 많았고 이외의 변수 상황은 1000번과 마찬가지였습니다.</span></p>
</section>
<p style="line-height: 1.5;">&nbsp;</p>