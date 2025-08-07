# -from pathlib import Path
from IPython.display import FileLink

# Tạo file HTML đơn giản để lấy token từ localStorage trên iOS Safari
html_content = """
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lấy Token Discord</title>
</head>
<body style="font-family: sans-serif; padding: 20px;">
  <h2>Lấy Token Discord</h2>
  <button onclick="getToken()" style="padding: 10px 20px; font-size: 16px;">Hiện Token</button>
  <p id="output" style="margin-top: 20px; font-weight: bold;"></p>

  <script>
    function getToken() {
      try {
        const direct = localStorage.token;
        const wrapped = JSON.parse(localStorage.tokens || '{}').__analytics__;
        const token = (direct || wrapped || '').replace(/^\"|\"$/g, '');
        if (!token) {
          document.getElementById("output").textContent = "❌ Không tìm thấy token.";
        } else {
          document.getElementById("output").textContent = "✅ Token của bạn: " + token;
        }
      } catch (e) {
        document.getElementById("output").textContent = "⚠️ Lỗi: " + e.message;
      }
    }
  </script>
</body>
</html>
"""

# Lưu file
file_path = Path("/mnt/data/get_token_ios.html")
file_path.write_text(html_content, encoding='utf-8')

file_path.name  # Return file name for download link
