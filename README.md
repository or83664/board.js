# board.js
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
    <meta name="description" content="">
    <meta name="author" content="">
    <link rel="icon" href="favicon.ico">
    <title>board.html</title>
    <!-- Bootstrap core CSS -->
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css"></script>
<style>
/* Move down content because we have a fixed navbar that is 50px tall */
body {
  padding-top: 60px;
  padding-bottom: 20px;
}
</style>
<nav class="navbar navbar-inverse navbar-fixed-top">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" href="#">留言板</a>
        </div>
        <div id="navbar" class="navbar-collapse collapse">
        </div><!--/.navbar-collapse -->
      </div>
    </nav>


</head>

<body>
  <style>
input , textarea { width:100%; margin:8; padding:8; }
a { color:blue; }
</style>
   <div class="container">
      <!-- Example row of columns -->
      <div class="row">
        <div class="col-md-4">
        </div>
        <div class="col-md-4">
         <div><input id="title" "type="text" value="心情記事"/></div>
<br/>
<div><textarea id="text" style="height:300px">write down your feeling!</textarea></div>
<button onclick="save()" class="btn btn-lg btn-primary btn-block" >save</button>
<div>
<table id="list">
</table>
        </div>
        <div class="col-md-4">
        </div>
<script>
var oTitle = document.getElementById("title");
var oText  = document.getElementById("text");
var oList = document.getElementById("list");

function save() {
  var title = oTitle.value;
  var text  = oText.value;
  window.localStorage.setItem("notepad:"+title, text);
  showList();
}

function showList() {
  var rowHtml = "";
  for (var title in window.localStorage) {
    if (title.startsWith("notepad:")) {
      rowHtml += "<tr><td><a onclick=\"loadDoc('"+title+"')\">"+title.substring(8)+"</a></td></tr>"
    }
  }
  oList.innerHTML = rowHtml;
}

function loadDoc(title) {
  oTitle.value = title.substring(8);
  oText.value  = window.localStorage.getItem(title);
}
</script>
</div>


</body>
</html>
