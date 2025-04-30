## 📄 liff 紀錄

### 觀念
1.liff為line機制，網址會類似這樣:https://liff.line.me/xxxxxxxx?class_num=bbb
2.liff會對應一個網頁，該網頁可以用liff相關函式取得資料，像下面這樣，只能透過前端取得資料

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>LIFF Redirect with Token</title>
    <script src="https://static.line-scdn.net/liff/edge/2.1/sdk.js"></script>
</head>
<body>
    <p>請稍候，自動導向中...</p>

    <script>
        async function initLiffAndRedirect() {
            const liffId = "aaa"; // 替換為 LIFF ID

            try {
                await liff.init({ liffId });

                if (!liff.isLoggedIn()) {
                    liff.login();
                    return; // login 會重新導向，這邊先結束
                }

        
                const profile = await liff.getProfile();

                // 拿到使用者 ID（userId）
                const userId = profile.userId;    //這邊會拿到UserId

                const queryString = window.location.search.replace(/^\?/, '');   // 移除開頭的 ?
                const redirectUrl = `xxx.aspx?${queryString}&user_id=${userId}`; // 導向Class_Content頁面

                window.location.href = redirectUrl;

            } catch (error) {
                console.error("LIFF 初始化失敗", error);
                document.body.innerHTML = `<p>發生錯誤：${error}</p>`;
            }
        }

        window.onload = initLiffAndRedirect;
    </script>
</body>
</html>

3.觀念就是當點開https://liff.line.me/xxxxxxxx?class_num=bbb 網址後，
相當於打開映射的網頁，比如https://Liff_Redirect.html，該網頁可以透過liff既有的line函式庫取得資料







