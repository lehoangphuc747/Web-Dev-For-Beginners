<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "46bcdd9a0174031655a49bb062aa279c",
  "translation_date": "2025-10-24T13:50:38+00:00",
  "source_file": "6-space-game/6-end-condition/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../../README.md) | [◀️ Quay lại](../README.md) | [▶️ Module tiếp theo](../../7-bank-project/README.md)

---
# Xây dựng trò chơi không gian Phần 6: Kết thúc và Khởi động lại

Mỗi trò chơi tuyệt vời đều cần có điều kiện kết thúc rõ ràng và cơ chế khởi động lại mượt mà. Bạn đã xây dựng một trò chơi không gian ấn tượng với di chuyển, chiến đấu và tính điểm - giờ là lúc thêm những mảnh ghép cuối cùng để làm cho nó hoàn chỉnh.

Hiện tại, trò chơi của bạn chạy vô thời hạn, giống như các tàu thăm dò Voyager mà NASA đã phóng vào năm 1977 - vẫn đang du hành trong không gian sau nhiều thập kỷ. Mặc dù điều đó phù hợp với việc khám phá không gian, nhưng trò chơi cần có điểm kết thúc xác định để tạo ra trải nghiệm thỏa mãn.

Hôm nay, chúng ta sẽ triển khai các điều kiện thắng/thua và hệ thống khởi động lại. Sau bài học này, bạn sẽ có một trò chơi hoàn chỉnh mà người chơi có thể hoàn thành và chơi lại, giống như các trò chơi arcade cổ điển đã định hình ngành công nghiệp này.

## Câu hỏi trước bài giảng

