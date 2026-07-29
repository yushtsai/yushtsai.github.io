https://drive.google.com/file/d/15M7-fq_RC21gCkcvBpaTpav5GIGR3hcC/view?usp=sharing

| 方法 | 輸入資料 | 輸入數量 | 輸入限制 | 輸出資料 | 輸出數量 | 輸出限制 | 生成腳本 |
|---|---|---|---|---|---|---|---|
| **NoiseTransfer** | clean X + reference noisy Y^r(不需配對) | 各 1 張/次 | 需 noisy reference 指定噪聲類型 | 合成 noisy patch | 動態生成,無固定張數 | 噪聲由 reference 決定 | 無批量腳本,需自己包 |
| **NeCA-W** | clean + 配對 noisy(估 gain) | 各 1 張/次 | 每台相機一組模型;需配對 noisy | 合成 noisy image | 1:1 替換 SIDD(靜態) | 綁定該相機分佈 | `main_test.py`(單張) |
| **NeCA-S** | clean + AWGN(σ∈[0,75]) | 1 張/次 | 訓練僅需 3 pairs;噪聲 signal-independent | SINC noisy image | 1:1 替換(靜態) | 無 signal dependency | 同上 |
| **NAFlow** | clean(+noisy 選分佈) | 1 張/次 | 限訓練過的相機/ISO 分佈 | 合成 noisy image | 1:1 替換(靜態) | 多樣性受分佈採樣限制 | `scripts/generate_images.py` |
| **PNG** | clean + 任意 noisy(prompt) | 各 1 張/次 | 需 1 張 noisy 抽 prompt;不需 metadata | 合成 noisy image | 全資料集批次生成 | 品質受 SIDD 訓練分佈影響 | `generate_image.py`(批量,4 資料集) |
