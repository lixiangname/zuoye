<!DOCTYPE html>
<html>

	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			.box {
				margin: 0 auto;
				width: 500px;
				height: 400px;
				border: 1px solid black;
			}
			
			img {
				width: 150px;
				height: 150px;
				margin: 20px;
			}
			
			ul {
				list-style: none;
				float: right;
				text-align: center;
			}
			
			ul li {
				width: 200px;
				height: 20px;
				background-color: gray;
				margin: 10px;
			}
			
			.left {
				float: left;
			}
			
			.right {
				float: right;
			}
			
			.clear {
				clear: both;
				display: block;
				content: "";
			}
			
			.back {
				width: 500px;
				height: 180px;
			}
			
			.garbage {
				width: 150px;
				height: 150px;
				margin: 20px;
				background-image: url(images/trash2.jpg) ;
				background-size:150px 150px ;
			}
		</style>
	</head>

	<body>
		<div class="box">
			<div class="left">
				<img src="images/trash1.png" />
			</div>
			<ul class="right ">
				<li draggable="true" class="list">书名1</li>
				<li draggable="true" class="list">书名2</li>
				<li draggable="true" class="list">书名3</li>
			</ul>
			<div class="clear ">
				<p>已删除</p>
				<hr />
			</div>
			<div class="back ">

			</div>
		</div>
		<script type="text/javascript">
			var list = document.querySelectorAll('.list');
			var back = document.querySelector('.back');
			var change = document.querySelector('.box img')
			var tmp;
			for (var i = 0; i < list.length; i++) {
				list[i].ondragstart = function() {
					tmp = this;
				}
				list[i].ondragend = function() {
					tmp = null;
				}
			}
			back.ondragleave = function() {}
			back.ondragenter = function() {}
			back.ondragover = function(e) {
				e.preventDefault();
			}
			back.ondrop = function(e) {
				e.preventDefault();
				console.log('松手');
				if (tmp != null)
					this.appendChild(tmp);
				if (back !="") {
					change.className = "garbage";
					
				}
			}
		</script>
	</body>

</html>
