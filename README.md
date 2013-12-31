jquery.extratouch
==================

ボタンをタッチしてから上下にスクロールされなかった場合にtouchend時に関数を実行する jQuery Plugin

仕様
------
下記のタイミングで関数を実行することができます。

 * startFunction : touchstart時に実行
 * moveFunction : touchstart後、上下どちらかにスクロールした時に実行
 * moveUpFunction : touchstart後、上にスクロールした時に実行
 * moveDownFunction : touchstart後、下にスクロールした時に実行
 * endFunction : 上下にスクロールされなかった場合のtouchend時に実行

使い方
------
    <script type="text/javascript" src="js/jquery.js"></script>
    <script type="text/javascript" src="js/jquery.extratouch.js"></script>

オプション
------

 * startFunction : touchstart時に実行される関数。
 * moveFunction : touchstart後、上下どちらかにスクロールした時に実行される関数
 * moveUpFunction : touchstart後、上にスクロールした時に実行される関数
 * moveDownFunction : touchstart後、下にスクロールした時に実行される関数
 * endFunction : 上下にスクロールされなかった場合のtouchend時に実行される関数
 * isReturn : endFunction実行時に return false;するかしないか。

### 初期設定 ###
	
	startFunction : '',
	moveFunction : '',
	moveUpFunction : '',
	moveDownFunction : '',
	endFunction : '',
	isReturn : true


使用例
------
2通りの書き方ができます。

	//例1）
	$('.button').extraTouch({
		startFunction : function(e){
			$(e.currentTarget).addClass('active');
		},
		moveFunction : function(e) {
			console.log('動かした！')
			$(e.currentTarget).removeClass('active');
		},
		moveUpFunction : function(e) {
			console.log('上に移動')
		},
		moveDownFunction : function(e) {
			console.log('下に移動')
		},
		endFunction : function(e) {
			$(e.currentTarget).removeClass('active');
		}
	});

	$('.button').extraTouch({
		endFunction : function(e) {
			alert('test');
		},
		isReturn : false
	});

	//例2）
	//下記のような書き方もできます。
	//1つ目がstartFunction、２つ目がmoveFunction、3つ目がendFunction
	$('.button2').extraTouch(
		function(e){
			$(e.currentTarget).addClass('active');
		},
		function(e) {
			console.log('動かした！')
			$(e.currentTarget).removeClass('active');
		},
		function(e) {
			$(e.currentTarget).removeClass('active');
		}
	);

	//もしも関数が2つ以下の場合はendFunction
	$('.button2').extraTouch(
		function(e) {
			alert('test');
		},
		false
	);


ライセンス
----------
+ Copyright 2014 &copy; kamem
+ [http://www.opensource.org/licenses/mit-license.php][mit]

[develo.org]: http://develo.org/ "develo.org"
[MIT]: http://www.opensource.org/licenses/mit-license.php