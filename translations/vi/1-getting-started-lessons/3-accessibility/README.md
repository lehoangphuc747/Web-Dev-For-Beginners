<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "90b19cde5b79b29e91babd3138cd8035",
  "translation_date": "2025-10-24T13:32:19+00:00",
  "source_file": "1-getting-started-lessons/3-accessibility/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../../README.md) | [◀️ Quay lại](../README.md) | [▶️ Module tiếp theo](../../2-js-basics/README.md)

---
# Tạo Trang Web Dễ Tiếp Cận

![Tất cả về khả năng tiếp cận](../../../../translated_images/webdev101-a11y.8ef3025c858d897a403a1a42c0897c76e11b724d9a8a0c0578dd4316f7507622.vi.png)
> Sketchnote bởi [Tomomi Imura](https://twitter.com/girlie_mac)

## Câu hỏi trước bài giảng
[Câu hỏi trước bài giảng](https://ff-quizzes.netlify.app/web/)

> Sức mạnh của Web nằm ở tính phổ quát của nó. Việc mọi người đều có thể truy cập, bất kể khuyết tật, là một khía cạnh thiết yếu.
>
> \- Sir Timothy Berners-Lee, Giám đốc W3C và người sáng tạo ra World Wide Web

Đây là điều có thể khiến bạn ngạc nhiên: khi bạn xây dựng các trang web dễ tiếp cận, bạn không chỉ giúp đỡ những người khuyết tật—mà thực ra bạn đang làm cho web trở nên tốt hơn cho tất cả mọi người!

Bạn có bao giờ để ý những đoạn đường dốc ở góc phố không? Ban đầu chúng được thiết kế cho xe lăn, nhưng giờ đây chúng giúp người đi xe đẩy, nhân viên giao hàng với xe đẩy, du khách với hành lý kéo, và cả người đi xe đạp nữa. Đó chính là cách thiết kế web dễ tiếp cận hoạt động—những giải pháp giúp một nhóm người thường sẽ mang lại lợi ích cho tất cả mọi người. Thật tuyệt phải không?

Trong bài học này, chúng ta sẽ khám phá cách tạo ra các trang web thực sự hoạt động cho tất cả mọi người, bất kể họ duyệt web như thế nào. Bạn sẽ tìm hiểu các kỹ thuật thực tế đã được tích hợp sẵn trong các tiêu chuẩn web, thực hành với các công cụ kiểm tra, và thấy cách khả năng tiếp cận làm cho các trang web của bạn dễ sử dụng hơn cho tất cả người dùng.

Kết thúc bài học này, bạn sẽ tự tin để biến khả năng tiếp cận thành một phần tự nhiên trong quy trình phát triển của mình. Sẵn sàng khám phá cách những lựa chọn thiết kế chu đáo có thể mở rộng web cho hàng tỷ người dùng chưa? Hãy bắt đầu nào!

> Bạn có thể tham gia bài học này trên [Microsoft Learn](https://docs.microsoft.com/learn/modules/web-development-101/accessibility/?WT.mc_id=academic-77807-sagibbon)!

## Hiểu về Công Nghệ Hỗ Trợ

Trước khi bắt đầu viết mã, hãy dành một chút thời gian để hiểu cách những người có khả năng khác nhau thực sự trải nghiệm web. Đây không chỉ là lý thuyết—hiểu các mẫu điều hướng thực tế này sẽ giúp bạn trở thành một nhà phát triển tốt hơn nhiều!

Công nghệ hỗ trợ là những công cụ tuyệt vời giúp người khuyết tật tương tác với các trang web theo những cách có thể khiến bạn ngạc nhiên. Một khi bạn hiểu cách các công nghệ này hoạt động, việc tạo ra trải nghiệm web dễ tiếp cận sẽ trở nên trực quan hơn nhiều. Nó giống như học cách nhìn mã của bạn qua con mắt của người khác.

### Trình đọc màn hình

[Trình đọc màn hình](https://en.wikipedia.org/wiki/Screen_reader) là những công nghệ khá tinh vi chuyển đổi văn bản kỹ thuật số thành âm thanh hoặc đầu ra chữ nổi. Mặc dù chúng chủ yếu được sử dụng bởi những người khiếm thị, chúng cũng rất hữu ích cho người dùng có các khuyết tật học tập như chứng khó đọc.

Tôi thích nghĩ về trình đọc màn hình như một người kể chuyện thông minh đang đọc sách cho bạn. Nó đọc nội dung thành tiếng theo thứ tự logic, thông báo các phần tử tương tác như "nút" hoặc "liên kết," và cung cấp các phím tắt để di chuyển quanh trang. Nhưng điều quan trọng là—trình đọc màn hình chỉ có thể hoạt động tốt nếu chúng ta xây dựng các trang web với cấu trúc đúng và nội dung có ý nghĩa. Đó là nơi bạn, với vai trò nhà phát triển, xuất hiện!

**Các trình đọc màn hình phổ biến trên các nền tảng:**
- **Windows**: [NVDA](https://www.nvaccess.org/about-nvda/) (miễn phí và phổ biến nhất), [JAWS](https://webaim.org/articles/jaws/), [Narrator](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1/?WT.mc_id=academic-77807-sagibbon) (tích hợp sẵn)
- **macOS/iOS**: [VoiceOver](https://support.apple.com/guide/voiceover/welcome/10) (tích hợp sẵn và rất mạnh mẽ)
- **Android**: [TalkBack](https://support.google.com/accessibility/android/answer/6283677) (tích hợp sẵn)
- **Linux**: [Orca](https://wiki.gnome.org/Projects/Orca) (miễn phí và mã nguồn mở)

**Cách trình đọc màn hình điều hướng nội dung web:**

Trình đọc màn hình cung cấp nhiều phương pháp điều hướng giúp việc duyệt web hiệu quả hơn cho người dùng có kinh nghiệm:
- **Đọc tuần tự**: Đọc nội dung từ trên xuống dưới, giống như đọc một cuốn sách
- **Điều hướng theo điểm mốc**: Chuyển giữa các phần của trang (đầu trang, điều hướng, chính, chân trang)
- **Điều hướng theo tiêu đề**: Nhảy giữa các tiêu đề để hiểu cấu trúc trang
- **Danh sách liên kết**: Tạo danh sách tất cả các liên kết để truy cập nhanh
- **Điều khiển biểu mẫu**: Điều hướng trực tiếp giữa các trường nhập liệu và nút

> 💡 **Điều này khiến tôi rất ngạc nhiên**: 68% người dùng trình đọc màn hình chủ yếu điều hướng bằng tiêu đề ([Khảo sát WebAIM](https://webaim.org/projects/screenreadersurvey9/#finding)). Điều này có nghĩa là cấu trúc tiêu đề của bạn giống như một bản đồ chỉ đường cho người dùng—khi bạn làm đúng, bạn thực sự đang giúp mọi người tìm đường quanh nội dung của bạn nhanh hơn!

### Xây dựng quy trình kiểm tra của bạn

Đây là tin tốt—kiểm tra khả năng tiếp cận hiệu quả không cần phải quá phức tạp! Bạn sẽ muốn kết hợp các công cụ tự động (chúng rất tuyệt trong việc phát hiện các vấn đề rõ ràng) với một số kiểm tra thủ công. Đây là cách tiếp cận có hệ thống mà tôi thấy bắt được nhiều vấn đề nhất mà không tốn quá nhiều thời gian:

**Quy trình kiểm tra thủ công cần thiết:**

```mermaid
graph TD
    A[Start Testing] --> B{Keyboard Navigation}
    B --> C[Tab through all interactive elements]
    C --> D{Screen Reader Testing}
    D --> E[Test with NVDA/VoiceOver]
    E --> F{Zoom Testing}
    F --> G[Zoom to 200% and test functionality]
    G --> H{Color/Contrast Check}
    H --> I[Verify all text meets contrast ratios]
    I --> J{Focus Management}
    J --> K[Ensure focus indicators are visible]
    K --> L[Testing Complete]
```

**Danh sách kiểm tra từng bước:**
1. **Điều hướng bằng bàn phím**: Chỉ sử dụng Tab, Shift+Tab, Enter, Space, và các phím mũi tên
2. **Kiểm tra trình đọc màn hình**: Bật NVDA, VoiceOver, hoặc Narrator và điều hướng với mắt nhắm
3. **Kiểm tra phóng to**: Kiểm tra ở mức phóng to 200% và 400%
4. **Xác minh độ tương phản màu sắc**: Kiểm tra tất cả văn bản và các thành phần giao diện người dùng
5. **Kiểm tra chỉ báo tiêu điểm**: Đảm bảo tất cả các phần tử tương tác có trạng thái tiêu điểm rõ ràng

✅ **Bắt đầu với Lighthouse**: Mở DevTools của trình duyệt, chạy kiểm tra khả năng tiếp cận bằng Lighthouse, sau đó sử dụng kết quả để tập trung vào các khu vực kiểm tra thủ công.

### Công cụ phóng to và phóng đại

Bạn có biết cách bạn đôi khi phóng to trên điện thoại khi văn bản quá nhỏ, hoặc nheo mắt nhìn màn hình laptop dưới ánh sáng mặt trời? Nhiều người dùng dựa vào các công cụ phóng đại để làm cho nội dung dễ đọc mỗi ngày. Điều này bao gồm những người có thị lực kém, người lớn tuổi, và bất kỳ ai từng cố đọc một trang web ngoài trời.

Công nghệ phóng to hiện đại đã phát triển vượt xa việc chỉ làm mọi thứ lớn hơn. Hiểu cách các công cụ này hoạt động sẽ giúp bạn tạo ra các thiết kế đáp ứng vẫn giữ được chức năng và hấp dẫn ở bất kỳ mức độ phóng đại nào.

**Khả năng phóng to của trình duyệt hiện đại:**
- **Phóng to trang**: Phóng to tất cả nội dung theo tỷ lệ (văn bản, hình ảnh, bố cục) - đây là phương pháp ưu tiên
- **Phóng to chỉ văn bản**: Tăng kích thước phông chữ trong khi giữ nguyên bố cục ban đầu
- **Phóng to bằng cách chụm tay**: Hỗ trợ cử chỉ trên thiết bị di động để phóng đại tạm thời
- **Hỗ trợ trình duyệt**: Tất cả các trình duyệt hiện đại hỗ trợ phóng to lên đến 500% mà không làm hỏng chức năng

**Phần mềm phóng đại chuyên dụng:**
- **Windows**: [Magnifier](https://support.microsoft.com/windows/use-magnifier-to-make-things-on-the-screen-easier-to-see-414948ba-8b1c-d3bd-8615-0e5e32204198) (tích hợp sẵn), [ZoomText](https://www.freedomscientific.com/training/zoomtext/getting-started/)
- **macOS/iOS**: [Zoom](https://www.apple.com/accessibility/mac/vision/) (tích hợp sẵn với các tính năng nâng cao)

> ⚠️ **Cân nhắc thiết kế**: WCAG yêu cầu nội dung vẫn phải hoạt động khi được phóng to đến 200%. Ở mức này, cuộn ngang nên được giảm thiểu, và tất cả các phần tử tương tác vẫn phải dễ tiếp cận.

✅ **Kiểm tra thiết kế đáp ứng của bạn**: Phóng to trình duyệt của bạn lên 200% và 400%. Bố cục của bạn có thích ứng một cách mượt mà không? Bạn có thể truy cập tất cả các chức năng mà không cần cuộn quá nhiều không?

## Công Cụ Kiểm Tra Khả Năng Tiếp Cận Hiện Đại

Bây giờ bạn đã hiểu cách mọi người điều hướng web với công nghệ hỗ trợ, hãy khám phá các công cụ giúp bạn xây dựng và kiểm tra các trang web dễ tiếp cận.

Hãy nghĩ như thế này: các công cụ tự động rất tốt trong việc phát hiện các vấn đề rõ ràng (như thiếu văn bản thay thế), trong khi kiểm tra thủ công giúp bạn đảm bảo trang web của mình dễ sử dụng trong thực tế. Kết hợp cả hai sẽ giúp bạn tự tin rằng các trang web của bạn hoạt động cho tất cả mọi người.

### Kiểm tra độ tương phản màu sắc

Đây là tin tốt: độ tương phản màu sắc là một trong những vấn đề khả năng tiếp cận phổ biến nhất, nhưng cũng là một trong những vấn đề dễ khắc phục nhất. Độ tương phản tốt mang lại lợi ích cho tất cả mọi người—từ người dùng có thị lực kém đến những người cố đọc điện thoại của họ trên bãi biển.

**Yêu cầu độ tương phản của WCAG:**

| Loại văn bản | WCAG AA (Tối thiểu) | WCAG AAA (Nâng cao) |
|--------------|---------------------|---------------------|
| **Văn bản thường** (dưới 18pt) | Tỷ lệ tương phản 4.5:1 | Tỷ lệ tương phản 7:1 |
| **Văn bản lớn** (18pt+ hoặc 14pt+ đậm) | Tỷ lệ tương phản 3:1 | Tỷ lệ tương phản 4.5:1 |
| **Thành phần UI** (nút, viền biểu mẫu) | Tỷ lệ tương phản 3:1 | Tỷ lệ tương phản 3:1 |

**Công cụ kiểm tra cần thiết:**
- [Colour Contrast Analyser](https://www.tpgi.com/color-contrast-checker/) - Ứng dụng máy tính với công cụ chọn màu
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) - Công cụ trực tuyến với phản hồi tức thì
- [Stark](https://www.getstark.co/) - Plugin công cụ thiết kế cho Figma, Sketch, Adobe XD
- [Accessible Colors](https://accessible-colors.com/) - Tìm bảng màu dễ tiếp cận

✅ **Xây dựng bảng màu tốt hơn**: Bắt đầu với màu thương hiệu của bạn và sử dụng các công cụ kiểm tra độ tương phản để tạo các biến thể dễ tiếp cận. Ghi lại những màu này như các token màu dễ tiếp cận trong hệ thống thiết kế của bạn.

### Kiểm tra khả năng tiếp cận toàn diện

Kiểm tra khả năng tiếp cận hiệu quả nhất là kết hợp nhiều phương pháp. Không có công cụ nào bắt được tất cả mọi thứ, vì vậy xây dựng một quy trình kiểm tra với các phương pháp khác nhau đảm bảo độ phủ toàn diện.

**Kiểm tra dựa trên trình duyệt (tích hợp trong DevTools):**
- **Chrome/Edge**: Kiểm tra khả năng tiếp cận bằng Lighthouse + bảng Accessibility
- **Firefox**: Accessibility Inspector với chế độ xem cây chi tiết
- **Safari**: Tab Audit trong Web Inspector với mô phỏng VoiceOver

**Tiện ích kiểm tra chuyên nghiệp:**
- [axe DevTools](https://www.deque.com/axe/devtools/) - Công cụ kiểm tra tự động tiêu chuẩn ngành
- [WAVE](https://wave.webaim.org/extension/) - Phản hồi trực quan với đánh dấu lỗi
- [Accessibility Insights](https://accessibilityinsights.io/) - Bộ công cụ kiểm tra toàn diện của Microsoft

**Tích hợp dòng lệnh và CI/CD:**
- [axe-core](https://github.com/dequelabs/axe-core) - Thư viện JavaScript để kiểm tra tự động
- [Pa11y](https://pa11y.org/) - Công cụ kiểm tra khả năng tiếp cận dòng lệnh
- [Lighthouse CI](https://github.com/GoogleChrome/lighthouse-ci) - Chấm điểm khả năng tiếp cận tự động

> 🎯 **Mục tiêu kiểm tra**: Nhắm đến điểm số khả năng tiếp cận Lighthouse từ 95+ làm cơ sở. Hãy nhớ rằng, các công cụ tự động chỉ bắt được khoảng 30-40% vấn đề khả năng tiếp cận—kiểm tra thủ công vẫn rất cần thiết!

## Xây Dựng Khả Năng Tiếp Cận Từ Đầu

Chìa khóa để thành công trong khả năng tiếp cận là xây dựng nó vào nền tảng ngay từ đầu. Tôi biết rất dễ nghĩ "Tôi sẽ thêm khả năng tiếp cận sau," nhưng đó giống như cố gắng thêm một đoạn đường dốc vào một ngôi nhà sau khi nó đã được xây dựng. Có thể? Có. Dễ dàng? Không thực sự.

Hãy nghĩ về khả năng tiếp cận như việc lập kế hoạch cho một ngôi nhà—dễ dàng hơn nhiều để bao gồm khả năng tiếp cận xe lăn trong kế hoạch kiến trúc ban đầu hơn là sửa đổi mọi thứ sau này.

### Nguyên tắc POUR: Nền tảng khả năng tiếp cận của bạn

Các Hướng dẫn Nội dung Web Dễ Tiếp Cận (WCAG) được xây dựng xung quanh bốn nguyên tắc cơ bản được viết tắt là POUR. Đừng lo—đây không phải là những khái niệm học thuật khô khan! Chúng thực sự là những hướng dẫn thực tế để tạo nội dung hoạt động cho tất cả mọi người.

Một khi bạn hiểu nguyên tắc POUR, việc đưa ra các quyết định về khả năng tiếp cận sẽ trở nên trực quan hơn nhiều. Nó giống như có một danh sách kiểm tra tinh thần hướng dẫn các lựa chọn thiết kế của bạn. Hãy cùng phân tích:

**🔍 Có thể cảm nhận được**: Thông tin phải được trình bày theo cách người dùng có thể cảm nhận qua các giác quan sẵn có

- Cung cấp các thay thế văn bản cho nội dung không phải văn bản (hình ảnh, video, âm thanh)
- Đảm bảo độ tương phản màu sắc đủ cho tất cả văn bản và các thành phần giao diện người dùng
- Cung cấp phụ đề và bản ghi cho nội dung đa phương tiện
- Thiết kế nội dung vẫn hoạt động khi được phóng to lên đến 200%
- Sử dụng nhiều đặc điểm cảm giác (không chỉ màu sắc) để truyền tải thông tin

**🎮 Có thể vận hành**: Tất cả các thành phần giao diện phải có thể vận hành thông qua các phương pháp nhập liệu sẵn có

- Làm cho tất cả các chức năng có thể truy cập qua điều hướng bằng bàn phím
- Cung cấp đủ thời gian để người dùng đọc và tương tác với nội dung
- Tránh nội dung gây co giật hoặc rối loạn tiền đình
- Giúp người dùng điều hướng hiệu quả với cấu trúc rõ ràng và các điểm mốc
- Đảm bảo các phần tử tương tác có kích thước mục tiêu đủ lớn (tối thiểu 44px)

**📖 Có thể hiểu được**: Thông tin và cách vận hành giao diện phải rõ ràng và dễ hiểu

- Sử dụng ngôn ngữ rõ ràng, đơn giản phù hợp với đối tượng của bạn
- Đảm bảo nội dung xuất hiện và hoạt động theo cách có thể dự đoán và nhất quán
- Cung cấp hướng dẫn rõ ràng và thông báo lỗi cho đầu vào của người dùng
- Giúp người dùng hiểu và sửa lỗi trong biểu mẫu
- Tổ chức nội dung với thứ tự đọc logic và hệ thống phân cấp thông tin

**💪 Mạnh mẽ**: Nội dung phải hoạt động đáng tin cậy trên các công nghệ và thiết bị hỗ trợ khác nhau

- Sử dụng HTML hợp lệ, có tính ngữ nghĩa làm nền tảng của bạn
- Đảm bảo tương thích với các công nghệ hỗ trợ hiện tại và tương lai
- Tuân theo các tiêu chuẩn web và thực hành tốt nhất về đánh dấu
- Kiểm tra trên các trình duyệt, thiết bị, và công cụ hỗ trợ khác nhau
- Cấu trúc nội dung để nó suy giảm một cách duyên dáng khi các tính năng nâng cao không được hỗ trợ

## Tạo Thiết Kế Hình Ảnh Dễ Tiếp Cận

Thiết kế hình ảnh tốt và khả năng tiếp cận luôn song hành. Khi bạn thiết kế với khả năng tiếp cận trong tâm trí, bạn thường phát hiện ra rằng
Màu sắc là một công cụ mạnh mẽ để giao tiếp, nhưng không bao giờ nên là cách duy nhất để truyền tải thông tin quan trọng. Thiết kế vượt ra ngoài màu sắc tạo ra trải nghiệm mạnh mẽ hơn, toàn diện hơn và phù hợp với nhiều tình huống hơn.

**Thiết kế cho sự khác biệt về thị giác màu sắc:**

Khoảng 8% nam giới và 0.5% nữ giới có một dạng khác biệt về thị giác màu sắc (thường được gọi là "mù màu"). Các loại phổ biến nhất là:
- **Deuteranopia**: Khó phân biệt giữa màu đỏ và màu xanh lá cây
- **Protanopia**: Màu đỏ trông mờ hơn
- **Tritanopia**: Khó phân biệt giữa màu xanh dương và màu vàng (hiếm gặp)

**Chiến lược màu sắc toàn diện:**

```css
/* ❌ Bad: Using only color to indicate status */
.error { color: red; }
.success { color: green; }

/* ✅ Good: Color plus icons and context */
.error {
  color: #d32f2f;
  border-left: 4px solid #d32f2f;
}
.error::before {
  content: "⚠️";
  margin-right: 8px;
}

.success {
  color: #2e7d32;
  border-left: 4px solid #2e7d32;
}
.success::before {
  content: "✅";
  margin-right: 8px;
}
```

**Vượt qua yêu cầu cơ bản về độ tương phản:**
- Kiểm tra lựa chọn màu sắc của bạn với các trình mô phỏng mù màu
- Sử dụng hoa văn, kết cấu hoặc hình dạng cùng với mã hóa màu sắc
- Đảm bảo trạng thái tương tác vẫn có thể phân biệt được mà không cần màu sắc
- Xem xét cách thiết kế của bạn hiển thị trong chế độ độ tương phản cao

✅ **Kiểm tra khả năng tiếp cận màu sắc của bạn**: Sử dụng các công cụ như [Coblis](https://www.color-blindness.com/coblis-color-blindness-simulator/) để xem trang web của bạn hiển thị như thế nào đối với người dùng có các loại thị giác màu sắc khác nhau.

### Chỉ báo tiêu điểm và thiết kế tương tác

Chỉ báo tiêu điểm là tương đương kỹ thuật số của con trỏ chuột—chúng cho người dùng bàn phím biết họ đang ở đâu trên trang. Chỉ báo tiêu điểm được thiết kế tốt nâng cao trải nghiệm cho mọi người bằng cách làm cho các tương tác trở nên rõ ràng và dễ dự đoán.

**Thực hành tốt nhất cho chỉ báo tiêu điểm hiện đại:**

```css
/* Enhanced focus styles that work across browsers */
button:focus-visible {
  outline: 2px solid #0066cc;
  outline-offset: 2px;
  box-shadow: 0 0 0 4px rgba(0, 102, 204, 0.25);
}

/* Remove focus outline for mouse users, preserve for keyboard users */
button:focus:not(:focus-visible) {
  outline: none;
}

/* Focus-within for complex components */
.card:focus-within {
  box-shadow: 0 0 0 3px rgba(74, 144, 164, 0.5);
  border-color: #4A90A4;
}

/* Ensure focus indicators meet contrast requirements */
.custom-focus:focus-visible {
  outline: 3px solid #ffffff;
  outline-offset: 2px;
  box-shadow: 0 0 0 6px #000000;
}
```

**Yêu cầu đối với chỉ báo tiêu điểm:**
- **Khả năng hiển thị**: Phải có tỷ lệ tương phản ít nhất 3:1 với các yếu tố xung quanh
- **Độ rộng**: Độ dày tối thiểu 2px xung quanh toàn bộ yếu tố
- **Duy trì**: Nên vẫn hiển thị cho đến khi tiêu điểm chuyển sang nơi khác
- **Phân biệt**: Phải khác biệt rõ ràng với các trạng thái UI khác

> 💡 **Mẹo thiết kế**: Chỉ báo tiêu điểm tuyệt vời thường sử dụng sự kết hợp giữa đường viền, bóng hộp và thay đổi màu sắc để đảm bảo khả năng hiển thị trên các nền và ngữ cảnh khác nhau.

✅ **Kiểm tra chỉ báo tiêu điểm**: Sử dụng phím Tab để di chuyển qua trang web của bạn và ghi chú lại các yếu tố có chỉ báo tiêu điểm rõ ràng. Có yếu tố nào khó nhìn thấy hoặc hoàn toàn thiếu không?

### HTML ngữ nghĩa: Nền tảng của khả năng tiếp cận

HTML ngữ nghĩa giống như cung cấp cho các công nghệ hỗ trợ một hệ thống GPS cho trang web của bạn. Khi bạn sử dụng các yếu tố HTML đúng mục đích của chúng, bạn đang cung cấp cho các trình đọc màn hình, bàn phím và các công cụ khác một bản đồ chi tiết để giúp người dùng điều hướng hiệu quả.

Đây là một phép so sánh mà tôi thấy rất hợp lý: HTML ngữ nghĩa giống như sự khác biệt giữa một thư viện được tổ chức tốt với các danh mục rõ ràng và biển chỉ dẫn hữu ích so với một nhà kho nơi sách bị vứt lung tung. Cả hai nơi đều có cùng số sách, nhưng bạn sẽ muốn tìm kiếm ở nơi nào hơn? Chính xác!

**Các khối xây dựng cấu trúc trang tiếp cận:**

```html
<!-- Landmark elements provide page navigation structure -->
<header>
  <h1>Your Site Name</h1>
  <nav aria-label="Main navigation">
    <ul>
      <li><a href="/home">Home</a></li>
      <li><a href="/about">About</a></li>
      <li><a href="/services">Services</a></li>
    </ul>
  </nav>
</header>

<main>
  <article>
    <header>
      <h1>Article Title</h1>
      <p>Published on <time datetime="2024-10-14">October 14, 2024</time></p>
    </header>
    
    <section>
      <h2>First Section</h2>
      <p>Content that relates to this section...</p>
    </section>
    
    <section>
      <h2>Second Section</h2>
      <p>More related content...</p>
    </section>
  </article>
  
  <aside>
    <h2>Related Links</h2>
    <nav aria-label="Related articles">
      <ul>
        <li><a href="/related-1">First related article</a></li>
        <li><a href="/related-2">Second related article</a></li>
      </ul>
    </nav>
  </aside>
</main>

<footer>
  <p>&copy; 2024 Your Site Name. All rights reserved.</p>
  <nav aria-label="Footer links">
    <ul>
      <li><a href="/privacy">Privacy Policy</a></li>
      <li><a href="/contact">Contact Us</a></li>
    </ul>
  </nav>
</footer>
```

**Tại sao HTML ngữ nghĩa cải thiện khả năng tiếp cận:**

| Yếu tố ngữ nghĩa | Mục đích | Lợi ích cho trình đọc màn hình |
|------------------|---------|----------------------|
| `<header>` | Tiêu đề trang hoặc phần | "Banner landmark" - điều hướng nhanh đến đầu trang |
| `<nav>` | Liên kết điều hướng | "Navigation landmark" - danh sách các phần điều hướng |
| `<main>` | Nội dung chính của trang | "Main landmark" - chuyển trực tiếp đến nội dung |
| `<article>` | Nội dung tự chứa | Thông báo ranh giới bài viết |
| `<section>` | Nhóm nội dung theo chủ đề | Cung cấp cấu trúc nội dung |
| `<aside>` | Nội dung bên lề liên quan | "Complementary landmark" |
| `<footer>` | Chân trang hoặc phần cuối | "Contentinfo landmark" |

**Siêu năng lực của trình đọc màn hình với HTML ngữ nghĩa:**
- **Điều hướng landmark**: Chuyển nhanh giữa các phần chính của trang
- **Dàn ý tiêu đề**: Tạo bảng mục lục từ cấu trúc tiêu đề của bạn
- **Danh sách yếu tố**: Tạo danh sách tất cả các liên kết, nút hoặc điều khiển biểu mẫu
- **Nhận thức ngữ cảnh**: Hiểu mối quan hệ giữa các phần nội dung

> 🎯 **Kiểm tra nhanh**: Thử điều hướng trang web của bạn bằng trình đọc màn hình sử dụng phím tắt landmark (D cho landmark, H cho tiêu đề, K cho liên kết trong NVDA/JAWS). Điều hướng có hợp lý không?

✅ **Kiểm tra cấu trúc ngữ nghĩa của bạn**: Sử dụng bảng Accessibility trong DevTools của trình duyệt để xem cây khả năng tiếp cận và đảm bảo đánh dấu của bạn tạo ra cấu trúc hợp lý.

### Hệ thống tiêu đề: Tạo dàn ý nội dung hợp lý

Tiêu đề cực kỳ quan trọng đối với nội dung tiếp cận—chúng giống như xương sống giữ mọi thứ lại với nhau. Người dùng trình đọc màn hình dựa rất nhiều vào tiêu đề để hiểu và điều hướng nội dung của bạn. Hãy nghĩ về nó như cung cấp một bảng mục lục cho trang của bạn.

**Đây là quy tắc vàng cho tiêu đề:**
Không bao giờ bỏ qua cấp độ. Luôn tiến triển một cách hợp lý từ `<h1>` đến `<h2>` đến `<h3>`, và tiếp tục như vậy. Hãy nhớ lại việc tạo dàn ý ở trường học? Nguyên tắc hoàn toàn giống nhau—bạn sẽ không nhảy từ "I. Điểm chính" thẳng đến "C. Điểm phụ-phụ" mà không có "A. Điểm phụ" ở giữa, đúng không?

**Ví dụ về cấu trúc tiêu đề hoàn hảo:**

```html
<!-- ✅ Excellent: Logical, hierarchical progression -->
<main>
  <h1>Complete Guide to Web Accessibility</h1>
  
  <section>
    <h2>Understanding Screen Readers</h2>
    <p>Introduction to screen reader technology...</p>
    
    <h3>Popular Screen Reader Software</h3>
    <p>NVDA, JAWS, and VoiceOver comparison...</p>
    
    <h3>Testing with Screen Readers</h3>
    <p>Step-by-step testing instructions...</p>
  </section>
  
  <section>
    <h2>Color and Contrast Guidelines</h2>
    <p>Designing with sufficient contrast...</p>
    
    <h3>WCAG Contrast Requirements</h3>
    <p>Understanding the different contrast levels...</p>
    
    <h3>Testing Tools and Techniques</h3>
    <p>Tools for verifying contrast ratios...</p>
  </section>
</main>
```

```html
<!-- ❌ Problematic: Skipping levels, inconsistent structure -->
<h1>Page Title</h1>
<h3>Subsection</h3> <!-- Skipped h2 -->
<h2>This should come before h3</h2>
<h1>Another main heading?</h1> <!-- Multiple h1s -->
```

**Thực hành tốt nhất cho tiêu đề:**
- **Một `<h1>` mỗi trang**: Thường là tiêu đề chính của trang hoặc tiêu đề nội dung chính
- **Tiến triển hợp lý**: Không bao giờ bỏ qua cấp độ (h1 → h2 → h3, không phải h1 → h3)
- **Nội dung mô tả**: Làm cho tiêu đề có ý nghĩa khi đọc ngoài ngữ cảnh
- **Phong cách trực quan với CSS**: Sử dụng CSS để hiển thị, cấp độ HTML để cấu trúc

**Thống kê điều hướng trình đọc màn hình:**
- 68% người dùng trình đọc màn hình điều hướng bằng tiêu đề ([Khảo sát WebAIM](https://webaim.org/projects/screenreadersurvey9/#finding))
- Người dùng mong đợi tìm thấy một dàn ý tiêu đề hợp lý
- Tiêu đề cung cấp cách nhanh nhất để hiểu cấu trúc trang

> 💡 **Mẹo chuyên nghiệp**: Sử dụng tiện ích mở rộng trình duyệt như "HeadingsMap" để hình dung cấu trúc tiêu đề của bạn. Nó nên đọc giống như một bảng mục lục được tổ chức tốt.

✅ **Kiểm tra cấu trúc tiêu đề của bạn**: Sử dụng điều hướng tiêu đề của trình đọc màn hình (phím H trong NVDA) để nhảy qua các tiêu đề của bạn. Tiến trình có kể câu chuyện nội dung của bạn một cách hợp lý không?

### Kỹ thuật tiếp cận hình ảnh nâng cao

Ngoài các yếu tố cơ bản về độ tương phản và màu sắc, có những kỹ thuật tinh vi giúp tạo ra trải nghiệm hình ảnh thực sự toàn diện. Những phương pháp này đảm bảo nội dung của bạn hoạt động trong các điều kiện xem khác nhau và với các công nghệ hỗ trợ.

**Chiến lược giao tiếp hình ảnh thiết yếu:**

- **Phản hồi đa phương thức**: Kết hợp các tín hiệu hình ảnh, văn bản và đôi khi âm thanh
- **Tiết lộ tiến bộ**: Trình bày thông tin thành các phần dễ tiêu hóa
- **Mẫu tương tác nhất quán**: Sử dụng các quy ước UI quen thuộc
- **Kiểu chữ đáp ứng**: Điều chỉnh kích thước văn bản phù hợp trên các thiết bị
- **Trạng thái tải và lỗi**: Cung cấp phản hồi rõ ràng cho tất cả các hành động của người dùng

**Tiện ích CSS để cải thiện khả năng tiếp cận:**

```css
/* Screen reader only text - visually hidden but accessible */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* Skip link for keyboard navigation */
.skip-link {
  position: absolute;
  top: -40px;
  left: 6px;
  background: #000000;
  color: #ffffff;
  padding: 8px 16px;
  text-decoration: none;
  border-radius: 4px;
  font-weight: bold;
  transition: top 0.3s ease;
  z-index: 1000;
}

.skip-link:focus {
  top: 6px;
}

/* Reduced motion respect */
@media (prefers-reduced-motion: reduce) {
  .skip-link {
    transition: none;
  }
  
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  .button {
    border: 2px solid;
  }
}
```

> 🎯 **Mẫu tiếp cận**: "Liên kết bỏ qua" là điều cần thiết cho người dùng bàn phím. Nó nên là yếu tố đầu tiên có thể tập trung trên trang của bạn và chuyển trực tiếp đến khu vực nội dung chính.

✅ **Thực hiện bỏ qua điều hướng**: Thêm liên kết bỏ qua vào các trang của bạn và kiểm tra chúng bằng cách nhấn phím Tab ngay khi trang tải. Chúng nên xuất hiện và cho phép bạn chuyển đến nội dung chính.

## Tạo văn bản liên kết có ý nghĩa

Liên kết về cơ bản là các con đường cao tốc của web, nhưng văn bản liên kết được viết kém giống như có các biển báo đường chỉ ghi "Nơi" thay vì "Trung tâm Chicago." Không hữu ích chút nào, đúng không?

Đây là điều khiến tôi ngạc nhiên khi lần đầu tiên biết đến: trình đọc màn hình có thể trích xuất tất cả các liên kết từ một trang và hiển thị chúng dưới dạng một danh sách lớn. Hãy tưởng tượng nếu ai đó đưa cho bạn một danh bạ của mọi liên kết trên trang của bạn. Liệu mỗi liên kết có ý nghĩa riêng không? Đó là bài kiểm tra mà văn bản liên kết của bạn cần vượt qua!

### Hiểu các mẫu điều hướng liên kết

Trình đọc màn hình cung cấp các tính năng điều hướng liên kết mạnh mẽ dựa trên văn bản liên kết được viết tốt:

**Phương pháp điều hướng liên kết:**
- **Đọc tuần tự**: Các liên kết được đọc trong ngữ cảnh như một phần của luồng nội dung
- **Tạo danh sách liên kết**: Tất cả các liên kết trên trang được biên soạn thành một danh bạ có thể tìm kiếm
- **Điều hướng nhanh**: Nhảy giữa các liên kết bằng phím tắt (K trong NVDA)
- **Chức năng tìm kiếm**: Tìm liên kết cụ thể bằng cách nhập một phần văn bản

**Tại sao ngữ cảnh lại quan trọng:**
Khi người dùng trình đọc màn hình tạo danh sách liên kết, họ sẽ thấy như sau:
- "Tải xuống báo cáo"
- "Tìm hiểu thêm"
- "Nhấp vào đây"
- "Chính sách bảo mật"
- "Nhấp vào đây"

Chỉ có hai trong số các liên kết này cung cấp thông tin hữu ích khi đọc ngoài ngữ cảnh!

> 📊 **Tác động đến người dùng**: Người dùng trình đọc màn hình quét danh sách liên kết để hiểu nội dung trang nhanh chóng. Văn bản liên kết chung chung buộc họ phải điều hướng trở lại ngữ cảnh của từng liên kết, làm chậm đáng kể trải nghiệm duyệt web của họ.

### Những lỗi phổ biến về văn bản liên kết cần tránh

Hiểu những gì không hiệu quả giúp bạn nhận ra và khắc phục các vấn đề về khả năng tiếp cận trong nội dung hiện có.

**❌ Văn bản liên kết chung chung không cung cấp ngữ cảnh:**

```html
<!-- Meaningless when read from a link list -->
<p>Our sustainability efforts are detailed in our recent report. 
   <a href="/sustainability-2024.pdf">Click here</a> to view it.</p>

<!-- Repeated generic text throughout the page -->
<div class="article-card">
  <h3>Web Accessibility Guide</h3>
  <p>Learn the fundamentals...</p>
  <a href="/accessibility-guide">Read more</a>
</div>
<div class="article-card">
  <h3>Color Contrast Tips</h3>
  <p>Improve your design...</p>
  <a href="/color-contrast">Read more</a>
</div>

<!-- URLs as link text (difficult for screen readers to announce) -->
<p>Visit https://www.w3.org/WAI/WCAG21/quickref/ for WCAG guidelines.</p>

<!-- Vague action words -->
<a href="/contact">Go</a> | <a href="/about">See</a> | <a href="/help">View</a>
```

**Tại sao các mẫu này thất bại:**
- **"Nhấp vào đây"** không nói gì về điểm đến
- **"Đọc thêm"** lặp lại nhiều lần gây nhầm lẫn
- **URL thô** khó để trình đọc màn hình phát âm rõ ràng
- **Từ đơn** như "Đi" hoặc "Xem" thiếu ngữ cảnh mô tả

### Viết văn bản liên kết xuất sắc

Văn bản liên kết mô tả rõ ràng mang lại lợi ích cho tất cả mọi người—người dùng có thể nhanh chóng quét các liên kết, và người dùng trình đọc màn hình hiểu ngay điểm đến.

**✅ Ví dụ về văn bản liên kết rõ ràng, mô tả:**

```html
<!-- Descriptive text that explains the destination -->
<p>Our comprehensive <a href="/sustainability-2024.pdf">2024 sustainability report (PDF, 2.1MB)</a> details our environmental initiatives.</p>

<!-- Specific, unique link text for each card -->
<div class="article-card">
  <h3>Web Accessibility Guide</h3>
  <p>Learn the fundamentals of inclusive design...</p>
  <a href="/accessibility-guide">Read our complete web accessibility guide</a>
</div>
<div class="article-card">
  <h3>Color Contrast Tips</h3>
  <p>Improve your design with better color choices...</p>
  <a href="/color-contrast">Explore color contrast best practices</a>
</div>

<!-- Meaningful text instead of raw URLs -->
<p>The <a href="https://www.w3.org/WAI/WCAG21/quickref/">WCAG 2.1 Quick Reference guide</a> provides comprehensive accessibility guidelines.</p>

<!-- Descriptive action links -->
<a href="/contact">Contact our support team</a> | 
<a href="/about">About our company</a> | 
<a href="/help">Get help with your account</a>
```

**Thực hành tốt nhất cho văn bản liên kết:**
- **Cụ thể**: "Tải xuống báo cáo tài chính quý" thay vì "Tải xuống"
- **Bao gồm loại tệp và kích thước**: "(PDF, 1.2MB)" cho các tệp có thể tải xuống
- **Đề cập nếu liên kết mở bên ngoài**: "(mở trong cửa sổ mới)" khi thích hợp
- **Sử dụng ngôn ngữ chủ động**: "Liên hệ với chúng tôi" thay vì "Trang liên hệ"
- **Giữ ngắn gọn**: Nhắm đến 2-8 từ khi có thể

### Mẫu tiếp cận liên kết nâng cao

Đôi khi các hạn chế về thiết kế trực quan hoặc yêu cầu kỹ thuật cần các giải pháp đặc biệt. Dưới đây là các kỹ thuật tinh vi cho các tình huống thách thức phổ biến:

**Sử dụng ARIA để tăng cường ngữ cảnh:**

```html
<!-- When button text must be short but needs more context -->
<a href="/report.pdf" 
   aria-label="Download 2024 annual financial report, PDF format, 2.3MB">
  Download Report
</a>

<!-- When the full context comes from surrounding content -->
<h3 id="sustainability-heading">Sustainability Initiative</h3>
<p>Our efforts to reduce environmental impact...</p>
<a href="/sustainability-details" 
   aria-labelledby="sustainability-heading"
   aria-describedby="sustainability-summary">
  Learn more
</a>
<p id="sustainability-summary">Detailed breakdown of our 2024 environmental goals and achievements</p>
```

**Chỉ định loại tệp và điểm đến bên ngoài:**

```html
<!-- Method 1: Include information in visible link text -->
<a href="/annual-report.pdf">
  Download our 2024 annual report (PDF, 2.3MB)
</a>

<!-- Method 2: Use screen reader-only text for file details -->
<a href="/annual-report.pdf">
  Download our 2024 annual report
  <span class="sr-only">(PDF format, 2.3MB)</span>
</a>

<!-- Method 3: External link indication -->
<a href="https://example.com" 
   target="_blank" 
   aria-describedby="external-link-warning">
  Visit external resource
</a>
<span id="external-link-warning" class="sr-only">
  (opens in new window)
</span>

<!-- Method 4: Using CSS for visual indicators -->
<a href="https://example.com" class="external-link">
  External resource
</a>
```

```css
/* Visual indicator for external links */
.external-link::after {
  content: " ↗";
  font-size: 0.8em;
  color: #666;
}

/* Screen reader announcement for external links */
.external-link::before {
  content: "External link: ";
  position: absolute;
  left: -10000px;
  width: 1px;
  height: 1px;
  overflow: hidden;
}
```

> ⚠️ **Quan trọng**: Khi sử dụng `target="_blank"`, luôn thông báo cho người dùng rằng liên kết mở trong cửa sổ hoặc tab mới. Những thay đổi điều hướng không mong đợi có thể gây mất phương hướng.

✅ **Kiểm tra ngữ cảnh liên kết của bạn**: Sử dụng công cụ dành cho nhà phát triển của trình duyệt để tạo danh sách tất cả các liên kết trên trang của bạn. Bạn có thể hiểu mục đích của từng liên kết mà không cần ngữ cảnh xung quanh không?

## ARIA: Tăng cường khả năng tiếp cận HTML

[Ứng dụng Internet Rich Accessible (ARIA)](https://developer.mozilla.org/docs/Web/Accessibility/ARIA) giống như có một bộ dịch thuật phổ quát giữa các ứng dụng web phức tạp của bạn và các công nghệ hỗ trợ. Khi HTML không thể diễn đạt hết mọi thứ mà các thành phần tương tác của bạn đang làm, ARIA sẽ lấp đầy những khoảng trống đó.

Tôi thích nghĩ về ARIA như việc thêm các chú thích hữu ích vào HTML của bạn—giống như các chỉ dẫn sân khấu trong kịch bản giúp diễn viên hiểu vai trò và mối quan hệ của họ.

**Đây là quy tắc quan trọng nhất về ARIA**: Luôn sử dụng HTML ngữ nghĩa trước, sau đó thêm ARIA để tăng cường. Hãy nghĩ về ARIA như gia vị, không phải món chính. Nó nên làm rõ và tăng cường cấu trúc HTML của bạn, không bao giờ thay thế nó. Hãy làm đúng nền tảng trước!

### Triển khai ARIA chiến lược

ARIA rất mạnh mẽ, nhưng với sức mạnh đi kèm trách nhiệm. ARIA không chính xác có thể làm cho khả năng tiếp cận trở nên tệ hơn là không có ARIA. Dưới đây là khi nào và cách sử dụng nó hiệu quả:

**✅ Sử dụng ARIA khi:**
- Tạo các tiện ích tương tác tùy chỉnh (accordion, tab, carousel)
- Xây dựng nội dung động thay đổi mà không tải lại trang
- Cung cấp ngữ cảnh bổ sung cho các mối quan hệ UI phức tạp
- Chỉ định trạng thái tải hoặc cập nhật nội dung trực tiếp
- Tạo giao diện giống ứng dụng với các điều khiển tùy chỉnh

**❌ Tránh ARIA khi:**
- Các yếu tố HTML tiêu chuẩn đã cung cấp ngữ nghĩa cần thiết
- Bạn không chắc chắn cách triển khai nó đúng cách
- Nó lặp lại thông tin đã được cung cấp bởi HTML ngữ nghĩa
- Bạn chưa kiểm tra với công nghệ hỗ trợ thực tế

> 🎯 **Quy tắc vàng của ARIA**: "Đừng thay đổi ngữ nghĩa trừ khi bạn thực sự cần, luôn đảm bảo khả năng tiếp cận bàn phím, và kiểm tra với công nghệ hỗ trợ thực tế."

**Năm loại ARIA:**

1. **Vai trò**: Đây là yếu tố gì? (`button`, `tab`, `dialog`)
2. **Thuộc tính**: Đặc điểm của nó là gì? (`aria-required`, `aria-haspopup`)
3. **Trạng thái**: Tình trạng hiện tại của nó là gì? (`aria-expanded`, `aria-checked`)
4. **Landmark**: Nó nằm ở đâu trong cấu trúc trang? (`banner`, `navigation`, `main`)
5. **Vùng trực tiếp**: Thay đổi nên được thông báo như thế nào? (`aria-live`, `aria-atomic`)

### Mẫu ARIA thiết yếu cho ứng dụng web hiện đại

Những mẫu này giải quyết các thách thức phổ biến nhất về khả năng tiếp cận trong các ứng dụng web tương tác:

**Đặt tên và mô tả yếu tố:**

```html
<!-- aria-label: Provides accessible name when visible text isn't sufficient -->
<button aria-label="Close newsletter subscription dialog">×</button>

<!-- aria-labelledby: References existing text as the accessible name -->
<section aria-labelledby="news-heading">
  <h2 id="news-heading">Latest News</h2>
  <!-- news content -->
</section>

<!-- aria-describedby: Links to additional descriptive text -->
<input type="password" 
       aria-describedby="pwd-requirements pwd-strength"
       required>
<div id="pwd-requirements">
  Password must contain at least 8 characters, including uppercase, lowercase, and numbers.
</div>
<div id="pwd-strength" aria-live="polite">
  <!-- Dynamic password strength indicator -->
</div>
```

**Vùng trực tiếp cho nội dung động:**

```html
<!-- Polite announcements (don't interrupt current speech) -->
<div aria-live="polite" id="status-updates">
  <!-- Status messages appear here -->
</div>

<!-- Assertive announcements (interrupt and announce immediately) -->
<div aria-live="assertive" id="urgent-alerts">
  <!-- Error messages and critical alerts -->
</div>

<!-- Loading states with live regions -->
<button id="submit-btn" aria-describedby="loading-status">
  Submit Application
</button>
<div id="loading-status" aria-live="polite" aria-atomic="true">
  <!-- "Processing your application..." appears here -->
</div>
```

**Ví dụ về tiện ích tương tác (accordion):**

```html
<div class="accordion">
  <h3>
    <button aria-expanded="false" 
            aria-controls="panel-1" 
            id="accordion-trigger-1"
            class="accordion-trigger">
      Accessibility Guidelines
    </button>
  </h3>
  <div id="panel-1" 
       role="region"
       aria-labelledby="accordion-trigger-1" 
       hidden>
    <p>WCAG 2.1 provides comprehensive guidelines...</p>
  </div>
</div>
```

```javascript
// JavaScript to manage accordion state
function toggleAccordion(trigger) {
  const panel = document.getElementById(trigger.getAttribute('aria-controls'));
  const isExpanded = trigger.getAttribute('aria-expanded') === 'true';
  
  // Toggle states
  trigger.setAttribute('aria-expanded', !isExpanded);
  panel.hidden = isExpanded;
  
  // Announce change to screen readers
  const status = document.getElementById('status-updates');
  status.textContent = isExpanded ? 'Section collapsed' : 'Section expanded';
}
```

### Thực hành tốt nhất khi triển khai ARIA

ARIA rất mạnh mẽ nhưng yêu cầu triển khai cẩn thận. Tuân theo các hướng dẫn này giúp đảm bảo ARIA của bạn tăng cường thay vì cản trở khả năng tiếp cận:

**🛡️ Nguyên tắc cốt lõi:**

1. **HTML ngữ nghĩa trước**: Luôn ưu tiên
5. **Bắt đầu đơn giản**: Các triển khai ARIA phức tạp dễ mắc lỗi hơn

**🔍 Quy trình kiểm tra:**

```mermaid
graph TD
    A[Write ARIA code] --> B[Validate HTML]
    B --> C[Test with keyboard only]
    C --> D[Test with screen reader]
    D --> E[Test across browsers]
    E --> F{Issues found?}
    F -->|Yes| G[Fix and re-test]
    F -->|No| H[Implementation complete]
    G --> B
```

**🚫 Những lỗi ARIA phổ biến cần tránh:**

- **Thông tin mâu thuẫn**: Đừng mâu thuẫn với ngữ nghĩa HTML
- **Quá nhiều nhãn**: Quá nhiều thông tin ARIA khiến người dùng bị quá tải
- **ARIA tĩnh**: Quên cập nhật trạng thái ARIA khi nội dung thay đổi
- **Triển khai chưa được kiểm tra**: ARIA hoạt động trên lý thuyết nhưng thất bại trong thực tế
- **Thiếu hỗ trợ bàn phím**: Vai trò ARIA không đi kèm với tương tác bàn phím phù hợp

> 💡 **Tài nguyên kiểm tra**: Sử dụng các công cụ như [accessibility-checker](https://www.npmjs.com/package/accessibility-checker) để kiểm tra ARIA tự động, nhưng luôn kiểm tra với trình đọc màn hình thực tế để có trải nghiệm đầy đủ.

✅ **Học hỏi từ chuyên gia**: Nghiên cứu [ARIA Authoring Practices Guide](https://w3c.github.io/aria-practices/) để tìm hiểu các mẫu và triển khai đã được kiểm chứng cho các tiện ích tương tác phức tạp.

## Làm cho hình ảnh và phương tiện truyền thông trở nên dễ tiếp cận

Nội dung hình ảnh và âm thanh là phần không thể thiếu của trải nghiệm web hiện đại, nhưng chúng có thể tạo ra rào cản nếu không được triển khai một cách cẩn thận. Mục tiêu là đảm bảo rằng thông tin và tác động cảm xúc của phương tiện truyền thông đến được với mọi người dùng. Khi bạn đã quen, việc này sẽ trở thành thói quen.

Các loại phương tiện khác nhau cần các cách tiếp cận về khả năng tiếp cận khác nhau. Giống như nấu ăn—bạn sẽ không xử lý một con cá tinh tế giống như cách bạn xử lý một miếng bít tết chắc chắn. Hiểu được những khác biệt này giúp bạn chọn giải pháp phù hợp cho từng tình huống.

### Chiến lược tiếp cận hình ảnh

Mỗi hình ảnh trên trang web của bạn đều có một mục đích. Hiểu được mục đích đó giúp bạn viết văn bản thay thế tốt hơn và tạo ra trải nghiệm bao gồm hơn.

**Bốn loại hình ảnh và chiến lược văn bản thay thế của chúng:**

**Hình ảnh thông tin** - truyền tải thông tin quan trọng:
```html
<img src="../../../../translated_images/chart.31c7eb0eb5c4450deba10b6f236732dfee8e8a11f6c0d8f31d2c2efb9d4c00ef.vi.png" alt="Sales increased 25% from Q1 to Q2 2024">
```

**Hình ảnh trang trí** - chỉ mang tính thẩm mỹ, không có giá trị thông tin:
```html
<img src="../../../../translated_images/decorative-border.b2f3c4d6634fb79d57fb6357835906c16938df3d5651c1314c196c3b1c52df98.vi.png" alt="" role="presentation">
```

**Hình ảnh chức năng** - đóng vai trò như nút hoặc điều khiển:
```html
<button>
  <img src="search-icon.svg" alt="Search">
</button>
```

**Hình ảnh phức tạp** - biểu đồ, sơ đồ, đồ họa thông tin:
```html
<img src="../../../../translated_images/complex-chart.c831f461a363b446a688be5ccacde20d011221758c902cb082cfd4293534ef17.vi.png" alt="Quarterly sales data" aria-describedby="chart-description">
<div id="chart-description">
  <p>Detailed description: Sales data shows a steady increase across all quarters...</p>
</div>
```

### Tiếp cận video và âm thanh

**Yêu cầu đối với video:**
- **Phụ đề**: Phiên bản văn bản của nội dung nói và hiệu ứng âm thanh
- **Mô tả âm thanh**: Tường thuật các yếu tố hình ảnh cho người dùng khiếm thị
- **Bản ghi**: Phiên bản văn bản đầy đủ của tất cả nội dung âm thanh và hình ảnh

```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <track kind="captions" src="captions.vtt" srclang="en" label="English">
  <track kind="descriptions" src="descriptions.vtt" srclang="en" label="Audio descriptions">
</video>
```

**Yêu cầu đối với âm thanh:**
- **Bản ghi**: Phiên bản văn bản của tất cả nội dung nói
- **Chỉ báo hình ảnh**: Đối với nội dung chỉ có âm thanh, cung cấp các dấu hiệu hình ảnh

### Kỹ thuật hình ảnh hiện đại

**Sử dụng CSS cho hình ảnh trang trí:**
```css
.hero-section {
  background-image: url('decorative-hero.jpg');
  /* Decorative images in CSS don't need alt text */
}
```

**Hình ảnh đáp ứng với khả năng tiếp cận:**
```html
<picture>
  <source media="(min-width: 800px)" srcset="large-chart.png">
  <source media="(min-width: 400px)" srcset="medium-chart.png">
  <img src="../../../../translated_images/small-chart.c50c7b1bbcce43d8d24fbfbab8f691fe47d8f25fb7c70857c9eae21d5f22862e.vi.png" alt="Website traffic increased 40% after accessibility improvements">
</picture>
```

✅ **Kiểm tra khả năng tiếp cận hình ảnh**: Sử dụng trình đọc màn hình để điều hướng một trang có hình ảnh. Bạn có nhận được đủ thông tin để hiểu nội dung không?

## Điều hướng bằng bàn phím và quản lý tiêu điểm

Nhiều người dùng điều hướng web hoàn toàn bằng bàn phím. Điều này bao gồm những người có khuyết tật vận động, người dùng chuyên nghiệp thấy bàn phím nhanh hơn chuột, và bất kỳ ai có chuột bị hỏng. Đảm bảo rằng trang web của bạn hoạt động tốt với đầu vào từ bàn phím là điều cần thiết và thường làm cho trang web của bạn hiệu quả hơn cho tất cả mọi người.

### Mẫu điều hướng bàn phím cơ bản

**Tương tác bàn phím tiêu chuẩn:**
- **Tab**: Di chuyển tiêu điểm qua các phần tử tương tác
- **Shift + Tab**: Di chuyển tiêu điểm ngược lại
- **Enter**: Kích hoạt nút và liên kết
- **Space**: Kích hoạt nút, chọn hộp kiểm
- **Phím mũi tên**: Điều hướng trong nhóm thành phần (nút radio, menu)
- **Escape**: Đóng hộp thoại, menu thả xuống hoặc hủy thao tác

### Thực hành tốt nhất về quản lý tiêu điểm

**Chỉ báo tiêu điểm rõ ràng:**
```css
/* Ensure focus is always visible */
button:focus-visible {
  outline: 2px solid #4A90A4;
  outline-offset: 2px;
}

/* Custom focus styles for different components */
.card:focus-within {
  box-shadow: 0 0 0 3px rgba(74, 144, 164, 0.5);
}
```

**Liên kết bỏ qua để điều hướng hiệu quả:**
```html
<a href="#main-content" class="skip-link">Skip to main content</a>
<a href="#navigation" class="skip-link">Skip to navigation</a>

<nav id="navigation">
  <!-- navigation content -->
</nav>
<main id="main-content">
  <!-- main content -->
</main>
```

**Thứ tự tab hợp lý:**
```html
<!-- Use semantic HTML for natural tab order -->
<form>
  <label for="name">Name:</label>
  <input type="text" id="name" tabindex="0">
  
  <label for="email">Email:</label>
  <input type="email" id="email" tabindex="0">
  
  <button type="submit" tabindex="0">Submit</button>
</form>
```

### Bẫy tiêu điểm trong hộp thoại

Khi mở hộp thoại modal, tiêu điểm nên bị giới hạn trong hộp thoại:

```javascript
// Modern focus trap implementation
function trapFocus(element) {
  const focusableElements = element.querySelectorAll(
    'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
  );
  
  const firstElement = focusableElements[0];
  const lastElement = focusableElements[focusableElements.length - 1];

  element.addEventListener('keydown', (e) => {
    if (e.key === 'Tab') {
      if (e.shiftKey && document.activeElement === firstElement) {
        e.preventDefault();
        lastElement.focus();
      } else if (!e.shiftKey && document.activeElement === lastElement) {
        e.preventDefault();
        firstElement.focus();
      }
    }
    
    if (e.key === 'Escape') {
      closeModal();
    }
  });
  
  // Focus first element when modal opens
  firstElement.focus();
}
```

✅ **Kiểm tra điều hướng bàn phím**: Thử điều hướng trang web của bạn chỉ bằng phím Tab. Bạn có thể truy cập tất cả các phần tử tương tác không? Thứ tự tiêu điểm có hợp lý không? Các chỉ báo tiêu điểm có rõ ràng không?

## Khả năng tiếp cận của biểu mẫu

Biểu mẫu là yếu tố quan trọng để tương tác với người dùng và cần được chú ý đặc biệt về khả năng tiếp cận.

### Liên kết nhãn và điều khiển biểu mẫu

**Mỗi điều khiển biểu mẫu cần có một nhãn:**
```html
<!-- Explicit labeling (preferred) -->
<label for="username">Username:</label>
<input type="text" id="username" name="username" required>

<!-- Implicit labeling -->
<label>
  Password:
  <input type="password" name="password" required>
</label>

<!-- Using aria-label when visual label isn't desired -->
<input type="search" aria-label="Search products" placeholder="Search...">
```

### Xử lý lỗi và xác thực

**Thông báo lỗi dễ tiếp cận:**
```html
<label for="email">Email Address:</label>
<input type="email" id="email" name="email" 
       aria-describedby="email-error" 
       aria-invalid="true" required>
<div id="email-error" role="alert">
  Please enter a valid email address
</div>
```

**Thực hành tốt nhất về xác thực biểu mẫu:**
- Sử dụng `aria-invalid` để chỉ ra các trường không hợp lệ
- Cung cấp thông báo lỗi rõ ràng, cụ thể
- Sử dụng `role="alert"` cho các thông báo lỗi quan trọng
- Hiển thị lỗi cả ngay lập tức và khi gửi biểu mẫu

### Fieldsets và nhóm

**Nhóm các điều khiển biểu mẫu liên quan:**
```html
<fieldset>
  <legend>Shipping Address</legend>
  <label for="street">Street Address:</label>
  <input type="text" id="street" name="street">
  
  <label for="city">City:</label>
  <input type="text" id="city" name="city">
</fieldset>

<fieldset>
  <legend>Preferred Contact Method</legend>
  <input type="radio" id="contact-email" name="contact" value="email">
  <label for="contact-email">Email</label>
  
  <input type="radio" id="contact-phone" name="contact" value="phone">
  <label for="contact-phone">Phone</label>
</fieldset>
```

## Hành trình tiếp cận của bạn: Những điều cần nhớ

Chúc mừng! Bạn vừa nắm được kiến thức cơ bản để tạo ra trải nghiệm web thực sự bao gồm. Đây là điều rất thú vị! Khả năng tiếp cận web không chỉ là việc đánh dấu các ô tuân thủ—mà là việc nhận ra các cách đa dạng mà mọi người tương tác với nội dung số và thiết kế cho sự phức tạp tuyệt vời đó.

Bạn giờ đây là một phần của cộng đồng ngày càng lớn các nhà phát triển hiểu rằng thiết kế tuyệt vời là dành cho tất cả mọi người. Chào mừng bạn đến với câu lạc bộ!

**🎯 Bộ công cụ tiếp cận của bạn giờ đây bao gồm:**

| Nguyên tắc cốt lõi | Triển khai | Tác động |
|--------------------|------------|----------|
| **Nền tảng HTML ngữ nghĩa** | Sử dụng các phần tử HTML đúng mục đích | Trình đọc màn hình có thể điều hướng hiệu quả, bàn phím hoạt động tự động |
| **Thiết kế hình ảnh bao gồm** | Độ tương phản đủ, sử dụng màu sắc có ý nghĩa, chỉ báo tiêu điểm rõ ràng | Rõ ràng cho mọi người trong mọi điều kiện ánh sáng |
| **Nội dung mô tả** | Văn bản liên kết có ý nghĩa, văn bản thay thế, tiêu đề | Người dùng hiểu nội dung mà không cần ngữ cảnh hình ảnh |
| **Khả năng tiếp cận bàn phím** | Thứ tự tab, phím tắt, quản lý tiêu điểm | Khả năng tiếp cận vận động và hiệu quả cho người dùng chuyên nghiệp |
| **Tăng cường ARIA** | Sử dụng chiến lược để lấp đầy khoảng trống ngữ nghĩa | Ứng dụng phức tạp hoạt động với công nghệ hỗ trợ |
| **Kiểm tra toàn diện** | Công cụ tự động + xác minh thủ công + kiểm tra người dùng thực tế | Phát hiện vấn đề trước khi ảnh hưởng đến người dùng |

**🚀 Các bước tiếp theo của bạn:**

1. **Tích hợp khả năng tiếp cận vào quy trình làm việc**: Biến việc kiểm tra thành một phần tự nhiên của quy trình phát triển
2. **Học hỏi từ người dùng thực tế**: Tìm kiếm phản hồi từ những người sử dụng công nghệ hỗ trợ
3. **Luôn cập nhật**: Kỹ thuật tiếp cận phát triển cùng với công nghệ và tiêu chuẩn mới
4. **Vận động cho sự bao gồm**: Chia sẻ kiến thức của bạn và biến khả năng tiếp cận thành ưu tiên của nhóm

> 💡 **Nhớ rằng**: Các ràng buộc về khả năng tiếp cận thường dẫn đến các giải pháp sáng tạo, thanh lịch mang lại lợi ích cho tất cả mọi người. Đường dốc, phụ đề và điều khiển bằng giọng nói đều bắt đầu là các tính năng tiếp cận và trở thành cải tiến phổ biến.

**Lợi ích kinh doanh rất rõ ràng**: Các trang web dễ tiếp cận tiếp cận được nhiều người dùng hơn, xếp hạng tốt hơn trên công cụ tìm kiếm, có chi phí bảo trì thấp hơn và tránh được rủi ro pháp lý. Nhưng thực sự? Lý do thực sự để quan tâm đến khả năng tiếp cận còn sâu sắc hơn thế. Các trang web dễ tiếp cận thể hiện những giá trị tốt nhất của web—sự cởi mở, bao gồm, và ý tưởng rằng mọi người đều xứng đáng có quyền truy cập thông tin như nhau.

Bạn giờ đây đã sẵn sàng để xây dựng web bao gồm của tương lai. Mỗi trang web dễ tiếp cận mà bạn tạo ra làm cho internet trở thành một nơi chào đón hơn cho tất cả mọi người. Điều đó thật tuyệt vời khi bạn nghĩ về nó!

## Tài nguyên bổ sung

Tiếp tục hành trình học hỏi về khả năng tiếp cận của bạn với những tài nguyên thiết yếu này:

**📚 Tiêu chuẩn và hướng dẫn chính thức:**
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/) - Tiêu chuẩn tiếp cận chính thức với tham khảo nhanh
- [ARIA Authoring Practices Guide](https://w3c.github.io/aria-practices/) - Các mẫu toàn diện cho tiện ích tương tác
- [WebAIM Guidelines](https://webaim.org/) - Hướng dẫn tiếp cận thực tế, thân thiện với người mới bắt đầu

**🛠️ Công cụ và tài nguyên kiểm tra:**
- [axe DevTools](https://www.deque.com/axe/devtools/) - Công cụ kiểm tra tiếp cận tiêu chuẩn ngành
- [A11y Project Checklist](https://www.a11yproject.com/checklist/) - Xác minh tiếp cận từng bước
- [Accessibility Insights](https://accessibilityinsights.io/) - Bộ công cụ kiểm tra toàn diện của Microsoft
- [Color Oracle](https://colororacle.org/) - Trình mô phỏng mù màu để kiểm tra thiết kế

**🎓 Học hỏi và cộng đồng:**
- [WebAIM Screen Reader Survey](https://webaim.org/projects/screenreadersurvey9/) - Sở thích và hành vi của người dùng thực tế
- [Inclusive Components](https://inclusive-components.design/) - Mẫu thành phần tiếp cận hiện đại
- [A11y Coffee](https://a11y.coffee/) - Mẹo và thông tin nhanh về khả năng tiếp cận
- [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/) - Tài nguyên tiếp cận toàn diện của W3C

**🎥 Học tập thực hành:**
- [Accessibility Developer Guide](https://www.accessibility-developer-guide.com/) - Hướng dẫn triển khai thực tế
- [Deque University](https://dequeuniversity.com/) - Các khóa học đào tạo chuyên nghiệp về khả năng tiếp cận

## Thử thách GitHub Copilot Agent 🚀

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Tạo một thành phần hộp thoại modal dễ tiếp cận, thể hiện quản lý tiêu điểm đúng cách, thuộc tính ARIA, và mẫu điều hướng bàn phím.

**Yêu cầu:** Xây dựng một thành phần hộp thoại modal hoàn chỉnh với HTML, CSS, và JavaScript bao gồm: bẫy tiêu điểm đúng cách, phím ESC để đóng, nhấp bên ngoài để đóng, thuộc tính ARIA cho trình đọc màn hình, và chỉ báo tiêu điểm rõ ràng. Hộp thoại modal nên chứa một biểu mẫu với nhãn đúng cách và xử lý lỗi. Đảm bảo thành phần đáp ứng tiêu chuẩn WCAG 2.1 AA.

## 🚀 Thử thách

Hãy lấy HTML này và viết lại để dễ tiếp cận nhất có thể, dựa trên các chiến lược bạn đã học.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Turtle Ipsum - The World's Premier Turtle Fan Club</title>
    <link href='../assets/style.css' rel='stylesheet' type='text/css'>
  </head>
  <body>
    <header class="site-header">
      <h1 class="site-title">Turtle Ipsum</h1>
      <p class="site-subtitle">The World's Premier Turtle Fan Club</p>
    </header>
    
    <nav class="main-nav" aria-label="Main navigation">
      <h2 class="nav-header">Resources</h2>
      <ul class="nav-list">
        <li><a href="https://www.youtube.com/watch?v=CMNry4PE93Y">"I like turtles" video</a></li>
        <li><a href="https://en.wikipedia.org/wiki/Turtle">Basic turtle information</a></li>
        <li><a href="https://en.wikipedia.org/wiki/Turtles_(chocolate)">Chocolate turtles candy</a></li>
      </ul>
    </nav>
    
    <main class="main-content">
      <article>
        <h1>Welcome to Turtle Ipsum</h1>
        <p class="intro">
          <a href="/about">Learn more about our turtle community</a> and discover fascinating facts about these amazing creatures.
        </p>
        <p class="article-text">
          Turtle ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
        </p>
      </article>
    </main>
    
    <footer class="footer">
      <section class="newsletter-signup">
        <h2>Stay Updated</h2>
        <button type="button" onclick="showNewsletterForm()">Sign up for turtle news</button>
      </section>
      
      <nav class="footer-nav" aria-label="Footer navigation">
        <h2>Site Pages</h2>
        <ul>
          <li><a href="../">Home</a></li>
          <li><a href="../semantic">Semantic HTML example</a></li>
        </ul>
      </nav>
      
      <p class="footer-copyright">&copy; 2024 Instrument. All rights reserved.</p>
    </footer>
  </body>
</html>
```

**Những cải tiến chính đã thực hiện:**
- Thêm cấu trúc HTML ngữ nghĩa đúng cách
- Sửa thứ tự tiêu đề (một h1 duy nhất, tiến trình logic)
- Thêm văn bản liên kết có ý nghĩa thay vì "click here"
- Bao gồm nhãn ARIA đúng cách cho điều hướng
- Thêm thuộc tính lang và thẻ meta phù hợp
- Sử dụng phần tử button cho các phần tử tương tác
- Cấu trúc nội dung footer với các điểm mốc phù hợp

## Câu hỏi kiểm tra sau bài giảng
[Câu hỏi kiểm tra sau bài giảng](https://ff-quizzes.netlify.app/web/en/)

## Ôn tập & Tự học

Nhiều chính phủ có luật về yêu cầu tiếp cận. Tìm hiểu về luật tiếp cận của quốc gia bạn. Những gì được bao phủ và những gì không? Một ví dụ là [trang web chính phủ này](https://accessibility.blog.gov.uk/).

## Bài tập

[Phân tích một trang web không dễ tiếp cận](assignment.md)

Nguồn: [Turtle Ipsum](https://github.com/Instrument/semantic-html-sample) của Instrument

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, chúng tôi khuyến nghị sử dụng dịch vụ dịch thuật chuyên nghiệp từ con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.