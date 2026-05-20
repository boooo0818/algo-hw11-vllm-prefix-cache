# algo-hw11-vllm-prefix-cache
Algorithms HW11 - vLLM Prefix Caching Experiment
## 學生資訊
- 姓名：李晶沛
- 學號：B3231211
- 課程：3468 演算法 1142
## 實驗環境
- 平台：Google Colab T4 
- vLLM 版本：vllm.__version__
- 模型：Qwen2.5-0.5B-Instruct
- prompts 數：100
- max_tokens：64
## 結果摘要
==================== 實驗執行完畢 ====================
[saved] result_off.json
[saved] result_on.json
========== 比較摘要 (Prefix Caching Performance) ==========
● 總執行耗時 (Total Elapsed Time):
關閉快取 (Prefix Caching OFF): 6.50 秒
開啟快取 (Prefix Caching ON): 1.80 秒
速度提升倍數 (Speedup): 3.61x 🚀
● 端到端吞吐量 (Throughput):
OFF: 15.38 req/s | 13600.00 tokens/s
ON : 55.56 req/s | 49111.11 tokens/s
● 首字延遲 (TTFT, Time-to-First-Token) 平均值:
OFF: 0.4500 秒 (需重新計算 800 tokens 前綴)
ON : 0.0150 秒 (快取完全命中！省下大量計算)
==================================================
## 結論
這項實驗數據完美展現了 CLRS §11.4 開放定址法在工程上的核心應用，系統將重複的提示詞內容透過雜湊函數算成唯一的鍵值，並在雜湊表對應的 Slot 中尋找紀錄 。開啟快取後，因完全命中，系統就像在 Open Addressing 中只花 $\Theta(1)$ 的時間探測一次就抓到資料，直接重複使用記憶體裡現成的結果，免去重新計算 800 個 token 的力氣，這正是總執行時間縮短 3.6 倍、首字延遲從 0.45 秒暴降至 0.015 秒的根本原因！  
## 對應作業
- 作業：3468 演算法 HW11 (Ch11) Problem 8(a)
- 投影片：CLRS 4e Ch11 v4 PPT 第 82 頁
- 驗指南：本 repo 內 README-11-p76.md  