[Câu hỏi trước bài giảng](https://ff-quizzes.netlify.app/web/quiz/39)

## Hiểu về điều kiện kết thúc trò chơi

Khi nào trò chơi của bạn nên kết thúc? Câu hỏi cơ bản này đã định hình thiết kế trò chơi từ thời kỳ arcade đầu tiên. Pac-Man kết thúc khi bạn bị ma bắt hoặc ăn hết các chấm, trong khi Space Invaders kết thúc khi người ngoài hành tinh chạm đáy hoặc bạn tiêu diệt hết chúng.

Là người tạo ra trò chơi, bạn sẽ xác định các điều kiện thắng và thua. Đối với trò chơi không gian của chúng ta, đây là những cách tiếp cận đã được chứng minh để tạo ra lối chơi hấp dẫn:

- **Tiêu diệt `N` tàu địch**: Đây là cách khá phổ biến nếu bạn chia trò chơi thành các cấp độ khác nhau, bạn cần tiêu diệt `N` tàu địch để hoàn thành một cấp độ.
- **Tàu của bạn bị phá hủy**: Có những trò chơi mà bạn thua nếu tàu của bạn bị phá hủy. Một cách tiếp cận phổ biến khác là khái niệm về mạng sống. Mỗi lần tàu của bạn bị phá hủy, nó sẽ trừ đi một mạng sống. Khi tất cả mạng sống bị mất, bạn sẽ thua trò chơi.
- **Thu thập `N` điểm**: Một điều kiện kết thúc phổ biến khác là thu thập điểm. Cách bạn kiếm điểm tùy thuộc vào bạn, nhưng thường thì điểm được gán cho các hoạt động như tiêu diệt tàu địch hoặc thu thập các vật phẩm mà các vật phẩm *rơi* ra khi bị phá hủy.
- **Hoàn thành một cấp độ**: Điều này có thể bao gồm nhiều điều kiện như tiêu diệt `X` tàu địch, thu thập `Y` điểm hoặc có thể là thu thập một vật phẩm cụ thể.

## Triển khai chức năng khởi động lại trò chơi

Các trò chơi hay khuyến khích khả năng chơi lại thông qua cơ chế khởi động lại mượt mà. Khi người chơi hoàn thành trò chơi (hoặc gặp thất bại), họ thường muốn thử lại ngay lập tức - dù là để vượt qua điểm số hay cải thiện hiệu suất.

Tetris là ví dụ hoàn hảo: khi các khối của bạn chạm đỉnh, bạn có thể bắt đầu một trò chơi mới ngay lập tức mà không cần điều hướng qua các menu phức tạp. Chúng ta sẽ xây dựng một hệ thống khởi động lại tương tự, giúp trạng thái trò chơi được đặt lại sạch sẽ và đưa người chơi trở lại hành động nhanh chóng.

✅ **Suy ngẫm**: Hãy nghĩ về các trò chơi bạn đã chơi. Trong điều kiện nào chúng kết thúc, và làm thế nào bạn được nhắc khởi động lại? Điều gì làm cho trải nghiệm khởi động lại trở nên mượt mà so với gây khó chịu?

## Những gì bạn sẽ xây dựng

Bạn sẽ triển khai các tính năng cuối cùng để biến dự án của mình thành một trải nghiệm trò chơi hoàn chỉnh. Những yếu tố này phân biệt các trò chơi được hoàn thiện với các nguyên mẫu cơ bản.

**Đây là những gì chúng ta sẽ thêm hôm nay:**

1. **Điều kiện chiến thắng**: Tiêu diệt tất cả kẻ thù và nhận được màn ăn mừng đúng nghĩa (bạn xứng đáng với điều đó!)
2. **Điều kiện thất bại**: Hết mạng sống và đối mặt với màn hình thất bại
3. **Cơ chế khởi động lại**: Nhấn Enter để quay lại ngay - vì một trò chơi không bao giờ là đủ
4. **Quản lý trạng thái**: Làm mới mọi thứ mỗi lần - không còn kẻ thù sót lại hay lỗi kỳ lạ từ trò chơi trước

## Bắt đầu

Hãy chuẩn bị môi trường phát triển của bạn. Bạn nên có tất cả các tệp trò chơi không gian từ các bài học trước.

**Dự án của bạn nên trông giống như thế này:**

```bash
-| assets
  -| enemyShip.png
  -| player.png
  -| laserRed.png
  -| life.png
-| index.html
-| app.js
-| package.json
```

**Khởi động máy chủ phát triển của bạn:**

```bash
cd your-work
npm start
```

**Lệnh này:**
- Chạy một máy chủ cục bộ trên `http://localhost:5000`
- Phục vụ các tệp của bạn đúng cách
- Tự động làm mới khi bạn thực hiện thay đổi

Mở `http://localhost:5000` trong trình duyệt của bạn và xác nhận trò chơi của bạn đang chạy. Bạn nên có thể di chuyển, bắn và tương tác với kẻ thù. Khi đã xác nhận, chúng ta có thể tiến hành triển khai.

> 💡 **Mẹo chuyên nghiệp**: Để tránh cảnh báo trong Visual Studio Code, khai báo `gameLoopId` ở đầu tệp của bạn dưới dạng `let gameLoopId;` thay vì khai báo nó bên trong hàm `window.onload`. Điều này tuân theo các thực tiễn tốt nhất về khai báo biến trong JavaScript hiện đại.

## Các bước triển khai

### Bước 1: Tạo các hàm theo dõi điều kiện kết thúc

Chúng ta cần các hàm để giám sát khi nào trò chơi nên kết thúc. Giống như các cảm biến trên Trạm Vũ trụ Quốc tế liên tục giám sát các hệ thống quan trọng, các hàm này sẽ liên tục kiểm tra trạng thái trò chơi.

```javascript
function isHeroDead() {
  return hero.life <= 0;
}

function isEnemiesDead() {
  const enemies = gameObjects.filter((go) => go.type === "Enemy" && !go.dead);
  return enemies.length === 0;
}
```

**Đây là những gì đang diễn ra bên trong:**
- **Kiểm tra** nếu anh hùng của chúng ta hết mạng sống (ôi trời!)
- **Đếm** số lượng kẻ thù vẫn còn sống và chiến đấu
- **Trả về** `true` khi chiến trường không còn kẻ thù
- **Sử dụng** logic đơn giản true/false để giữ mọi thứ dễ hiểu
- **Lọc** qua tất cả các đối tượng trò chơi để tìm những kẻ sống sót

### Bước 2: Cập nhật các trình xử lý sự kiện cho điều kiện kết thúc

Bây giờ chúng ta sẽ kết nối các kiểm tra điều kiện này với hệ thống sự kiện của trò chơi. Mỗi khi xảy ra va chạm, trò chơi sẽ đánh giá liệu nó có kích hoạt điều kiện kết thúc hay không. Điều này tạo ra phản hồi ngay lập tức cho các sự kiện quan trọng trong trò chơi.

```javascript
eventEmitter.on(Messages.COLLISION_ENEMY_LASER, (_, { first, second }) => {
    first.dead = true;
    second.dead = true;
    hero.incrementPoints();

    if (isEnemiesDead()) {
      eventEmitter.emit(Messages.GAME_END_WIN);
    }
});

eventEmitter.on(Messages.COLLISION_ENEMY_HERO, (_, { enemy }) => {
    enemy.dead = true;
    hero.decrementLife();
    if (isHeroDead())  {
      eventEmitter.emit(Messages.GAME_END_LOSS);
      return; // loss before victory
    }
    if (isEnemiesDead()) {
      eventEmitter.emit(Messages.GAME_END_WIN);
    }
});

eventEmitter.on(Messages.GAME_END_WIN, () => {
    endGame(true);
});
  
eventEmitter.on(Messages.GAME_END_LOSS, () => {
  endGame(false);
});
```

**Điều gì đang diễn ra ở đây:**
- **Laser bắn trúng kẻ thù**: Cả hai biến mất, bạn nhận được điểm, và chúng ta kiểm tra xem bạn đã thắng chưa
- **Kẻ thù bắn trúng bạn**: Bạn mất một mạng sống, và chúng ta kiểm tra xem bạn còn sống không
- **Thứ tự thông minh**: Chúng ta kiểm tra thất bại trước (không ai muốn vừa thắng vừa thua cùng lúc!)
- **Phản ứng tức thì**: Ngay khi có điều gì quan trọng xảy ra, trò chơi sẽ biết về nó

### Bước 3: Thêm các hằng số thông báo mới

Bạn sẽ cần thêm các loại thông báo mới vào đối tượng hằng số `Messages` của mình. Các hằng số này giúp duy trì tính nhất quán và ngăn chặn lỗi chính tả trong hệ thống sự kiện của bạn.

```javascript
GAME_END_LOSS: "GAME_END_LOSS",
GAME_END_WIN: "GAME_END_WIN",
```

**Trong đoạn trên, chúng ta đã:**
- **Thêm** các hằng số cho các sự kiện kết thúc trò chơi để duy trì tính nhất quán
- **Sử dụng** các tên mô tả rõ ràng mục đích của sự kiện
- **Tuân theo** quy ước đặt tên hiện có cho các loại thông báo

### Bước 4: Triển khai các điều khiển khởi động lại

Bây giờ bạn sẽ thêm các điều khiển bàn phím cho phép người chơi khởi động lại trò chơi. Phím Enter là một lựa chọn tự nhiên vì nó thường được liên kết với việc xác nhận hành động và bắt đầu trò chơi mới.

**Thêm phát hiện phím Enter vào trình nghe sự kiện keydown hiện có của bạn:**

```javascript
else if(evt.key === "Enter") {
   eventEmitter.emit(Messages.KEY_EVENT_ENTER);
}
```

**Thêm hằng số thông báo mới:**

```javascript
KEY_EVENT_ENTER: "KEY_EVENT_ENTER",
```

**Những gì bạn cần biết:**
- **Mở rộng** hệ thống xử lý sự kiện bàn phím hiện có của bạn
- **Sử dụng** phím Enter làm trình kích hoạt khởi động lại để mang lại trải nghiệm người dùng trực quan
- **Phát ra** một sự kiện tùy chỉnh mà các phần khác của trò chơi có thể lắng nghe
- **Duy trì** cùng một mẫu như các điều khiển bàn phím khác của bạn

### Bước 5: Tạo hệ thống hiển thị thông báo

Trò chơi của bạn cần giao tiếp kết quả rõ ràng với người chơi. Chúng ta sẽ tạo một hệ thống thông báo hiển thị trạng thái chiến thắng và thất bại bằng văn bản được mã hóa màu, tương tự như giao diện terminal của các hệ thống máy tính đầu tiên, nơi màu xanh lá cây biểu thị thành công và màu đỏ báo hiệu lỗi.

**Tạo hàm `displayMessage()`:**

```javascript
function displayMessage(message, color = "red") {
  ctx.font = "30px Arial";
  ctx.fillStyle = color;
  ctx.textAlign = "center";
  ctx.fillText(message, canvas.width / 2, canvas.height / 2);
}
```

**Từng bước, đây là những gì đang diễn ra:**
- **Đặt** kích thước và kiểu phông chữ để văn bản rõ ràng, dễ đọc
- **Áp dụng** tham số màu với "red" làm mặc định cho cảnh báo
- **Căn giữa** văn bản theo chiều ngang và dọc trên canvas
- **Sử dụng** các tham số mặc định hiện đại của JavaScript để tùy chỉnh màu sắc linh hoạt
- **Tận dụng** ngữ cảnh 2D của canvas để hiển thị văn bản trực tiếp

**Tạo hàm `endGame()`:**

```javascript
function endGame(win) {
  clearInterval(gameLoopId);

  // Set a delay to ensure any pending renders complete
  setTimeout(() => {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "black";
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    if (win) {
      displayMessage(
        "Victory!!! Pew Pew... - Press [Enter] to start a new game Captain Pew Pew",
        "green"
      );
    } else {
      displayMessage(
        "You died !!! Press [Enter] to start a new game Captain Pew Pew"
      );
    }
  }, 200)  
}
```

**Hàm này làm gì:**
- **Đóng băng** mọi thứ tại chỗ - không còn tàu hoặc tia laser di chuyển
- **Tạm dừng** một chút (200ms) để khung hình cuối cùng hoàn thành vẽ
- **Xóa** màn hình và tô màu đen để tạo hiệu ứng kịch tính
- **Hiển thị** các thông báo khác nhau cho người thắng và người thua
- **Mã hóa màu** tin tức - xanh cho tốt, đỏ cho... không tốt lắm
- **Thông báo** cho người chơi cách quay lại trò chơi

### Bước 6: Triển khai chức năng đặt lại trò chơi

Hệ thống đặt lại cần hoàn toàn dọn dẹp trạng thái trò chơi hiện tại và khởi tạo một phiên trò chơi mới. Điều này đảm bảo người chơi có một khởi đầu sạch sẽ mà không có bất kỳ dữ liệu dư thừa nào từ trò chơi trước.

**Tạo hàm `resetGame()`:**

```javascript
function resetGame() {
  if (gameLoopId) {
    clearInterval(gameLoopId);
    eventEmitter.clear();
    initGame();
    gameLoopId = setInterval(() => {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "black";
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      drawPoints();
      drawLife();
      updateGameObjects();
      drawGameObjects(ctx);
    }, 100);
  }
}
```

**Hãy hiểu từng phần:**
- **Kiểm tra** nếu một vòng lặp trò chơi hiện đang chạy trước khi đặt lại
- **Xóa** vòng lặp trò chơi hiện tại để dừng tất cả hoạt động trò chơi hiện tại
- **Loại bỏ** tất cả các trình nghe sự kiện để ngăn rò rỉ bộ nhớ
- **Khởi tạo lại** trạng thái trò chơi với các đối tượng và biến mới
- **Bắt đầu** một vòng lặp trò chơi mới với tất cả các chức năng trò chơi cần thiết
- **Duy trì** cùng khoảng thời gian 100ms để đảm bảo hiệu suất trò chơi nhất quán

**Thêm trình xử lý sự kiện phím Enter vào hàm `initGame()`:**

```javascript
eventEmitter.on(Messages.KEY_EVENT_ENTER, () => {
  resetGame();
});
```

**Thêm phương thức `clear()` vào lớp EventEmitter của bạn:**

```javascript
clear() {
  this.listeners = {};
}
```

**Những điểm chính cần nhớ:**
- **Kết nối** việc nhấn phím Enter với chức năng đặt lại trò chơi
- **Đăng ký** trình nghe sự kiện này trong quá trình khởi tạo trò chơi
- **Cung cấp** cách sạch sẽ để loại bỏ tất cả các trình nghe sự kiện khi đặt lại
- **Ngăn chặn** rò rỉ bộ nhớ bằng cách xóa các trình xử lý sự kiện giữa các trò chơi
- **Đặt lại** đối tượng listeners về trạng thái trống để khởi tạo mới

## Chúc mừng! 🎉

👽 💥 🚀 Bạn đã xây dựng thành công một trò chơi hoàn chỉnh từ đầu. Giống như các lập trình viên đã tạo ra các trò chơi video đầu tiên vào những năm 1970, bạn đã biến các dòng mã thành một trải nghiệm tương tác với cơ chế trò chơi và phản hồi người dùng đúng cách. 🚀 💥 👽

**Bạn đã hoàn thành:**
- **Triển khai** các điều kiện thắng và thua hoàn chỉnh với phản hồi người dùng
- **Tạo** hệ thống khởi động lại mượt mà cho lối chơi liên tục
- **Thiết kế** giao tiếp hình ảnh rõ ràng cho các trạng thái trò chơi
- **Quản lý** các chuyển đổi trạng thái trò chơi phức tạp và dọn dẹp
- **Lắp ráp** tất cả các thành phần thành một trò chơi hoàn chỉnh, có thể chơi được

## Thử thách GitHub Copilot Agent 🚀

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Nâng cấp trò chơi không gian bằng cách triển khai hệ thống tiến cấp với độ khó tăng dần và các tính năng thưởng.

**Yêu cầu:** Tạo hệ thống trò chơi nhiều cấp độ, trong đó mỗi cấp độ có nhiều tàu địch hơn với tốc độ và sức khỏe tăng lên. Thêm hệ số nhân điểm số tăng lên theo từng cấp độ, và triển khai các vật phẩm hỗ trợ (như bắn nhanh hoặc lá chắn) xuất hiện ngẫu nhiên khi kẻ thù bị tiêu diệt. Bao gồm phần thưởng hoàn thành cấp độ và hiển thị cấp độ hiện tại trên màn hình cùng với điểm số và mạng sống hiện có.

Tìm hiểu thêm về [chế độ agent](https://code.visualstudio.com/blogs/2025/02/24/introducing-copilot-agent-mode) tại đây.

## 🚀 Thử thách nâng cao tùy chọn

**Thêm âm thanh vào trò chơi của bạn**: Nâng cao trải nghiệm chơi trò chơi bằng cách triển khai hiệu ứng âm thanh! Hãy cân nhắc thêm âm thanh cho:

- **Bắn tia laser** khi người chơi bắn
- **Tiêu diệt kẻ thù** khi tàu bị bắn trúng
- **Thiệt hại của anh hùng** khi người chơi bị tấn công
- **Nhạc chiến thắng** khi trò chơi được thắng
- **Âm thanh thất bại** khi trò chơi bị thua

**Ví dụ triển khai âm thanh:**

```javascript
// Create audio objects
const laserSound = new Audio('assets/laser.wav');
const explosionSound = new Audio('assets/explosion.wav');

// Play sounds during game events
function playLaserSound() {
  laserSound.currentTime = 0; // Reset to beginning
  laserSound.play();
}
```

**Những gì bạn cần biết:**
- **Tạo** các đối tượng âm thanh cho các hiệu ứng âm thanh khác nhau
- **Đặt lại** `currentTime` để cho phép hiệu ứng âm thanh bắn nhanh
- **Xử lý** các chính sách tự động phát của trình duyệt bằng cách kích hoạt âm thanh từ các tương tác của người dùng
- **Quản lý** âm lượng và thời gian âm thanh để cải thiện trải nghiệm trò chơi

> 💡 **Tài nguyên học tập**: Khám phá [audio sandbox](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_audio_play) này để tìm hiểu thêm về việc triển khai âm thanh trong các trò chơi JavaScript.

## Câu hỏi sau bài giảng

[Câu hỏi sau bài giảng](https://ff-quizzes.netlify.app/web/quiz/40)

## Ôn tập & Tự học

Bài tập của bạn là tạo một trò chơi mẫu mới, vì vậy hãy khám phá một số trò chơi thú vị ngoài kia để xem bạn có thể xây dựng loại trò chơi nào.

## Bài tập

[Xây dựng một trò chơi mẫu](assignment.md)

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.