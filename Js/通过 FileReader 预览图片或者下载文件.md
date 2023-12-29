
```html
<!doctype html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport"  
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">  
    <meta http-equiv="X-UA-Compatible" content="ie=edge">  
    <title>Document</title>  
</head>  
<body>  
  
<div>  
    <span>图片预览</span>  
    <input type="file" id="input1">  
    <img id="img"/>  
</div>  
  
<div>  
    <span>文件下载</span>  
    <input type="file" id="input2">  
</div>  
  
  
</body>  
<script>  
  
  const input1 = document.getElementById('input1');  
  const input2 = document.getElementById('input2');  
  
  
  input1.onchange = event => {  
    const file = event.target.files[0];  
  
    const reader = new FileReader();  
  
    reader.onloadend = function () {  
      const img = document.getElementById('img');  
      img.src = reader.result;  
    };  
  
    reader.readAsDataURL(file);  
  }  
  
  input2.onchange = event => {  
    const file = event.target.files[0];  
  
    const reader = new FileReader();  
  
    reader.onloadend = function () {  
      const a = document.createElement('a');  
      a.download = file.name;  
      a.href = reader.result;  
      document.body.appendChild(a);  
      a.click();  
      document.body.removeChild(a);  
    };  
  
    reader.readAsDataURL(file);  
  }  
</script>  
</html>
```