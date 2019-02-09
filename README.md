### これは何？
`@EnableScheduling`を用いて  
Spring BootのScheduling Tasksについて調査した際のサンプルコードです  

以下を検証しています  
5秒おきに起動されるTaskです。
1. 5秒以内で終わるTask
2. 5秒以上かかるTask(10秒かかる)
3. 5秒以上かかるTask(10秒かかる)でFuture利用

### 検証結果
1.は当然ながら5秒おきに起動されて別段言及することはない
2.は処理が終わるまで待ち合わせてくれる嬉しい挙動
3.は当たり前だが2.の結果をもって、別スレッドで起動するので、起動要求はやはり5分おきにかかる  
これのメリットはプログラム自体がスタックしてるかどうかの判別がつきやすいのかな…といったところか。
