```
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSVアップロード</title>
</head>
<body>
    <h2>CSVファイルアップロード</h2>
    <form action="http://example.com/upload" method="post" enctype="multipart/form-data">
        <label for="file">CSVファイルを選択:</label>
        <input type="file" name="file" id="file" accept=".csv" required>
        <button type="submit">アップロード</button>
    </form>
</body>
</html>
```
