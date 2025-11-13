<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "20c72cf2e5b0050d38ca3cb14a75a9df",
  "translation_date": "2025-10-24T13:41:18+00:00",
  "source_file": "3-terrarium/1-intro-to-html/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../../README.md) | [◀️ Quay lại](../README.md) | [▶️ Bài tiếp theo](../2-intro-to-css/README.md)

---
# Dự án Terrarium Phần 1: Giới thiệu về HTML

![Giới thiệu về HTML](../../../../translated_images/webdev101-html.4389c2067af68e98280c1bde52b6c6269f399eaae3659b7c846018d8a7b0bbd9.vi.png)
> Sketchnote bởi [Tomomi Imura](https://twitter.com/girlie_mac)

HTML, hay HyperText Markup Language, là nền tảng của mọi trang web mà bạn từng truy cập. Hãy nghĩ về HTML như bộ khung xương giúp định hình cấu trúc cho các trang web – nó xác định vị trí nội dung, cách tổ chức và ý nghĩa của từng phần. Trong khi CSS sẽ "trang trí" HTML với màu sắc và bố cục, và JavaScript sẽ làm cho nó sống động với tính tương tác, HTML cung cấp cấu trúc cơ bản để mọi thứ khác có thể hoạt động.

Trong bài học này, bạn sẽ tạo cấu trúc HTML cho giao diện terrarium ảo. Dự án thực hành này sẽ giúp bạn nắm vững các khái niệm cơ bản về HTML trong khi xây dựng một thứ gì đó hấp dẫn về mặt hình ảnh. Bạn sẽ học cách tổ chức nội dung bằng các phần tử ngữ nghĩa, làm việc với hình ảnh và tạo nền tảng cho một ứng dụng web tương tác.

Kết thúc bài học này, bạn sẽ có một trang HTML hoạt động hiển thị hình ảnh cây cối trong các cột được tổ chức, sẵn sàng để thêm phong cách trong bài học tiếp theo. Đừng lo nếu ban đầu nó trông đơn giản – đó chính xác là những gì HTML nên làm trước khi CSS thêm sự tinh tế về mặt hình ảnh.

## Câu hỏi trước bài học

[Câu hỏi trước bài học](https://ff-quizzes.netlify.app/web/quiz/15)

> 📺 **Xem và học**: Xem video tổng quan hữu ích này
> 
> [![Video Cơ bản về HTML](https://img.youtube.com/vi/1TvxJKBzhyQ/0.jpg)](https://www.youtube.com/watch?v=1TvxJKBzhyQ)

## Thiết lập dự án của bạn

Trước khi đi sâu vào mã HTML, hãy thiết lập một không gian làm việc phù hợp cho dự án terrarium của bạn. Tạo một cấu trúc tệp được tổ chức từ đầu là một thói quen quan trọng sẽ giúp bạn rất nhiều trong suốt hành trình phát triển web.

### Nhiệm vụ: Tạo cấu trúc dự án của bạn

Bạn sẽ tạo một thư mục dành riêng cho dự án terrarium và thêm tệp HTML đầu tiên của mình. Dưới đây là hai cách bạn có thể sử dụng:

**Cách 1: Sử dụng Visual Studio Code**
1. Mở Visual Studio Code
2. Nhấp vào "File" → "Open Folder" hoặc sử dụng `Ctrl+K, Ctrl+O` (Windows/Linux) hoặc `Cmd+K, Cmd+O` (Mac)
3. Tạo một thư mục mới tên là `terrarium` và chọn nó
4. Trong bảng Explorer, nhấp vào biểu tượng "New File"
5. Đặt tên tệp của bạn là `index.html`

![VS Code Explorer hiển thị việc tạo tệp mới](../../../../translated_images/vs-code-index.e2986cf919471eb984a0afef231380c8b132b000635105f2397bd2754d1b689c.vi.png)

**Cách 2: Sử dụng lệnh Terminal**
```bash
mkdir terrarium
cd terrarium
touch index.html
code index.html
```

**Những gì các lệnh này thực hiện:**
- **Tạo** một thư mục mới tên là `terrarium` cho dự án của bạn
- **Chuyển đến** thư mục terrarium
- **Tạo** một tệp `index.html` trống
- **Mở** tệp trong Visual Studio Code để chỉnh sửa

> 💡 **Mẹo chuyên nghiệp**: Tên tệp `index.html` rất đặc biệt trong phát triển web. Khi ai đó truy cập một trang web, trình duyệt tự động tìm kiếm `index.html` làm trang mặc định để hiển thị. Điều này có nghĩa là một URL như `https://mysite.com/projects/` sẽ tự động phục vụ tệp `index.html` từ thư mục `projects` mà không cần chỉ định tên tệp trong URL.

## Hiểu cấu trúc tài liệu HTML

Mỗi tài liệu HTML tuân theo một cấu trúc cụ thể mà trình duyệt cần để hiểu và hiển thị chính xác. Hãy nghĩ về cấu trúc này như một lá thư chính thức – nó có các phần tử bắt buộc theo một thứ tự cụ thể giúp người nhận (trong trường hợp này là trình duyệt) xử lý nội dung đúng cách.

Hãy bắt đầu bằng cách thêm nền tảng cần thiết mà mọi tài liệu HTML cần có.

### Khai báo DOCTYPE và phần tử gốc

Hai dòng đầu tiên của bất kỳ tệp HTML nào đóng vai trò như "giới thiệu" của tài liệu với trình duyệt:

```html
<!DOCTYPE html>
<html></html>
```

**Hiểu những gì mã này làm:**
- **Khai báo** loại tài liệu là HTML5 bằng `<!DOCTYPE html>`
- **Tạo** phần tử gốc `<html>` sẽ chứa tất cả nội dung trang
- **Thiết lập** các tiêu chuẩn web hiện đại để trình duyệt hiển thị đúng cách
- **Đảm bảo** hiển thị nhất quán trên các trình duyệt và thiết bị khác nhau

> 💡 **Mẹo VS Code**: Di chuột qua bất kỳ thẻ HTML nào trong VS Code để xem thông tin hữu ích từ MDN Web Docs, bao gồm các ví dụ sử dụng và chi tiết về khả năng tương thích trình duyệt.

> 📚 **Tìm hiểu thêm**: Khai báo DOCTYPE ngăn trình duyệt vào chế độ "quirks mode", được sử dụng để hỗ trợ các trang web rất cũ. Phát triển web hiện đại sử dụng khai báo đơn giản `<!DOCTYPE html>` để đảm bảo [hiển thị tuân thủ tiêu chuẩn](https://developer.mozilla.org/docs/Web/HTML/Quirks_Mode_and_Standards_Mode).

## Thêm siêu dữ liệu cần thiết cho tài liệu

Phần `<head>` của tài liệu HTML chứa thông tin quan trọng mà trình duyệt và công cụ tìm kiếm cần, nhưng khách truy cập không thấy trực tiếp trên trang. Hãy nghĩ về nó như thông tin "hậu trường" giúp trang web của bạn hoạt động đúng và hiển thị chính xác trên các thiết bị và nền tảng khác nhau.

Siêu dữ liệu này cho trình duyệt biết cách hiển thị trang của bạn, mã hóa ký tự nào cần sử dụng và cách xử lý các kích thước màn hình khác nhau – tất cả đều cần thiết để tạo các trang web chuyên nghiệp, dễ truy cập.

### Nhiệm vụ: Thêm phần đầu tài liệu

Chèn phần `<head>` này giữa các thẻ `<html>` mở và đóng của bạn:

```html
<head>
	<title>Welcome to my Virtual Terrarium</title>
	<meta charset="utf-8" />
	<meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
</head>
```

**Phân tích những gì mỗi phần tử thực hiện:**
- **Đặt** tiêu đề trang xuất hiện trong tab trình duyệt và kết quả tìm kiếm
- **Chỉ định** mã hóa ký tự UTF-8 để hiển thị văn bản đúng cách trên toàn thế giới
- **Đảm bảo** tương thích với các phiên bản hiện đại của Internet Explorer
- **Cấu hình** thiết kế đáp ứng bằng cách đặt viewport phù hợp với chiều rộng thiết bị
- **Kiểm soát** mức độ phóng ban đầu để hiển thị nội dung ở kích thước tự nhiên

> 🤔 **Suy nghĩ về điều này**: Điều gì sẽ xảy ra nếu bạn đặt thẻ meta viewport như thế này: `<meta name="viewport" content="width=600">`? Điều này sẽ buộc trang luôn rộng 600 pixel, phá vỡ thiết kế đáp ứng! Tìm hiểu thêm về [cấu hình viewport đúng cách](https://developer.mozilla.org/docs/Web/HTML/Viewport_meta_tag).

## Xây dựng phần thân tài liệu

Phần tử `<body>` chứa tất cả nội dung hiển thị của trang web – mọi thứ người dùng sẽ thấy và tương tác. Trong khi phần `<head>` cung cấp hướng dẫn cho trình duyệt, phần `<body>` chứa nội dung thực tế: văn bản, hình ảnh, nút và các phần tử khác tạo giao diện người dùng của bạn.

Hãy thêm cấu trúc phần thân và hiểu cách các thẻ HTML hoạt động cùng nhau để tạo nội dung có ý nghĩa.

### Hiểu cấu trúc thẻ HTML

HTML sử dụng các thẻ cặp để định nghĩa các phần tử. Hầu hết các thẻ có thẻ mở như `<p>` và thẻ đóng như `</p>`, với nội dung ở giữa: `<p>Hello, world!</p>`. Điều này tạo ra một phần tử đoạn văn chứa văn bản "Hello, world!".

### Nhiệm vụ: Thêm phần tử Body

Cập nhật tệp HTML của bạn để bao gồm phần tử `<body>`:

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Welcome to my Virtual Terrarium</title>
		<meta charset="utf-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1" />
	</head>
	<body></body>
</html>
```

**Đây là những gì cấu trúc hoàn chỉnh này cung cấp:**
- **Thiết lập** khung tài liệu HTML5 cơ bản
- **Bao gồm** siêu dữ liệu cần thiết để trình duyệt hiển thị đúng cách
- **Tạo** một phần thân trống sẵn sàng cho nội dung hiển thị của bạn
- **Tuân theo** các thực hành tốt nhất trong phát triển web hiện đại

Bây giờ bạn đã sẵn sàng thêm các phần tử hiển thị của terrarium. Chúng ta sẽ sử dụng các phần tử `<div>` làm các container để tổ chức các phần nội dung khác nhau và các phần tử `<img>` để hiển thị hình ảnh cây cối.

### Làm việc với hình ảnh và các container bố cục

Hình ảnh đặc biệt trong HTML vì chúng sử dụng các thẻ "tự đóng". Không giống như các phần tử như `<p></p>` bao quanh nội dung, thẻ `<img>` chứa tất cả thông tin cần thiết trong chính thẻ đó bằng các thuộc tính như `src` cho đường dẫn tệp hình ảnh và `alt` cho khả năng truy cập.

Trước khi thêm hình ảnh vào HTML của bạn, bạn cần tổ chức các tệp dự án đúng cách bằng cách tạo một thư mục hình ảnh và thêm các đồ họa cây cối.

**Đầu tiên, thiết lập hình ảnh của bạn:**
1. Tạo một thư mục tên là `images` bên trong thư mục dự án terrarium của bạn
2. Tải xuống hình ảnh cây từ [thư mục giải pháp](../../../../3-terrarium/solution/images) (tổng cộng 14 hình ảnh cây)
3. Sao chép tất cả hình ảnh cây vào thư mục `images` mới của bạn

### Nhiệm vụ: Tạo bố cục hiển thị cây

Bây giờ hãy thêm hình ảnh cây được tổ chức trong hai cột giữa các thẻ `<body></body>` của bạn:

```html
<div id="page">
	<div id="left-container" class="container">
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant1" src="../../../../translated_images/plant1.d87946a2ca70cc4316bda6e6c3af7210fbe9ada5539a7885141a9ce0efaf7be3.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant2" src="../../../../translated_images/plant2.8daa1606c9c1ad896bb171212c7d1d882e504b76b8ec3a2d1c337d775cf50dc3.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant3" src="../../../../translated_images/plant3.8b0d484381a2a2a77c5c06ad97ab6ae5b7023da8c6c7678b0183bc0e46ea17a7.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant4" src="../../../../translated_images/plant4.656e16ae1df37be2af5f4e7b5ab6c5decc432c3d3ec2eb98b904ddbecad49db0.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant5" src="../../../../translated_images/plant5.2b41b9355f11ebccd62d327f5f14e56531ecda9c6f970bc89e386ee9f0273bb0.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant6" src="../../../../translated_images/plant6.3d1827d03b6569946be13ae5da1f32947ae56732638a43757a7c616a6adccc5d.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant7" src="../../../../translated_images/plant7.8152c302ac97f621a6c595bdf3939103568f9efc7d3b06a0f02a1ea66f479de0.vi.png" />
		</div>
	</div>
	<div id="right-container" class="container">
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant8" src="../../../../translated_images/plant8.38d6428174ffa850a47cd1b81d528fa528adda7d23f3ae0bb42f4a27356ca5e6.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant9" src="../../../../translated_images/plant9.f0e38d3327c37fc29cd2734d48d20c2cf69300898ece6d46708829e02ce540e3.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant10" src="../../../../translated_images/plant10.b159d6d6e985595f56d86b4b38061b8e7b4c9969c210c199fe967269cf935e7f.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant11" src="../../../../translated_images/plant11.2a03a1c2ec8ea84ef3a80c06cc6883f3960fbb669f2c0b0bd824ba33d7eb7d32.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant12" src="../../../../translated_images/plant12.60e9b53e538fbaf3e5797ebf800acb483baf5639e6cf378292ac2321ab8a5ea9.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant13" src="../../../../translated_images/plant13.07a51543c820bcf57f67a9a6c0acbd6211ff795e2e67a42a9718224534e95fab.vi.png" />
		</div>
		<div class="plant-holder">
			<img class="plant" alt="plant" id="plant14" src="../../../../translated_images/plant14.6e486371ba7d36ba3520d9828887993cb4c3edad8bdd8ff9b1b315717ff8cb63.vi.png" />
		</div>
	</div>
</div>
```

**Từng bước, đây là những gì đang xảy ra trong mã này:**
- **Tạo** một container trang chính với `id="page"` để chứa tất cả nội dung
- **Thiết lập** hai container cột: `left-container` và `right-container`
- **Tổ chức** 7 cây trong cột bên trái và 7 cây trong cột bên phải
- **Bao quanh** mỗi hình ảnh cây trong một div `plant-holder` để định vị riêng lẻ
- **Áp dụng** các tên lớp nhất quán để tạo kiểu CSS trong bài học tiếp theo
- **Gán** các ID duy nhất cho mỗi hình ảnh cây để tương tác JavaScript sau này
- **Bao gồm** các đường dẫn tệp đúng chỉ đến thư mục hình ảnh

> 🤔 **Hãy cân nhắc điều này**: Lưu ý rằng tất cả hình ảnh hiện có cùng văn bản alt "plant". Điều này không lý tưởng cho khả năng truy cập. Người dùng trình đọc màn hình sẽ nghe "plant" lặp lại 14 lần mà không biết hình ảnh cây cụ thể nào. Bạn có thể nghĩ ra văn bản alt tốt hơn, mô tả hơn cho từng hình ảnh không?

> 📝 **Các loại phần tử HTML**: Các phần tử `<div>` là "cấp khối" và chiếm toàn bộ chiều rộng, trong khi các phần tử `<span>` là "cấp dòng" và chỉ chiếm chiều rộng cần thiết. Bạn nghĩ điều gì sẽ xảy ra nếu bạn thay đổi tất cả các thẻ `<div>` này thành thẻ `<span>`?

Với mã này được thêm vào, các cây sẽ xuất hiện trên màn hình, mặc dù chúng chưa được tinh chỉnh – đó là nhiệm vụ của CSS trong bài học tiếp theo! Hiện tại, bạn đã có một nền tảng HTML vững chắc tổ chức nội dung đúng cách và tuân theo các thực hành tốt nhất về khả năng truy cập.

## Sử dụng HTML ngữ nghĩa để tăng khả năng truy cập

HTML ngữ nghĩa có nghĩa là chọn các phần tử HTML dựa trên ý nghĩa và mục đích của chúng, không chỉ dựa trên hình thức. Khi bạn sử dụng đánh dấu ngữ nghĩa, bạn đang truyền đạt cấu trúc và ý nghĩa của nội dung của bạn cho trình duyệt, công cụ tìm kiếm và các công nghệ hỗ trợ như trình đọc màn hình.

Cách tiếp cận này làm cho các trang web của bạn dễ truy cập hơn đối với người dùng khuyết tật và giúp công cụ tìm kiếm hiểu rõ hơn về nội dung của bạn. Đây là một nguyên tắc cơ bản của phát triển web hiện đại, tạo ra trải nghiệm tốt hơn cho mọi người.

### Thêm tiêu đề trang ngữ nghĩa

Hãy thêm một tiêu đề phù hợp cho trang terrarium của bạn. Chèn dòng này ngay sau thẻ `<body>` mở:

```html
<h1>My Terrarium</h1>
```

**Tại sao đánh dấu ngữ nghĩa lại quan trọng:**
- **Giúp** trình đọc màn hình điều hướng và hiểu cấu trúc trang
- **Cải thiện** tối ưu hóa công cụ tìm kiếm (SEO) bằng cách làm rõ thứ bậc nội dung
- **Tăng cường** khả năng truy cập cho người dùng bị khiếm thị hoặc gặp khó khăn về nhận thức
- **Tạo** trải nghiệm người dùng tốt hơn trên tất cả các thiết bị và nền tảng
- **Tuân theo** các tiêu chuẩn web và thực hành tốt nhất cho phát triển chuyên nghiệp

**Ví dụ về lựa chọn ngữ nghĩa và không ngữ nghĩa:**

| Mục đích | ✅ Lựa chọn ngữ nghĩa | ❌ Lựa chọn không ngữ nghĩa |
|---------|-------------------|------------------------|
| Tiêu đề chính | `<h1>Tiêu đề</h1>` | `<div class="big-text">Tiêu đề</div>` |
| Điều hướng | `<nav><ul><li></li></ul></nav>` | `<div class="menu"><div></div></div>` |
| Nút | `<button>Nhấn vào tôi</button>` | `<span onclick="...">Nhấn vào tôi</span>` |
| Nội dung bài viết | `<article><p></p></article>` | `<div class="content"><div></div></div>` |

> 🎥 **Xem nó hoạt động**: Xem [cách trình đọc màn hình tương tác với các trang web](https://www.youtube.com/watch?v=OUDV1gqs9GA) để hiểu tại sao đánh dấu ngữ nghĩa lại quan trọng đối với khả năng truy cập. Lưu ý cách cấu trúc HTML đúng giúp người dùng điều hướng hiệu quả.

## Tạo container Terrarium

Bây giờ hãy thêm cấu trúc HTML cho chính terrarium – container kính nơi các cây sẽ được đặt. Phần này minh họa một khái niệm quan trọng: HTML cung cấp cấu trúc, nhưng nếu không có CSS, các phần tử này sẽ chưa hiển thị.

Đánh dấu terrarium sử dụng các tên lớp mô tả sẽ làm cho việc tạo kiểu CSS trực quan và dễ duy trì trong bài học tiếp theo.

### Nhiệm vụ: Thêm cấu trúc Terrarium

Chèn đoạn mã này phía trên thẻ `</div>` cuối cùng (trước thẻ đóng của container trang):

```html
<div id="terrarium">
	<div class="jar-top"></div>
	<div class="jar-walls">
		<div class="jar-glossy-long"></div>
		<div class="jar-glossy-short"></div>
	</div>
	<div class="dirt"></div>
	<div class="jar-bottom"></div>
</div>
```

**Hiểu cấu trúc terrarium này:**
- **Tạo** một container terrarium chính với ID duy nhất để tạo kiểu
- **Định nghĩa** các phần tử riêng biệt cho từng thành phần hình ảnh (trên, tường, đất, đáy)
- **Bao gồm** các phần tử lồng nhau cho hiệu ứng phản chiếu kính (các phần tử glossy)
- **Sử dụng** các tên lớp mô tả rõ ràng mục đích của từng phần tử
- **Chuẩn bị** cấu trúc cho việc tạo kiểu CSS sẽ tạo ra diện mạo terrarium kính

> 🤔 **Lưu ý điều này**: Mặc dù bạn đã thêm đoạn mã này, bạn không thấy bất kỳ điều gì mới trên trang! Điều này minh họa hoàn hảo cách HTML cung cấp cấu trúc trong khi CSS cung cấp hình thức. Các thẻ `<div>` này tồn tại nhưng chưa có kiểu dáng trực quan – điều đó sẽ được thực hiện trong bài học tiếp theo!

---

## Thử thách Agent GitHub Copilot

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Tạo một cấu trúc HTML ngữ nghĩa cho phần hướng dẫn chăm sóc cây có thể được thêm vào dự án terrarium.
**Đề bài:** Tạo một phần HTML ngữ nghĩa bao gồm tiêu đề chính "Hướng Dẫn Chăm Sóc Cây", ba phần phụ với tiêu đề "Tưới Nước", "Yêu Cầu Ánh Sáng" và "Chăm Sóc Đất", mỗi phần chứa một đoạn văn bản thông tin về chăm sóc cây. Sử dụng các thẻ HTML ngữ nghĩa phù hợp như `<section>`, `<h2>`, `<h3>`, và `<p>` để cấu trúc nội dung một cách hợp lý.

Tìm hiểu thêm về [chế độ agent](https://code.visualstudio.com/blogs/2025/02/24/introducing-copilot-agent-mode) tại đây.

## Thử Thách Lịch Sử HTML

**Tìm Hiểu Về Sự Phát Triển Của Web**

HTML đã phát triển đáng kể kể từ khi Tim Berners-Lee tạo ra trình duyệt web đầu tiên tại CERN vào năm 1990. Một số thẻ cũ như `<marquee>` hiện đã bị loại bỏ vì chúng không phù hợp với các tiêu chuẩn truy cập hiện đại và nguyên tắc thiết kế đáp ứng.

**Thử Nghiệm Này:**
1. Tạm thời bao bọc tiêu đề `<h1>` của bạn trong thẻ `<marquee>`: `<marquee><h1>Terrarium Của Tôi</h1></marquee>`
2. Mở trang của bạn trong trình duyệt và quan sát hiệu ứng cuộn
3. Suy nghĩ tại sao thẻ này bị loại bỏ (gợi ý: nghĩ về trải nghiệm người dùng và khả năng truy cập)
4. Gỡ bỏ thẻ `<marquee>` và quay lại sử dụng đánh dấu ngữ nghĩa

**Câu Hỏi Suy Ngẫm:**
- Tiêu đề cuộn có thể ảnh hưởng như thế nào đến người dùng bị suy giảm thị lực hoặc nhạy cảm với chuyển động?
- Những kỹ thuật CSS hiện đại nào có thể tạo ra hiệu ứng tương tự một cách dễ tiếp cận hơn?
- Tại sao việc sử dụng các tiêu chuẩn web hiện tại thay vì các phần tử đã bị loại bỏ lại quan trọng?

Tìm hiểu thêm về [các phần tử HTML lỗi thời và đã bị loại bỏ](https://developer.mozilla.org/docs/Web/HTML/Element#Obsolete_and_deprecated_elements) để hiểu cách các tiêu chuẩn web phát triển nhằm cải thiện trải nghiệm người dùng.

## Câu Hỏi Sau Bài Giảng

[Bài kiểm tra sau bài giảng](https://ff-quizzes.netlify.app/web/quiz/16)

## Ôn Tập & Tự Học

**Nâng Cao Kiến Thức HTML Của Bạn**

HTML đã là nền tảng của web trong hơn 30 năm, phát triển từ một ngôn ngữ đánh dấu tài liệu đơn giản thành một nền tảng phức tạp để xây dựng các ứng dụng tương tác. Hiểu được sự phát triển này giúp bạn đánh giá cao các tiêu chuẩn web hiện đại và đưa ra các quyết định phát triển tốt hơn.

**Lộ Trình Học Tập Được Đề Xuất:**

1. **Lịch Sử và Sự Phát Triển của HTML**
   - Nghiên cứu dòng thời gian từ HTML 1.0 đến HTML5
   - Tìm hiểu lý do tại sao một số thẻ bị loại bỏ (khả năng truy cập, thân thiện với thiết bị di động, dễ bảo trì)
   - Khám phá các tính năng HTML mới và các đề xuất đang nổi lên

2. **Tìm Hiểu Sâu Về HTML Ngữ Nghĩa**
   - Nghiên cứu danh sách đầy đủ các [phần tử ngữ nghĩa HTML5](https://developer.mozilla.org/docs/Web/HTML/Element)
   - Thực hành xác định khi nào nên sử dụng `<article>`, `<section>`, `<aside>`, và `<main>`
   - Tìm hiểu về các thuộc tính ARIA để tăng cường khả năng truy cập

3. **Phát Triển Web Hiện Đại**
   - Khám phá [xây dựng các trang web đáp ứng](https://docs.microsoft.com/learn/modules/build-simple-website/?WT.mc_id=academic-77807-sagibbon) trên Microsoft Learn
   - Hiểu cách HTML tích hợp với CSS và JavaScript
   - Tìm hiểu về hiệu suất web và các phương pháp SEO tốt nhất

**Câu Hỏi Suy Ngẫm:**
- Bạn đã phát hiện ra những thẻ HTML nào bị loại bỏ và tại sao chúng bị loại bỏ?
- Những tính năng HTML mới nào đang được đề xuất cho các phiên bản tương lai?
- HTML ngữ nghĩa đóng góp như thế nào vào khả năng truy cập web và SEO?

## Bài Tập

[Luyện tập HTML của bạn: Xây dựng một mô hình blog](assignment.md)

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.