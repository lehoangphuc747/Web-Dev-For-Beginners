<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4b1d441cfd31924084956000c0fee5a5",
  "translation_date": "2025-10-24T13:51:27+00:00",
  "source_file": "6-space-game/4-collision-detection/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../../README.md) | [◀️ Quay lại](../README.md) | [▶️ Bài tiếp theo](../5-keeping-score/README.md)

---
# Xây dựng trò chơi không gian Phần 4: Thêm tia laser và phát hiện va chạm

## Câu hỏi trước bài giảng

[Quiz trước bài giảng](https://ff-quizzes.netlify.app/web/quiz/35)

Hãy nghĩ về khoảnh khắc trong Star Wars khi Luke bắn torpedo proton vào cổng xả của Death Star. Việc phát hiện va chạm chính xác đó đã thay đổi số phận của cả thiên hà! Trong trò chơi, phát hiện va chạm hoạt động tương tự - nó xác định khi nào các đối tượng tương tác và điều gì sẽ xảy ra tiếp theo.

Trong bài học này, bạn sẽ thêm vũ khí laser vào trò chơi không gian của mình và triển khai phát hiện va chạm. Giống như các nhà hoạch định nhiệm vụ của NASA tính toán quỹ đạo tàu vũ trụ để tránh mảnh vỡ, bạn sẽ học cách phát hiện khi các đối tượng trong trò chơi giao nhau. Chúng ta sẽ chia nhỏ thành các bước dễ quản lý để xây dựng dần.

Kết thúc bài học, bạn sẽ có một hệ thống chiến đấu hoạt động, nơi tia laser tiêu diệt kẻ thù và va chạm kích hoạt các sự kiện trong trò chơi. Những nguyên tắc phát hiện va chạm này cũng được sử dụng trong mọi thứ từ mô phỏng vật lý đến giao diện web tương tác.

✅ Tìm hiểu một chút về trò chơi máy tính đầu tiên từng được viết. Chức năng của nó là gì?

## Phát hiện va chạm

Phát hiện va chạm hoạt động giống như các cảm biến gần của module Apollo - nó liên tục kiểm tra khoảng cách và kích hoạt cảnh báo khi các đối tượng đến quá gần. Trong trò chơi, hệ thống này xác định khi nào các đối tượng tương tác và điều gì nên xảy ra tiếp theo.

Phương pháp chúng ta sẽ sử dụng coi mỗi đối tượng trong trò chơi như một hình chữ nhật, tương tự như cách các hệ thống kiểm soát không lưu sử dụng các hình dạng hình học đơn giản để theo dõi máy bay. Phương pháp hình chữ nhật này có vẻ cơ bản, nhưng nó hiệu quả về mặt tính toán và hoạt động tốt cho hầu hết các kịch bản trò chơi.

### Đại diện hình chữ nhật

Mỗi đối tượng trong trò chơi cần có các giới hạn tọa độ, giống như cách rover Mars Pathfinder lập bản đồ vị trí của nó trên bề mặt sao Hỏa. Đây là cách chúng ta định nghĩa các tọa độ giới hạn này:

```javascript
rectFromGameObject() {
  return {
    top: this.y,
    left: this.x,
    bottom: this.y + this.height,
    right: this.x + this.width
  }
}
```

**Phân tích:**
- **Cạnh trên**: Đó là nơi đối tượng của bạn bắt đầu theo chiều dọc (vị trí y của nó)
- **Cạnh trái**: Nơi nó bắt đầu theo chiều ngang (vị trí x của nó)
- **Cạnh dưới**: Cộng chiều cao vào vị trí y - bây giờ bạn biết nơi nó kết thúc!
- **Cạnh phải**: Cộng chiều rộng vào vị trí x - và bạn đã có giới hạn hoàn chỉnh

### Thuật toán giao nhau

Phát hiện giao nhau của hình chữ nhật sử dụng logic tương tự như cách Kính viễn vọng không gian Hubble xác định liệu các đối tượng thiên thể có chồng chéo trong trường quan sát của nó hay không. Thuật toán kiểm tra sự tách biệt:

```javascript
function intersectRect(r1, r2) {
  return !(r2.left > r1.right ||
    r2.right < r1.left ||
    r2.top > r1.bottom ||
    r2.bottom < r1.top);
}
```

**Kiểm tra sự tách biệt hoạt động giống như hệ thống radar:**
- Hình chữ nhật 2 hoàn toàn nằm bên phải hình chữ nhật 1?
- Hình chữ nhật 2 hoàn toàn nằm bên trái hình chữ nhật 1?
- Hình chữ nhật 2 hoàn toàn nằm dưới hình chữ nhật 1?
- Hình chữ nhật 2 hoàn toàn nằm trên hình chữ nhật 1?

Nếu không có điều kiện nào trong số này đúng, các hình chữ nhật phải chồng chéo. Phương pháp này giống như cách các nhà điều hành radar xác định liệu hai máy bay có ở khoảng cách an toàn hay không.

## Quản lý vòng đời đối tượng

Khi tia laser bắn trúng kẻ thù, cả hai đối tượng cần được loại bỏ khỏi trò chơi. Tuy nhiên, việc xóa đối tượng giữa vòng lặp có thể gây ra lỗi - một bài học được rút ra từ các hệ thống máy tính ban đầu như Apollo Guidance Computer. Thay vào đó, chúng ta sử dụng phương pháp "đánh dấu để xóa" để loại bỏ đối tượng một cách an toàn giữa các khung hình.

Đây là cách chúng ta đánh dấu một đối tượng để xóa:

```javascript
// Mark object for removal
enemy.dead = true;
```

**Tại sao phương pháp này hoạt động:**
- Chúng ta đánh dấu đối tượng là "đã chết" nhưng không xóa ngay lập tức
- Điều này cho phép khung hình hiện tại của trò chơi hoàn thành một cách an toàn
- Không có lỗi từ việc cố gắng sử dụng thứ gì đó đã bị xóa!

Sau đó lọc ra các đối tượng đã được đánh dấu trước chu kỳ render tiếp theo:

```javascript
gameObjects = gameObjects.filter(go => !go.dead);
```

**Điều mà việc lọc này làm:**
- Tạo danh sách mới chỉ với các đối tượng "còn sống"
- Loại bỏ bất cứ thứ gì đã được đánh dấu là chết
- Giữ cho trò chơi của bạn chạy mượt mà
- Ngăn chặn việc tích tụ bộ nhớ từ các đối tượng bị phá hủy

## Triển khai cơ chế laser

Các tia laser trong trò chơi hoạt động theo nguyên tắc giống như torpedo photon trong Star Trek - chúng là các đối tượng riêng biệt di chuyển theo đường thẳng cho đến khi va chạm với thứ gì đó. Mỗi lần nhấn phím cách sẽ tạo ra một đối tượng laser mới di chuyển trên màn hình.

Để làm điều này, chúng ta cần phối hợp một vài phần khác nhau:

**Các thành phần chính cần triển khai:**
- **Tạo** các đối tượng laser xuất hiện từ vị trí của nhân vật chính
- **Xử lý** đầu vào từ bàn phím để kích hoạt việc tạo laser
- **Quản lý** chuyển động và vòng đời của laser
- **Triển khai** hình ảnh đại diện cho các tia laser

## Triển khai kiểm soát tốc độ bắn

Tốc độ bắn không giới hạn sẽ làm quá tải động cơ trò chơi và khiến trò chơi trở nên quá dễ dàng. Các hệ thống vũ khí thực tế cũng đối mặt với những hạn chế tương tự - ngay cả phasers của USS Enterprise cũng cần thời gian để nạp lại giữa các lần bắn.

Chúng ta sẽ triển khai hệ thống làm mát để ngăn chặn việc bắn liên tục trong khi vẫn duy trì điều khiển nhạy:

```javascript
class Cooldown {
  constructor(time) {
    this.cool = false;
    setTimeout(() => {
      this.cool = true;
    }, time);
  }
}

class Weapon {
  constructor() {
    this.cooldown = null;
  }
  
  fire() {
    if (!this.cooldown || this.cooldown.cool) {
      // Create laser projectile
      this.cooldown = new Cooldown(500);
    } else {
      // Weapon is still cooling down
    }
  }
}
```

**Cách hệ thống làm mát hoạt động:**
- Khi được tạo, vũ khí bắt đầu "nóng" (chưa thể bắn)
- Sau khoảng thời gian chờ, nó trở thành "mát" (sẵn sàng bắn)
- Trước khi bắn, chúng ta kiểm tra: "Vũ khí đã mát chưa?"
- Điều này ngăn chặn việc nhấn chuột liên tục trong khi vẫn giữ điều khiển nhạy

✅ Tham khảo bài học 1 trong loạt bài trò chơi không gian để nhắc lại về hệ thống làm mát.

## Xây dựng hệ thống phát hiện va chạm

Bạn sẽ mở rộng mã trò chơi không gian hiện có của mình để tạo hệ thống phát hiện va chạm. Giống như hệ thống tránh va chạm tự động của Trạm Vũ trụ Quốc tế, trò chơi của bạn sẽ liên tục theo dõi vị trí của các đối tượng và phản hồi khi có giao nhau.

Bắt đầu từ mã bài học trước, bạn sẽ thêm phát hiện va chạm với các quy tắc cụ thể điều chỉnh tương tác giữa các đối tượng.

> 💡 **Mẹo chuyên nghiệp**: Sprite laser đã được bao gồm trong thư mục tài nguyên của bạn và được tham chiếu trong mã, sẵn sàng để triển khai.

### Quy tắc va chạm cần triển khai

**Cơ chế trò chơi cần thêm:**
1. **Laser bắn trúng kẻ thù**: Đối tượng kẻ thù bị phá hủy khi bị tia laser bắn trúng
2. **Laser chạm vào ranh giới màn hình**: Tia laser bị loại bỏ khi chạm đến cạnh trên của màn hình
3. **Kẻ thù va chạm với nhân vật chính**: Cả hai đối tượng bị phá hủy khi chúng giao nhau
4. **Kẻ thù chạm đáy**: Điều kiện kết thúc trò chơi khi kẻ thù chạm đáy màn hình

## Thiết lập môi trường phát triển

Tin tốt - chúng tôi đã thiết lập hầu hết các nền tảng cho bạn! Tất cả tài nguyên trò chơi và cấu trúc cơ bản của bạn đang chờ trong thư mục `your-work`, sẵn sàng để bạn thêm các tính năng phát hiện va chạm thú vị.

### Cấu trúc dự án

```bash
-| assets
  -| enemyShip.png
  -| player.png
  -| laserRed.png
-| index.html
-| app.js
-| package.json
```

**Hiểu cấu trúc tệp:**
- **Chứa** tất cả hình ảnh sprite cần thiết cho các đối tượng trò chơi
- **Bao gồm** tài liệu HTML chính và tệp ứng dụng JavaScript
- **Cung cấp** cấu hình gói cho máy chủ phát triển cục bộ

### Bắt đầu máy chủ phát triển

Điều hướng đến thư mục dự án của bạn và khởi động máy chủ cục bộ:

```bash
cd your-work
npm start
```

**Trình tự lệnh này:**
- **Thay đổi** thư mục sang thư mục dự án của bạn
- **Khởi động** máy chủ HTTP cục bộ tại `http://localhost:5000`
- **Phục vụ** các tệp trò chơi của bạn để thử nghiệm và phát triển
- **Cho phép** phát triển trực tiếp với khả năng tải lại tự động

Mở trình duyệt của bạn và điều hướng đến `http://localhost:5000` để xem trạng thái hiện tại của trò chơi với nhân vật chính và kẻ thù được hiển thị trên màn hình.

### Triển khai từng bước

Giống như cách tiếp cận có hệ thống NASA đã sử dụng để lập trình tàu vũ trụ Voyager, chúng ta sẽ triển khai phát hiện va chạm một cách có phương pháp, xây dựng từng thành phần từng bước.

#### 1. Thêm giới hạn va chạm hình chữ nhật

Đầu tiên, hãy dạy các đối tượng trò chơi cách mô tả giới hạn của chúng. Thêm phương pháp này vào lớp `GameObject` của bạn:

```javascript
rectFromGameObject() {
    return {
      top: this.y,
      left: this.x,
      bottom: this.y + this.height,
      right: this.x + this.width,
    };
  }
```

**Phương pháp này đạt được:**
- **Tạo** một đối tượng hình chữ nhật với các tọa độ giới hạn chính xác
- **Tính toán** cạnh dưới và cạnh phải bằng cách sử dụng vị trí cộng kích thước
- **Trả về** một đối tượng sẵn sàng cho các thuật toán phát hiện va chạm
- **Cung cấp** giao diện chuẩn hóa cho tất cả các đối tượng trò chơi

#### 2. Triển khai phát hiện giao nhau

Bây giờ hãy tạo "thám tử va chạm" của chúng ta - một hàm có thể xác định khi hai hình chữ nhật chồng chéo:

```javascript
function intersectRect(r1, r2) {
  return !(
    r2.left > r1.right ||
    r2.right < r1.left ||
    r2.top > r1.bottom ||
    r2.bottom < r1.top
  );
}
```

**Thuật toán này hoạt động bằng cách:**
- **Kiểm tra** bốn điều kiện tách biệt giữa các hình chữ nhật
- **Trả về** `false` nếu bất kỳ điều kiện tách biệt nào đúng
- **Chỉ ra** va chạm khi không có sự tách biệt
- **Sử dụng** logic phủ định để kiểm tra giao nhau hiệu quả

#### 3. Triển khai hệ thống bắn laser

Đây là lúc mọi thứ trở nên thú vị! Hãy thiết lập hệ thống bắn laser.

##### Hằng số thông báo

Đầu tiên, hãy định nghĩa một số loại thông báo để các phần khác nhau của trò chơi có thể giao tiếp với nhau:

```javascript
KEY_EVENT_SPACE: "KEY_EVENT_SPACE",
COLLISION_ENEMY_LASER: "COLLISION_ENEMY_LASER",
COLLISION_ENEMY_HERO: "COLLISION_ENEMY_HERO",
```

**Các hằng số này cung cấp:**
- **Chuẩn hóa** tên sự kiện trong toàn bộ ứng dụng
- **Cho phép** giao tiếp nhất quán giữa các hệ thống trò chơi
- **Ngăn chặn** lỗi chính tả trong việc đăng ký xử lý sự kiện

##### Xử lý đầu vào từ bàn phím

Thêm phát hiện phím cách vào trình lắng nghe sự kiện phím của bạn:

```javascript
} else if(evt.keyCode === 32) {
  eventEmitter.emit(Messages.KEY_EVENT_SPACE);
}
```

**Trình xử lý đầu vào này:**
- **Phát hiện** nhấn phím cách bằng cách sử dụng keyCode 32
- **Phát ra** một thông báo sự kiện chuẩn hóa
- **Cho phép** logic bắn tách biệt

##### Thiết lập trình lắng nghe sự kiện

Đăng ký hành vi bắn trong hàm `initGame()` của bạn:

```javascript
eventEmitter.on(Messages.KEY_EVENT_SPACE, () => {
 if (hero.canFire()) {
   hero.fire();
 }
});
```

**Trình lắng nghe sự kiện này:**
- **Phản hồi** các sự kiện phím cách
- **Kiểm tra** trạng thái làm mát của vũ khí
- **Kích hoạt** việc tạo laser khi được phép

Thêm xử lý va chạm cho tương tác giữa laser và kẻ thù:

```javascript
eventEmitter.on(Messages.COLLISION_ENEMY_LASER, (_, { first, second }) => {
  first.dead = true;
  second.dead = true;
});
```

**Trình xử lý va chạm này:**
- **Nhận** dữ liệu sự kiện va chạm với cả hai đối tượng
- **Đánh dấu** cả hai đối tượng để xóa
- **Đảm bảo** dọn dẹp đúng cách sau va chạm

#### 4. Tạo lớp Laser

Triển khai một tia laser di chuyển lên trên và quản lý vòng đời của nó:

```javascript
class Laser extends GameObject {
  constructor(x, y) {
    super(x, y);
    this.width = 9;
    this.height = 33;
    this.type = 'Laser';
    this.img = laserImg;
    
    let id = setInterval(() => {
      if (this.y > 0) {
        this.y -= 15;
      } else {
        this.dead = true;
        clearInterval(id);
      }
    }, 100);
  }
}
```

**Triển khai lớp này:**
- **Mở rộng** GameObject để kế thừa chức năng cơ bản
- **Đặt** kích thước phù hợp cho sprite laser
- **Tạo** chuyển động lên tự động bằng cách sử dụng `setInterval()`
- **Xử lý** tự hủy khi chạm đến cạnh trên màn hình
- **Quản lý** thời gian hoạt hình và dọn dẹp của chính nó

#### 5. Triển khai hệ thống phát hiện va chạm

Tạo một hàm phát hiện va chạm toàn diện:

```javascript
function updateGameObjects() {
  const enemies = gameObjects.filter(go => go.type === 'Enemy');
  const lasers = gameObjects.filter(go => go.type === "Laser");
  
  // Test laser-enemy collisions
  lasers.forEach((laser) => {
    enemies.forEach((enemy) => {
      if (intersectRect(laser.rectFromGameObject(), enemy.rectFromGameObject())) {
        eventEmitter.emit(Messages.COLLISION_ENEMY_LASER, {
          first: laser,
          second: enemy,
        });
      }
    });
  });

  // Remove destroyed objects
  gameObjects = gameObjects.filter(go => !go.dead);
}
```

**Hệ thống va chạm này:**
- **Lọc** các đối tượng trò chơi theo loại để kiểm tra hiệu quả
- **Kiểm tra** mỗi laser với mỗi kẻ thù để tìm giao nhau
- **Phát ra** các sự kiện va chạm khi phát hiện giao nhau
- **Dọn dẹp** các đối tượng bị phá hủy sau khi xử lý va chạm

> ⚠️ **Quan trọng**: Thêm `updateGameObjects()` vào vòng lặp trò chơi chính của bạn trong `window.onload` để kích hoạt phát hiện va chạm.

#### 6. Thêm hệ thống làm mát vào lớp Hero

Nâng cấp lớp Hero với cơ chế bắn và giới hạn tốc độ:

```javascript
class Hero extends GameObject {
  constructor(x, y) {
    super(x, y);
    this.width = 99;
    this.height = 75;
    this.type = "Hero";
    this.speed = { x: 0, y: 0 };
    this.cooldown = 0;
  }
  
  fire() {
    gameObjects.push(new Laser(this.x + 45, this.y - 10));
    this.cooldown = 500;

    let id = setInterval(() => {
      if (this.cooldown > 0) {
        this.cooldown -= 100;
      } else {
        clearInterval(id);
      }
    }, 200);
  }
  
  canFire() {
    return this.cooldown === 0;
  }
}
```

**Hiểu lớp Hero được nâng cấp:**
- **Khởi tạo** bộ đếm thời gian làm mát ở mức 0 (sẵn sàng bắn)
- **Tạo** các đối tượng laser được đặt phía trên tàu của nhân vật chính
- **Đặt** khoảng thời gian làm mát để ngăn chặn việc bắn liên tục
- **Giảm** bộ đếm thời gian làm mát bằng các cập nhật dựa trên khoảng thời gian
- **Cung cấp** kiểm tra trạng thái bắn thông qua phương pháp `canFire()`

### Kiểm tra triển khai của bạn

Trò chơi không gian của bạn giờ đây có tính năng phát hiện va chạm hoàn chỉnh và cơ chế chiến đấu. 🚀 Kiểm tra các khả năng mới này:
- **Di chuyển** bằng các phím mũi tên để kiểm tra điều khiển di chuyển
- **Bắn laser** bằng phím cách - chú ý cách hệ thống làm mát ngăn chặn việc nhấn liên tục
- **Quan sát va chạm** khi laser bắn trúng kẻ thù, kích hoạt việc loại bỏ
- **Kiểm tra dọn dẹp** khi các đối tượng bị phá hủy biến mất khỏi trò chơi

Bạn đã triển khai thành công hệ thống phát hiện va chạm bằng các nguyên tắc toán học giống như hướng dẫn điều hướng tàu vũ trụ và robot.

## Thử thách GitHub Copilot Agent 🚀

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Nâng cấp hệ thống phát hiện va chạm bằng cách triển khai các vật phẩm tăng cường xuất hiện ngẫu nhiên và cung cấp khả năng tạm thời khi được nhân vật chính thu thập.

**Yêu cầu:** Tạo một lớp PowerUp mở rộng GameObject và triển khai phát hiện va chạm giữa nhân vật chính và các vật phẩm tăng cường. Thêm ít nhất hai loại vật phẩm tăng cường: một loại tăng tốc độ bắn (giảm thời gian làm mát) và một loại tạo lá chắn tạm thời. Bao gồm logic xuất hiện tạo các vật phẩm tăng cường tại các khoảng thời gian và vị trí ngẫu nhiên.

---



## 🚀 Thử thách

Thêm hiệu ứng nổ! Xem các tài nguyên trò chơi trong [repo Space Art](../../../../6-space-game/solution/spaceArt/readme.txt) và thử thêm hiệu ứng nổ khi tia laser bắn trúng người ngoài hành tinh.

## Câu hỏi sau bài giảng

[Quiz sau bài giảng](https://ff-quizzes.netlify.app/web/quiz/36)

## Ôn tập & Tự học

Thử nghiệm với các khoảng thời gian trong trò chơi của bạn cho đến nay. Điều gì xảy ra khi bạn thay đổi chúng? Đọc thêm về [sự kiện thời gian trong JavaScript](https://www.freecodecamp.org/news/javascript-timing-events-settimeout-and-setinterval/).

## Bài tập

[Khám phá va chạm](assignment.md)

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.