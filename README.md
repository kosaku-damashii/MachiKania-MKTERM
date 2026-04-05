# MachiKania-MKTERM
Terminal emulator on MachiKania type PU<BR>
MachiKania type PU ( http://www.ze.em-net.ne.jp/~kenken/machikania/typepu.html )で動作するターミナルソフト。<BR>
MachiKania type PU mini や MachiKania type PU で動作する。<BR>

〇接続方法<BR>
PCなどをUSBシリアル変換などで繋ぎ表示とキー入力の端末にして操作しているホストマイコンボートに対して、PCの代わりにMachiKania type PUをUARTで接続する。その際、信号の出夏レベルが異なる場合(5V/3.3V)は、レベル変換モジュールを介してUART接続すること。<BR>

レベル変換モジュールの例としては、秋月電子で購入できる「4ビット双方向ロジックレベル変換モジュール」(https://akizukidenshi.com/catalog/g/g113837/) が2ch分UARTを変換出来る。高電圧側と低電圧側で接続できるピンが決まっているので注意。以下、このモジュールを前提に説明する。<BR>
UARTを接続する際には、信号の電圧レベルが同じであれば、GND/Tx/Rxの３本で、MachiKania type PUとホストマイコンボードを繋げばよいが、レベル変換が必要な場合は、基準電圧をレベル変換モジュールへ伝える必要があるので、3.3V(MachiKania type PU)側と5V(ホストマイコンボード側)も接続すること。<BR>
なお、MachiKania type PUとホストマイコンボードを動作させるための電源は、それぞれのボードへ別途接続しておく。

<img width="1499" height="1361" alt="image" src="https://github.com/user-attachments/assets/5e84f3e1-135e-4241-ae71-84d03dcb997d" />

MachiKania type PU miniの外部入出力のピン配置は下記の通り。
なお、5VはUARTの接続には使用しないが、MachiKania type PU miniのDC端子に直結しているので、ホストマイコンボードからこの5Vピンに給電してMachiKania type PU miniを動作させることも出来ると思われる。
<img width="533" height="347" alt="image" src="https://github.com/user-attachments/assets/921aa8d3-e564-4aca-8df2-0a95d741f04d" />


〇使い方<BR>
<注意点><BR>
MachiKania type PUの横80文字モードを使って表示している。ただし、このモードではカラー表示は出来ずモノクロになる。<BR>
現状、最低限のコントロールコードについては実装されているので、コマンドラインの操作は出来るが、エスケープシーケンスは未対応なので、エディタなどについては正常に操作出来ない。<BR>
制御文字の表示は、例えば、ESCの場合は"^["と２文字で表示される。<BR>

<CapsLockを起動時にOFFする方法><BR>
MACHIKAP.INI の 「CAPSLOCK」をコメントアウト（先頭に'#'を追加）して起動すると、CapsLockをOFFすることが出来る。<BR>

<自動実行について><BR>
自動起動したいファイル（KMTERAM.BAS）をSDカードのルートディレクトリに「MACHIKAP.BAS」という名前で保存すると、起動時に自動的に実行されます。
詳しくは、本家サイト ( http://www.ze.em-net.ne.jp/~kenken/machikania/typep.html )の「自動実行プログラムについて」を参照。<BR>
