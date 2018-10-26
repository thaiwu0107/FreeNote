# 需要的指令
## 名詞說明
* Spin
> 點擊投注,該按鈕也常使用「Play」或「Start」表示

* Autoplay
> 自動玩的按鈕,該按鈕也常直接使用「Auto」表示玩家可以使用該按鈕，設定自動玩的停止條件跟自動Spin的速度

* Lines
> 遊戲的賠付線數

* Bet
> 單 1 條線的投注額

* Total Bet
> 一次 SPIN 的總投注額 , Total Bet = Bet * Lines

* Win
> 一次 SPIN 中，玩家獲得的贏分總額

* Balance
> 玩家持有財產，該按鈕也常使用「Score」或「Credit」

* Info
> 遊戲規則說明，該按鈕也常使用「Pay Table」

* Main Game
> 主要遊戲

* Free Game
> 獎勵遊戲的其中一種，又稱為免費旋轉或免費轉，遊戲玩法同 Main Game，主要也是以「線獎獎勵」的兌獎為主，差別在於玩家不需要花錢投注，滿足連線條件就可以免費獲得相對應規則上的獎勵

* Bonus Game
> 老虎機獎勵遊戲的其中一種，常被稱為「小遊戲」或「副獎遊戲」通常非 Free Game 玩法的獎勵遊戲都統稱為 Bonus Game

* Reels
> 滾輪表遊戲中符號旋轉的部分, 舉例一個 3×5 的老虎機遊戲，由左至右的轉輪帶分別稱為 Reel1、Reel2、Reel3、Reel4、Reel5

* Near Win
> 一種表演特效，通常用在 SCATTER 或 BONUS Symbols 收集上。假設遊戲規則為「盤面上出現 3 個 SCATTER Symbols 即可進入免費遊戲」，當盤面已經出現一個以上的 SCATTER Symbol 時，尚未停止的轉輪帶會帶上一個加速特效，增加玩家的緊張與期待感

* Symbol
> 中文較常見的翻譯為「符號」，也就是老虎機遊戲轉輪帶上面的圖案，全部的符號都會出現在賠率表 (pay table) 上，裡面會詳細說明每個符號的兌獎規則和賠率大小。WILD、SCATTER 和 BONUS 不一定會全部用在同一款遊戲中，依該遊戲設計而定

* WILD
> 中文較常見的翻譯為「百搭」，通常可以替代所有符號，造成更容易連線的效果，有點類似撲克牌中的鬼牌角色。有些遊戲規則都會將 BONUS 和 SCATTER 排除在外，也就是 WILD 不能替代 BONUS 和 SCATTER 的意思

* Expanding Wilds
> 百搭符號的一種變形，又叫做「擴展百搭」，當它一出現就會往上和往下擴展至整條轉輪帶，造成更多的連線。除了上下擴展外，還有遊戲做成左右擴展的玩法，其線獎的命中率提高更多

* Lock Wilds
> 百搭符號的一種變形，又叫做「鎖定百搭」，當它一出現就會鎖住該格子，WILD 會固定在轉輪帶上，直到指定局數的 SPIN 結束，通常效果只有 1 局，多局數的鎖定百搭放在免費遊戲中比較常見

* Random Wilds / Walking Wilds
> 百搭符號的一種變形，又叫做「隨機百搭」，遊戲中會隨機給予多個 WILD，其出現位置並不固定

* SCATTER
> 免費遊戲、免費旋轉符號，轉輪帶上達成遊戲內規定的條件後，立即進入免費 SPIN，次數隨各遊戲不同。常見的規則舉例：3 個 SCATTER 進入免費遊戲 10 次，4 個 SCATTER 進入免費遊戲 15 次，5 個 SCATTER 進入免費遊戲 20 次

* BONUS
> 副獎遊戲符號，轉輪帶上達成遊戲內規定的條件後，立即進入副獎遊戲。常見的規則舉例：Reel1、Reel3 和 Reel5 出現 3 個 BONUS 符號即可進入副獎遊戲

* JACKPOT
> 進入Feature Game(Free Game、Bonus Game、Wheel Game、Choose Game 都是 Feature Game) 或是Main Game出現JACKPOT圖案才有可能獲得的超級大獎

* RTP
> Return To Player 回饋率

## 前端要送的Events
### Spin
>資料格式:
```
{
	type: number,
    bet: number
}
```

### FreeGame Choose
>資料格式:
```
{
	type: number,
    free_spin_times: number
}
```

### History
>資料格式:
```
{
	type: number,
    id: number
}
```

## 後端要送的Events
### SpinResult
>資料格式:
```
1.正常 = {
	type: number,
    reels: number[],
    lines: number[],
    near_win_reel: number,
    balance: number,
    expanding_wilds_reels: number[]
}

2.錢不夠(或是等等錯誤機制) = {
	type: number,
    message: string
}
```

### FreeGameResult
>資料格式:
```
result = {
    reels: number[],
    lines: number[],
    near_win_reel: number,
    balance: number,
    expanding_wilds_reels: number[]
}
{
	type: number,
    result_list: result[]
}
```

### History
>資料格式:
```
result = {
	balance: number,
    win: number,
    spin: number,
    bigwin: number
}
{
	result_list: result[]
}
```