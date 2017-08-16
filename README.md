# NR-server
クライアントサイドからみたAPI
送られてくるのはJSON

## RoomManager
ルームとplayerの情報を管理する
### emit "rm_access"
name、character番号を送る
on "wait"か on "start_battle"がくる
disconnect後復帰した場合を後で実装

### on "rm_wait"
人が揃うのを待っている状態を描画してねー

### on "btl_start"
相手のname, character番号、stage番号を受け取る
バトル開始だよーページ遷移してねー

### on "btl_return"
後で

## BattleManager
playerそれぞれのIDと、一つ前のコマンドを保持する

### emit "cmd_mine"
commandを送る (0~3)

### emit "cmd_timeup"
時間切れ。特に何も送らない

### on "cmd_enemy"
コマンドが双方出揃う、または一定時間経過で相手のコマンドが送られてくる
時間切れ、通信が切れはランダム

### emit "btl_end"
バトルが終了したらこれを送ろう
ルームを消す

## SocketIO標準
### socket.connect()
これをやるとはじまる予感
### on "connect"
接続したら自動的に返ってくる
### data
JSONが入ってるんじゃないかなー。たぶん
でも配列っぽい？
