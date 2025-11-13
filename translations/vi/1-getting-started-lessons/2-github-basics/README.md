<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "acad15f3164cd6348e065ff38619aae9",
  "translation_date": "2025-10-24T13:34:06+00:00",
  "source_file": "1-getting-started-lessons/2-github-basics/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../../README.md) | [◀️ Quay lại](../README.md) | [▶️ Bài tiếp theo](../3-accessibility/README.md)

---
# Giới thiệu về GitHub

Chào bạn, nhà phát triển tương lai! 👋 Sẵn sàng tham gia cùng hàng triệu lập trình viên trên khắp thế giới chưa? Mình thực sự rất hào hứng giới thiệu với bạn về GitHub – hãy nghĩ về nó như một mạng xã hội dành cho lập trình viên, nhưng thay vì chia sẻ ảnh bữa trưa, chúng ta chia sẻ mã nguồn và cùng nhau xây dựng những điều tuyệt vời!

Điều khiến mình kinh ngạc là: mọi ứng dụng trên điện thoại của bạn, mọi trang web bạn truy cập, và hầu hết các công cụ bạn sẽ học cách sử dụng đều được tạo ra bởi các nhóm lập trình viên hợp tác trên các nền tảng giống như GitHub. Ứng dụng âm nhạc bạn yêu thích? Ai đó giống bạn đã đóng góp vào nó. Trò chơi bạn không thể rời mắt? Đúng vậy, có lẽ được xây dựng với sự hợp tác trên GitHub. Và bây giờ BẠN sẽ học cách trở thành một phần của cộng đồng tuyệt vời đó!

Mình biết điều này có thể khiến bạn cảm thấy hơi nhiều lúc ban đầu – mình cũng từng nhìn vào trang GitHub đầu tiên của mình và nghĩ "Cái này nghĩa là gì vậy trời?" Nhưng đây là điều: mọi lập trình viên đều bắt đầu từ đúng vị trí của bạn bây giờ. Đến cuối bài học này, bạn sẽ có kho lưu trữ GitHub của riêng mình (hãy nghĩ về nó như một nơi trưng bày dự án cá nhân của bạn trên đám mây), và bạn sẽ biết cách lưu trữ công việc của mình, chia sẻ nó với người khác, và thậm chí đóng góp vào các dự án mà hàng triệu người sử dụng.

Chúng ta sẽ cùng nhau đi qua hành trình này, từng bước một. Không vội vàng, không áp lực – chỉ có bạn, mình, và một số công cụ thực sự thú vị sắp trở thành người bạn tốt nhất của bạn!

![Giới thiệu về GitHub](../../../../translated_images/webdev101-github.8846d7971abef6f947909b4f9d343e2a23778aa716ca6b9d71df7174ee5009ac.vi.png)
> Sketchnote bởi [Tomomi Imura](https://twitter.com/girlie_mac)

## Câu hỏi trước bài giảng
[Quiz trước bài giảng](https://ff-quizzes.netlify.app)

## Giới thiệu

Trước khi chúng ta đi sâu vào những điều thực sự thú vị, hãy chuẩn bị máy tính của bạn cho một chút phép thuật GitHub! Hãy nghĩ về điều này như việc sắp xếp dụng cụ nghệ thuật của bạn trước khi tạo ra một kiệt tác – có sẵn các công cụ phù hợp sẽ làm mọi thứ trở nên mượt mà hơn và thú vị hơn rất nhiều.

Mình sẽ hướng dẫn bạn từng bước thiết lập, và mình hứa rằng nó không hề đáng sợ như bạn nghĩ lúc đầu. Nếu có điều gì đó không hiểu ngay lập tức, điều đó hoàn toàn bình thường! Mình nhớ lần đầu tiên thiết lập môi trường phát triển của mình, cảm giác như đang cố gắng đọc chữ tượng hình cổ đại. Mọi lập trình viên đều đã từng ở đúng vị trí của bạn bây giờ, tự hỏi liệu họ có làm đúng không. Bật mí: nếu bạn đang học, bạn đã làm đúng rồi! 🌟

Trong bài học này, chúng ta sẽ tìm hiểu:

- cách theo dõi công việc bạn làm trên máy tính của mình
- cách làm việc trên các dự án với người khác
- cách đóng góp vào phần mềm mã nguồn mở

### Yêu cầu trước

Hãy chuẩn bị máy tính của bạn cho một chút phép thuật GitHub! Đừng lo – việc thiết lập này chỉ cần làm một lần, và sau đó bạn sẽ sẵn sàng cho toàn bộ hành trình lập trình của mình.

Được rồi, hãy bắt đầu với nền tảng! Đầu tiên, chúng ta cần kiểm tra xem Git đã có trên máy tính của bạn chưa. Git về cơ bản giống như một trợ lý siêu thông minh nhớ mọi thay đổi bạn thực hiện với mã nguồn của mình – tốt hơn nhiều so với việc nhấn Ctrl+S liên tục (ai cũng từng làm vậy!).

Hãy kiểm tra xem Git đã được cài đặt chưa bằng cách gõ lệnh này trong terminal của bạn:
`git --version`

Nếu Git chưa được cài đặt, đừng lo! Chỉ cần truy cập [download Git](https://git-scm.com/downloads) và tải về. Sau khi cài đặt xong, chúng ta cần giới thiệu Git với bạn một cách đúng đắn:

> 💡 **Thiết lập lần đầu tiên**: Những lệnh này sẽ cho Git biết bạn là ai. Thông tin này sẽ được gắn vào mỗi lần commit bạn thực hiện, vì vậy hãy chọn tên và email mà bạn cảm thấy thoải mái chia sẻ công khai.

```bash
git config --global user.name "your-name"
git config --global user.email "your-email"
```

Để kiểm tra xem Git đã được cấu hình chưa, bạn có thể gõ:
```bash
git config --list
```

Bạn cũng sẽ cần một tài khoản GitHub, một trình soạn thảo mã (như Visual Studio Code), và bạn cần mở terminal (hoặc: command prompt).

Truy cập [github.com](https://github.com/) và tạo tài khoản nếu bạn chưa có, hoặc đăng nhập và điền thông tin hồ sơ của bạn.

💡 **Mẹo hiện đại**: Hãy cân nhắc thiết lập [SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) hoặc sử dụng [GitHub CLI](https://cli.github.com/) để xác thực dễ dàng hơn mà không cần mật khẩu.

✅ GitHub không phải là kho lưu trữ mã duy nhất trên thế giới; có những kho khác, nhưng GitHub là nổi tiếng nhất.

### Chuẩn bị

Bạn sẽ cần một thư mục chứa dự án mã nguồn trên máy tính của mình (laptop hoặc PC), và một kho lưu trữ công khai trên GitHub, nơi sẽ là ví dụ cho cách đóng góp vào các dự án của người khác.

### Bảo vệ mã nguồn của bạn

Hãy nói về bảo mật một chút – nhưng đừng lo, chúng ta sẽ không làm bạn choáng ngợp với những điều đáng sợ! Hãy nghĩ về các thực hành bảo mật này như việc khóa xe hoặc nhà của bạn. Chúng là những thói quen đơn giản trở thành bản năng và giúp bảo vệ công việc của bạn.

Chúng ta sẽ chỉ cho bạn những cách làm việc hiện đại, an toàn với GitHub ngay từ đầu. Bằng cách này, bạn sẽ phát triển những thói quen tốt sẽ phục vụ bạn suốt sự nghiệp lập trình.

Khi làm việc với GitHub, điều quan trọng là tuân theo các thực hành bảo mật tốt nhất:

| Khu vực bảo mật | Thực hành tốt nhất | Tại sao nó quan trọng |
|-----------------|--------------------|-----------------------|
| **Xác thực** | Sử dụng SSH keys hoặc Personal Access Tokens | Mật khẩu kém an toàn hơn và đang dần bị loại bỏ |
| **Xác thực hai yếu tố** | Kích hoạt 2FA trên tài khoản GitHub của bạn | Thêm một lớp bảo vệ cho tài khoản của bạn |
| **Bảo mật kho lưu trữ** | Không bao giờ commit thông tin nhạy cảm | API keys và mật khẩu không nên xuất hiện trong kho công khai |
| **Quản lý phụ thuộc** | Kích hoạt Dependabot để cập nhật | Giữ cho các phụ thuộc của bạn an toàn và luôn được cập nhật |

> ⚠️ **Lưu ý bảo mật quan trọng**: Không bao giờ commit API keys, mật khẩu, hoặc thông tin nhạy cảm khác vào bất kỳ kho lưu trữ nào. Sử dụng biến môi trường và tệp `.gitignore` để bảo vệ dữ liệu nhạy cảm.

**Thiết lập xác thực hiện đại:**

```bash
# Generate SSH key (modern ed25519 algorithm)
ssh-keygen -t ed25519 -C "your_email@example.com"

# Set up Git to use SSH
git remote set-url origin git@github.com:username/repository.git
```

> 💡 **Mẹo chuyên nghiệp**: SSH keys loại bỏ việc phải nhập mật khẩu liên tục và an toàn hơn các phương pháp xác thực truyền thống.

---

## Quản lý mã nguồn của bạn như một chuyên gia

Được rồi, ĐÂY là lúc mọi thứ thực sự thú vị! 🎉 Chúng ta sắp học cách theo dõi và quản lý mã nguồn của bạn như các chuyên gia, và thành thật mà nói, đây là một trong những điều mình thích dạy nhất vì nó thực sự thay đổi cuộc chơi.

Hãy tưởng tượng thế này: bạn đang viết một câu chuyện tuyệt vời, và bạn muốn theo dõi mọi bản thảo, mọi chỉnh sửa xuất sắc, và mọi khoảnh khắc "chờ đã, thật là thiên tài!" trong suốt quá trình. Đó chính xác là những gì Git làm cho mã nguồn của bạn! Nó giống như có một cuốn sổ tay du hành thời gian tuyệt vời nhớ MỌI THỨ – từng lần gõ phím, từng thay đổi, từng khoảnh khắc "ôi, cái này làm hỏng mọi thứ" mà bạn có thể hoàn tác ngay lập tức.

Mình sẽ thành thật – điều này có thể cảm thấy choáng ngợp lúc đầu. Khi mình bắt đầu, mình đã nghĩ "Tại sao mình không thể chỉ lưu tệp như bình thường?" Nhưng hãy tin mình: một khi bạn hiểu Git (và bạn sẽ!), bạn sẽ có một khoảnh khắc "bật sáng" khi bạn nghĩ "Làm thế nào mà mình TỪNG lập trình mà không có cái này?" Nó giống như phát hiện ra bạn có thể bay khi bạn đã đi bộ khắp nơi cả đời!

Hãy giả sử bạn có một thư mục trên máy tính chứa một dự án mã nguồn và bạn muốn bắt đầu theo dõi tiến trình của mình bằng git - hệ thống kiểm soát phiên bản. Một số người so sánh việc sử dụng git với việc viết một lá thư tình cho bản thân trong tương lai. Đọc các thông điệp commit của bạn sau vài ngày, vài tuần hoặc vài tháng, bạn sẽ có thể nhớ lại lý do tại sao bạn đưa ra quyết định, hoặc "quay lại" một thay đổi - đó là khi bạn viết các thông điệp "commit" tốt.

### Nhiệm vụ: Tạo kho lưu trữ đầu tiên của bạn!

> 🎯 **Nhiệm vụ của bạn (và mình rất hào hứng vì bạn!)**: Chúng ta sẽ cùng nhau tạo kho lưu trữ GitHub đầu tiên của bạn! Đến khi hoàn thành, bạn sẽ có một góc nhỏ trên internet nơi mã nguồn của bạn sống, và bạn sẽ thực hiện lần "commit" đầu tiên của mình (đó là cách nói của lập trình viên để lưu công việc của bạn một cách thông minh).
>
> Đây thực sự là một khoảnh khắc đặc biệt – bạn sắp chính thức tham gia cộng đồng lập trình viên toàn cầu! Mình vẫn nhớ cảm giác hồi hộp khi tạo kho lưu trữ đầu tiên của mình và nghĩ "Wow, mình thực sự đang làm điều này!"

Hãy cùng nhau đi qua cuộc phiêu lưu này, từng bước một. Hãy dành thời gian cho từng phần – không có giải thưởng nào cho việc vội vàng, và mình hứa rằng từng bước sẽ có ý nghĩa. Hãy nhớ rằng, mọi ngôi sao lập trình bạn ngưỡng mộ đều từng ngồi đúng vị trí của bạn, chuẩn bị tạo kho lưu trữ đầu tiên của họ. Thật tuyệt phải không?

> Xem video
> 
> [![Video cơ bản về Git và GitHub](https://img.youtube.com/vi/9R31OUPpxU4/0.jpg)](https://www.youtube.com/watch?v=9R31OUPpxU4)

**Hãy cùng làm điều này:**

1. **Tạo kho lưu trữ của bạn trên GitHub**. Truy cập GitHub.com và tìm nút **New** màu xanh lá cây (hoặc dấu **+** ở góc trên bên phải). Nhấp vào đó và chọn **New repository**.

   Đây là những gì bạn cần làm:
   1. Đặt tên cho kho lưu trữ của bạn – hãy chọn một cái tên có ý nghĩa với bạn!
   1. Thêm mô tả nếu bạn muốn (điều này giúp người khác hiểu dự án của bạn là gì)
   1. Quyết định xem bạn muốn nó công khai (mọi người đều có thể xem) hay riêng tư (chỉ mình bạn)
   1. Mình khuyên bạn nên chọn hộp để thêm tệp README – nó giống như trang bìa của dự án của bạn
   1. Nhấp vào **Create repository** và ăn mừng – bạn vừa tạo kho lưu trữ đầu tiên của mình! 🎉

2. **Đi đến thư mục dự án của bạn**. Bây giờ hãy mở terminal của bạn (đừng lo, nó không đáng sợ như nó trông đâu!). Chúng ta cần nói với máy tính của bạn nơi các tệp dự án của bạn đang ở. Gõ lệnh này:

   ```bash
   cd [name of your folder]
   ```

   **Chúng ta đang làm gì ở đây:**
   - Chúng ta về cơ bản đang nói "Này máy tính, đưa tôi đến thư mục dự án của tôi"
   - Điều này giống như mở một thư mục cụ thể trên màn hình của bạn, nhưng chúng ta làm điều đó bằng lệnh văn bản
   - Thay thế `[name of your folder]` bằng tên thực tế của thư mục dự án của bạn

3. **Biến thư mục của bạn thành một kho lưu trữ Git**. Đây là lúc phép thuật xảy ra! Gõ:

   ```bash
   git init
   ```

   **Đây là những gì vừa xảy ra (thật tuyệt vời!):**
   - Git vừa tạo một thư mục ẩn `.git` trong dự án của bạn – bạn sẽ không thấy nó, nhưng nó ở đó!
   - Thư mục thông thường của bạn bây giờ là một "kho lưu trữ" có thể theo dõi mọi thay đổi bạn thực hiện
   - Hãy nghĩ về nó như việc trao cho thư mục của bạn siêu năng lực để nhớ mọi thứ

4. **Kiểm tra xem điều gì đang xảy ra**. Hãy xem Git nghĩ gì về dự án của bạn ngay bây giờ:

   ```bash
   git status
   ```

   **Hiểu những gì Git đang nói với bạn:**
   
   Bạn có thể thấy điều gì đó trông giống như thế này:

   ```output
   Changes not staged for commit:
   (use "git add <file>..." to update what will be committed)
   (use "git restore <file>..." to discard changes in working directory)

        modified:   file.txt
        modified:   file2.txt
   ```

   **Đừng hoảng sợ! Đây là ý nghĩa của điều này:**
   - Các tệp **màu đỏ** là các tệp đã thay đổi nhưng chưa sẵn sàng để lưu
   - Các tệp **màu xanh lá cây** (khi bạn thấy chúng) đã sẵn sàng để lưu
   - Git đang rất hữu ích khi nói cho bạn chính xác những gì bạn có thể làm tiếp theo

   > 💡 **Mẹo chuyên nghiệp**: Lệnh `git status` là người bạn tốt nhất của bạn! Sử dụng nó bất cứ khi nào bạn bối rối về điều gì đang xảy ra. Nó giống như hỏi Git "Này, tình hình hiện tại là gì?"

5. **Chuẩn bị các tệp của bạn để lưu** (điều này được gọi là "staging"):

   ```bash
   git add .
   ```

   **Những gì chúng ta vừa làm:**
   - Chúng ta đã nói với Git "Này, tôi muốn bao gồm TẤT CẢ các tệp của tôi trong lần lưu tiếp theo"
   - Dấu `.` giống như nói "mọi thứ trong thư mục này"
   - Bây giờ các tệp của bạn đã "staged" và sẵn sàng cho bước tiếp theo

   **Muốn chọn lọc hơn?** Bạn có thể chỉ thêm các tệp cụ thể:

   ```bash
   git add [file or folder name]
   ```

   **Tại sao bạn có thể muốn làm điều này?**
   - Đôi khi bạn muốn lưu các thay đổi liên quan với nhau
   - Nó giúp bạn tổ chức công việc thành các phần logic
   - Làm cho việc hiểu những gì đã thay đổi và khi nào dễ dàng hơn

   **Thay đổi ý định?** Không sao cả! Bạn có thể bỏ staging các tệp như thế này:

   ```bash
   # Unstage everything
   git reset
   
   # Unstage just one file
   git reset [file name]
   ```

   Đừng lo – điều này không xóa công việc của bạn, nó chỉ đưa các tệp ra khỏi "đống sẵn sàng để lưu".

6. **Lưu công việc của bạn vĩnh viễn** (thực hiện lần commit đầu tiên!):

   ```bash
   git commit -m "first commit"
   ```

   **🎉 Chúc mừng! Bạn vừa thực hiện lần commit đầu tiên của mình!**
   
   **Đây là những gì vừa xảy ra:**
   - Git đã chụp một "ảnh chụp" của tất cả các tệp đã staged của bạn tại thời điểm này
   - Thông điệp commit của bạn "first commit" giải thích về điểm lưu này
   - Git đã gán cho ảnh chụp này một ID duy nhất để bạn luôn có thể tìm thấy nó sau này
   - Bạn đã chính thức bắt đầu theo dõi lịch sử dự án của mình!

   > 💡 **Thông điệp commit trong tương lai**: Đối với các lần commit tiếp theo, hãy mô tả chi tiết hơn! Thay vì "updated stuff", hãy thử "Thêm form liên hệ vào trang chủ" hoặc "Sửa lỗi menu điều hướng". Tương lai bạn sẽ cảm ơn bạn!

7. **Kết nối dự án của bạn với GitHub**. Hiện tại, dự án của bạn chỉ tồn tại trên máy tính của bạn. Hãy kết nối nó với kho lưu trữ GitHub của bạn để bạn có thể chia sẻ nó với thế giới!

   Đầu tiên, truy cập trang kho lưu trữ GitHub của bạn và sao chép URL. Sau đó quay lại đây và gõ:

   ```bash
   git remote add origin https://github.com/username/repository_name.git
   ```
   
   (Thay URL đó bằng URL thực tế của kho lưu trữ của bạn!)

   **Những gì chúng ta vừa làm:**
   - Chúng tôi đã tạo kết nối giữa dự án cục bộ của bạn và kho lưu trữ GitHub của bạn
   - "Origin" chỉ là một biệt danh cho kho lưu trữ GitHub của bạn – giống như thêm một liên hệ vào điện thoại của bạn
   - Bây giờ Git cục bộ của bạn biết nơi để gửi mã của bạn khi bạn sẵn sàng chia sẻ nó

   💡 **Cách dễ hơn**: Nếu bạn đã cài đặt GitHub CLI, bạn có thể thực hiện điều này chỉ với một lệnh:
   ```bash
   gh repo create my-repo --public --push --source=.
   ```

8. **Gửi mã của bạn lên GitHub** (khoảnh khắc quan trọng!):

   ```bash
   git push -u origin main
   ```

   **🚀 Đây là lúc bạn tải mã của mình lên GitHub!**
   
   **Điều gì đang xảy ra:**
   - Các commit của bạn đang được chuyển từ máy tính của bạn lên GitHub
   - Cờ `-u` thiết lập kết nối vĩnh viễn để các lần đẩy sau dễ dàng hơn
   - "main" là tên nhánh chính của bạn (giống như thư mục chính)
   - Sau đó, bạn chỉ cần gõ `git push` cho các lần tải lên sau!

   💡 **Lưu ý nhanh**: Nếu nhánh của bạn có tên khác (như "master"), hãy sử dụng tên đó. Bạn có thể kiểm tra bằng `git branch --show-current`.

9. **Nhịp điệu lập trình hàng ngày mới của bạn** (đây là lúc bạn bị cuốn hút!):

   Từ giờ trở đi, bất cứ khi nào bạn thực hiện thay đổi trong dự án của mình, bạn sẽ có một quy trình ba bước đơn giản:

   ```bash
   git add .
   git commit -m "describe what you changed"
   git push
   ```

   **Đây sẽ trở thành nhịp điệu lập trình của bạn:**
   - Thực hiện một số thay đổi tuyệt vời cho mã của bạn ✨
   - Đánh dấu chúng bằng `git add` ("Này Git, chú ý đến những thay đổi này!")
   - Lưu chúng bằng `git commit` và một thông điệp mô tả (bạn trong tương lai sẽ cảm ơn bạn!)
   - Chia sẻ chúng với thế giới bằng `git push` 🚀
   - Lặp lại – thực sự, điều này sẽ trở nên tự nhiên như hít thở!

   Tôi yêu quy trình này vì nó giống như có nhiều điểm lưu trong một trò chơi điện tử. Thực hiện một thay đổi mà bạn yêu thích? Commit nó! Muốn thử điều gì đó mạo hiểm? Không vấn đề gì – bạn luôn có thể quay lại commit cuối cùng nếu mọi thứ không như ý!

   > 💡 **Mẹo**: Bạn cũng có thể muốn sử dụng tệp `.gitignore` để ngăn các tệp mà bạn không muốn theo dõi xuất hiện trên GitHub - như tệp ghi chú mà bạn lưu trong cùng thư mục nhưng không phù hợp với kho lưu trữ công khai. Bạn có thể tìm các mẫu tệp `.gitignore` tại [.gitignore templates](https://github.com/github/gitignore) hoặc tạo một tệp bằng [gitignore.io](https://www.toptal.com/developers/gitignore).

#### Quy trình Git hiện đại

Hãy cân nhắc áp dụng các thực hành hiện đại sau:

- **Conventional Commits**: Sử dụng định dạng thông điệp commit chuẩn như `feat:`, `fix:`, `docs:`, v.v. Tìm hiểu thêm tại [conventionalcommits.org](https://www.conventionalcommits.org/)
- **Atomic commits**: Mỗi commit đại diện cho một thay đổi logic duy nhất
- **Frequent commits**: Commit thường xuyên với thông điệp mô tả thay vì commit lớn, không thường xuyên

#### Thông điệp commit

Một dòng tiêu đề commit Git tuyệt vời hoàn thành câu sau:
Nếu được áp dụng, commit này sẽ <dòng tiêu đề của bạn ở đây>

Đối với tiêu đề, sử dụng thì hiện tại, dạng mệnh lệnh: "change" không phải "changed" hay "changes". 
Cũng như trong tiêu đề, trong phần thân (tùy chọn) cũng sử dụng thì hiện tại, dạng mệnh lệnh. Phần thân nên bao gồm lý do cho thay đổi và so sánh với hành vi trước đó. Bạn đang giải thích `tại sao`, không phải `như thế nào`.

✅ Dành vài phút để lướt qua GitHub. Bạn có thể tìm thấy một thông điệp commit thực sự tuyệt vời không? Bạn có thể tìm thấy một thông điệp tối giản không? Theo bạn, thông tin nào là quan trọng và hữu ích nhất để truyền tải trong một thông điệp commit?

## Làm việc với người khác (Phần thú vị!)

Hãy chuẩn bị tinh thần vì ĐÂY là lúc GitHub trở nên thực sự kỳ diệu! 🪄 Bạn đã thành thạo việc quản lý mã của riêng mình, nhưng bây giờ chúng ta sẽ khám phá phần tôi yêu thích nhất – cộng tác với những người tuyệt vời từ khắp nơi trên thế giới.

Hãy tưởng tượng: bạn thức dậy vào ngày mai và thấy rằng ai đó ở Tokyo đã cải thiện mã của bạn trong khi bạn đang ngủ. Sau đó, ai đó ở Berlin sửa một lỗi mà bạn đã mắc kẹt. Đến chiều, một nhà phát triển ở São Paulo đã thêm một tính năng mà bạn chưa từng nghĩ đến. Đó không phải là khoa học viễn tưởng – đó chỉ là một ngày thứ Ba trong vũ trụ GitHub!

Điều khiến tôi thực sự phấn khích là các kỹ năng cộng tác mà bạn sắp học? Đây chính là các quy trình mà các nhóm tại Google, Microsoft và các startup yêu thích của bạn sử dụng mỗi ngày. Bạn không chỉ học một công cụ thú vị – bạn đang học ngôn ngữ bí mật giúp toàn bộ thế giới phần mềm làm việc cùng nhau.

Thực sự, một khi bạn trải nghiệm cảm giác phấn khích khi ai đó hợp nhất pull request đầu tiên của bạn, bạn sẽ hiểu tại sao các nhà phát triển lại đam mê mã nguồn mở đến vậy. Nó giống như trở thành một phần của dự án nhóm lớn nhất, sáng tạo nhất thế giới!

> Xem video
>
> [![Video cơ bản về Git và GitHub](https://img.youtube.com/vi/bFCM-PC3cu8/0.jpg)](https://www.youtube.com/watch?v=bFCM-PC3cu8)

Lý do chính để đưa mọi thứ lên GitHub là để làm cho việc cộng tác với các nhà phát triển khác trở nên khả thi.

Trong kho lưu trữ của bạn, điều hướng đến `Insights > Community` để xem dự án của bạn so với các tiêu chuẩn cộng đồng được khuyến nghị như thế nào.

Muốn làm cho kho lưu trữ của bạn trông chuyên nghiệp và thân thiện? Hãy truy cập kho lưu trữ của bạn và nhấp vào `Insights > Community`. Tính năng thú vị này cho bạn thấy dự án của bạn so với những gì cộng đồng GitHub coi là "thực hành kho lưu trữ tốt".

> 🎯 **Làm cho dự án của bạn nổi bật**: Một kho lưu trữ được tổ chức tốt với tài liệu tốt giống như có một cửa hàng sạch sẽ, thân thiện. Nó cho mọi người thấy bạn quan tâm đến công việc của mình và khiến người khác muốn đóng góp!

**Đây là những gì làm cho một kho lưu trữ trở nên tuyệt vời:**

| Những gì cần thêm | Tại sao nó quan trọng | Nó làm gì cho bạn |
|-------------------|-----------------------|-------------------|
| **Mô tả** | Ấn tượng đầu tiên rất quan trọng! | Mọi người biết ngay dự án của bạn làm gì |
| **README** | Trang chính của dự án của bạn | Giống như một hướng dẫn thân thiện cho khách truy cập mới |
| **Hướng dẫn đóng góp** | Cho thấy bạn chào đón sự giúp đỡ | Mọi người biết chính xác cách họ có thể giúp bạn |
| **Quy tắc ứng xử** | Tạo không gian thân thiện | Mọi người cảm thấy được chào đón để tham gia |
| **Giấy phép** | Rõ ràng về pháp lý | Người khác biết cách họ có thể sử dụng mã của bạn |
| **Chính sách bảo mật** | Cho thấy bạn có trách nhiệm | Thể hiện các thực hành chuyên nghiệp |

> 💡 **Mẹo chuyên nghiệp**: GitHub cung cấp các mẫu cho tất cả các tệp này. Khi tạo một kho lưu trữ mới, hãy chọn các hộp để tự động tạo các tệp này.

**Các tính năng GitHub hiện đại để khám phá:**

🤖 **Tự động hóa & CI/CD:**
- **GitHub Actions** để kiểm tra và triển khai tự động
- **Dependabot** để cập nhật tự động các phụ thuộc

💬 **Cộng đồng & Quản lý dự án:**
- **GitHub Discussions** cho các cuộc trò chuyện cộng đồng ngoài các vấn đề
- **GitHub Projects** để quản lý dự án kiểu kanban
- **Quy tắc bảo vệ nhánh** để đảm bảo tiêu chuẩn chất lượng mã

Tất cả các tài nguyên này sẽ có lợi cho việc giới thiệu thành viên mới vào nhóm. Và đây thường là những điều mà các cộng tác viên mới xem xét trước khi thậm chí nhìn vào mã của bạn, để tìm hiểu xem dự án của bạn có phải là nơi phù hợp để họ dành thời gian hay không.

✅ Các tệp README, mặc dù mất thời gian để chuẩn bị, thường bị bỏ qua bởi các người duy trì bận rộn. Bạn có thể tìm thấy một ví dụ về một tệp README đặc biệt mô tả không? Lưu ý: có một số [công cụ giúp tạo tệp README tốt](https://www.makeareadme.com/) mà bạn có thể muốn thử.

### Nhiệm vụ: Hợp nhất một số mã

Tài liệu đóng góp giúp mọi người đóng góp vào dự án. Nó giải thích các loại đóng góp mà bạn đang tìm kiếm và cách quy trình hoạt động. Các cộng tác viên sẽ cần thực hiện một loạt các bước để có thể đóng góp vào kho lưu trữ của bạn trên GitHub:

1. **Fork kho lưu trữ của bạn** Bạn có thể muốn mọi người _fork_ dự án của bạn. Fork nghĩa là tạo một bản sao của kho lưu trữ của bạn trên hồ sơ GitHub của họ.
1. **Clone**. Từ đó họ sẽ clone dự án về máy cục bộ của họ. 
1. **Tạo một nhánh**. Bạn sẽ muốn yêu cầu họ tạo một _nhánh_ cho công việc của họ. 
1. **Tập trung vào một thay đổi**. Yêu cầu các cộng tác viên tập trung đóng góp của họ vào một điều tại một thời điểm - theo cách đó khả năng bạn có thể _hợp nhất_ công việc của họ sẽ cao hơn. Hãy tưởng tượng họ viết một bản sửa lỗi, thêm một tính năng mới và cập nhật một số bài kiểm tra - điều gì sẽ xảy ra nếu bạn muốn, hoặc chỉ có thể triển khai 2 trong số 3, hoặc 1 trong số 3 thay đổi?

✅ Hãy tưởng tượng một tình huống mà các nhánh đặc biệt quan trọng để viết và triển khai mã tốt. Bạn có thể nghĩ đến những trường hợp sử dụng nào?

> Lưu ý, hãy là sự thay đổi mà bạn muốn thấy trên thế giới, và tạo nhánh cho công việc của riêng bạn. Bất kỳ commit nào bạn thực hiện sẽ được thực hiện trên nhánh mà bạn hiện đang "checked out". Sử dụng `git status` để xem đó là nhánh nào.

Hãy đi qua quy trình làm việc của cộng tác viên. Giả sử cộng tác viên đã _fork_ và _clone_ kho lưu trữ để họ có một kho Git sẵn sàng làm việc trên máy cục bộ của họ:

1. **Tạo một nhánh**. Sử dụng lệnh `git branch` để tạo một nhánh sẽ chứa các thay đổi mà họ dự định đóng góp:

   ```bash
   git branch [branch-name]
   ```

   > 💡 **Cách tiếp cận hiện đại**: Bạn cũng có thể tạo và chuyển sang nhánh mới chỉ với một lệnh:
   ```bash
   git switch -c [branch-name]
   ```

1. **Chuyển sang nhánh làm việc**. Chuyển sang nhánh được chỉ định và cập nhật thư mục làm việc bằng `git switch`:

   ```bash
   git switch [branch-name]
   ```

   > 💡 **Lưu ý hiện đại**: `git switch` là sự thay thế hiện đại cho `git checkout` khi thay đổi nhánh. Nó rõ ràng hơn và an toàn hơn cho người mới bắt đầu.

1. **Thực hiện công việc**. Tại thời điểm này bạn muốn thêm các thay đổi của mình. Đừng quên thông báo cho Git về điều đó bằng các lệnh sau:

   ```bash
   git add .
   git commit -m "my changes"
   ```

   > ⚠️ **Chất lượng thông điệp commit**: Đảm bảo bạn đặt tên commit tốt, cả vì lợi ích của bạn và người duy trì kho lưu trữ mà bạn đang giúp đỡ. Hãy cụ thể về những gì bạn đã thay đổi!

1. **Kết hợp công việc của bạn với nhánh `main`**. Tại một thời điểm nào đó bạn đã hoàn thành công việc và muốn kết hợp công việc của mình với nhánh `main`. Nhánh `main` có thể đã thay đổi trong khi đó, vì vậy hãy đảm bảo bạn cập nhật nó lên phiên bản mới nhất bằng các lệnh sau:

   ```bash
   git switch main
   git pull
   ```

   Tại thời điểm này bạn muốn đảm bảo rằng bất kỳ _xung đột_ nào, tình huống mà Git không thể dễ dàng _kết hợp_ các thay đổi xảy ra trong nhánh làm việc của bạn. Do đó, chạy các lệnh sau:

   ```bash
   git switch [branch_name]
   git merge main
   ```

   Lệnh `git merge main` sẽ mang tất cả các thay đổi từ `main` vào nhánh của bạn. Hy vọng bạn có thể tiếp tục. Nếu không, VS Code sẽ cho bạn biết nơi Git bị _nhầm lẫn_ và bạn chỉ cần thay đổi các tệp bị ảnh hưởng để nói nội dung nào là chính xác nhất.

   💡 **Cách thay thế hiện đại**: Cân nhắc sử dụng `git rebase` để có lịch sử sạch hơn:
   ```bash
   git rebase main
   ```
   Điều này sẽ phát lại các commit của bạn trên đầu nhánh `main` mới nhất, tạo ra một lịch sử tuyến tính.

1. **Gửi công việc của bạn lên GitHub**. Gửi công việc của bạn lên GitHub nghĩa là hai điều. Đẩy nhánh của bạn lên kho lưu trữ của bạn và sau đó mở một PR, Pull Request.

   ```bash
   git push --set-upstream origin [branch-name]
   ```

   Lệnh trên tạo nhánh trên kho lưu trữ đã fork của bạn.

1. **Mở một PR**. Tiếp theo, bạn muốn mở một PR. Bạn làm điều đó bằng cách điều hướng đến kho lưu trữ đã fork trên GitHub. Bạn sẽ thấy một thông báo trên GitHub hỏi liệu bạn có muốn tạo một PR mới không, bạn nhấp vào đó và được đưa đến giao diện nơi bạn có thể thay đổi tiêu đề thông điệp commit, đưa ra mô tả phù hợp hơn. Bây giờ người duy trì kho lưu trữ mà bạn đã fork sẽ thấy PR này và _hy vọng_ họ sẽ đánh giá cao và _hợp nhất_ PR của bạn. Bạn bây giờ là một cộng tác viên, yay :)

   💡 **Mẹo hiện đại**: Bạn cũng có thể tạo PRs bằng GitHub CLI:
   ```bash
   gh pr create --title "Your PR title" --body "Description of changes"
   ```

   🔧 **Thực hành tốt nhất cho PRs**:
   - Liên kết đến các vấn đề liên quan bằng các từ khóa như "Fixes #123"
   - Thêm ảnh chụp màn hình cho các thay đổi giao diện người dùng
   - Yêu cầu người đánh giá cụ thể
   - Sử dụng PR nháp cho công việc đang tiến hành
   - Đảm bảo tất cả các kiểm tra CI đều vượt qua trước khi yêu cầu đánh giá

1. **Dọn dẹp**. Được coi là thực hành tốt để _dọn dẹp_ sau khi bạn đã hợp nhất thành công một PR. Bạn muốn dọn dẹp cả nhánh cục bộ và nhánh bạn đã đẩy lên GitHub. Đầu tiên hãy xóa nó cục bộ bằng lệnh sau:

   ```bash
   git branch -d [branch-name]
   ```

   Đảm bảo bạn truy cập trang GitHub cho kho lưu trữ đã fork tiếp theo và xóa nhánh từ xa mà bạn vừa đẩy lên.

`Pull request` có vẻ như là một thuật ngữ ngớ ngẩn vì thực sự bạn muốn đẩy các thay đổi của mình vào dự án. Nhưng người duy trì (chủ dự án) hoặc nhóm cốt lõi cần xem xét các thay đổi của bạn trước khi hợp nhất chúng với nhánh "main" của dự án, vì vậy bạn thực sự đang yêu cầu một quyết định thay đổi từ người duy trì.

Pull request là nơi để so sánh và thảo luận về các khác biệt được giới thiệu trên một nhánh với các đánh giá, nhận xét, kiểm tra tích hợp, và hơn thế nữa. Một pull request tốt tuân theo các quy tắc tương tự như một thông điệp commit. Bạn có thể thêm tham chiếu đến một vấn đề trong trình theo dõi vấn đề, khi công việc của bạn ví dụ như sửa một vấn đề. Điều này được thực hiện bằng cách sử dụng `#` theo sau bởi số của vấn đề của bạn. Ví dụ `#97`.
🤞Hy vọng rằng tất cả các kiểm tra đều vượt qua và chủ dự án sẽ hợp nhất các thay đổi của bạn vào dự án🤞

Cập nhật nhánh làm việc cục bộ hiện tại của bạn với tất cả các commit mới từ nhánh tương ứng trên GitHub:

`git pull`

## Đóng góp cho mã nguồn mở (Cơ hội để bạn tạo ra sự khác biệt!)

Bạn đã sẵn sàng cho điều gì đó sẽ khiến bạn kinh ngạc chưa? 🤯 Hãy nói về việc đóng góp cho các dự án mã nguồn mở – và tôi cảm thấy nổi da gà khi nghĩ đến việc chia sẻ điều này với bạn!

Đây là cơ hội để bạn trở thành một phần của điều gì đó thực sự phi thường. Hãy tưởng tượng bạn cải thiện các công cụ mà hàng triệu nhà phát triển sử dụng mỗi ngày, hoặc sửa một lỗi trong ứng dụng mà bạn bè của bạn yêu thích. Đó không chỉ là một giấc mơ – đó chính là những gì đóng góp mã nguồn mở mang lại!

Điều khiến tôi luôn cảm thấy phấn khích mỗi khi nghĩ về nó: mọi công cụ mà bạn đã học – trình soạn thảo mã, các framework mà chúng ta sẽ khám phá, thậm chí trình duyệt mà bạn đang đọc nội dung này – đều bắt đầu từ một người giống như bạn, thực hiện đóng góp đầu tiên của họ. Nhà phát triển tài năng đã tạo ra tiện ích mở rộng VS Code yêu thích của bạn? Họ cũng từng là người mới, nhấn "create pull request" với đôi tay run rẩy, giống như bạn sắp làm.

Và đây là phần đẹp nhất: cộng đồng mã nguồn mở giống như một cái ôm lớn nhất trên internet. Hầu hết các dự án đều tích cực tìm kiếm người mới và có các vấn đề được gắn thẻ "good first issue" dành riêng cho những người như bạn! Những người duy trì dự án thực sự rất vui khi thấy các nhà đóng góp mới vì họ nhớ lại những bước đầu tiên của mình.

Bạn không chỉ học cách viết mã ở đây – bạn đang chuẩn bị tham gia vào một gia đình toàn cầu của những người xây dựng, những người thức dậy mỗi ngày với suy nghĩ "Làm thế nào để chúng ta làm cho thế giới số trở nên tốt hơn một chút?" Chào mừng bạn đến với câu lạc bộ! 🌟

Đầu tiên, hãy tìm một kho lưu trữ (hoặc **repo**) trên GitHub mà bạn quan tâm và muốn đóng góp một thay đổi. Bạn sẽ muốn sao chép nội dung của nó về máy của mình.

✅ Một cách tốt để tìm các repo 'thân thiện với người mới bắt đầu' là [tìm kiếm theo thẻ 'good-first-issue'](https://github.blog/2020-01-22-browse-good-first-issues-to-start-contributing-to-open-source/).

![Sao chép repo về máy](../../../../translated_images/clone_repo.5085c48d666ead57664f050d806e325d7f883be6838c821e08bc823ab7c66665.vi.png)

Có nhiều cách để sao chép mã. Một cách là "clone" nội dung của kho lưu trữ, sử dụng HTTPS, SSH, hoặc sử dụng GitHub CLI (Command Line Interface).

Mở terminal của bạn và clone kho lưu trữ như sau:
```bash
# Using HTTPS
git clone https://github.com/ProjectURL

# Using SSH (requires SSH key setup)
git clone git@github.com:username/repository.git

# Using GitHub CLI
gh repo clone username/repository
```

Để làm việc trên dự án, chuyển đến thư mục phù hợp:
`cd ProjectURL`

Bạn cũng có thể mở toàn bộ dự án bằng:
- **[GitHub Codespaces](https://github.com/features/codespaces)** - Môi trường phát triển trên đám mây của GitHub với VS Code trong trình duyệt
- **[GitHub Desktop](https://desktop.github.com/)** - Ứng dụng GUI cho các thao tác Git  
- **[GitHub.dev](https://github.dev)** - Nhấn phím `.` trên bất kỳ repo GitHub nào để mở VS Code trong trình duyệt
- **VS Code** với tiện ích mở rộng GitHub Pull Requests

Cuối cùng, bạn có thể tải mã xuống dưới dạng thư mục nén.

### Một vài điều thú vị về GitHub

Bạn có thể gắn sao, theo dõi và/hoặc "fork" bất kỳ kho lưu trữ công khai nào trên GitHub. Bạn có thể tìm thấy các kho lưu trữ đã gắn sao của mình trong menu thả xuống ở góc trên bên phải. Nó giống như đánh dấu trang, nhưng dành cho mã.

Các dự án có một trình theo dõi vấn đề, chủ yếu trên GitHub trong tab "Issues" trừ khi được chỉ định khác, nơi mọi người thảo luận về các vấn đề liên quan đến dự án. Và tab Pull Requests là nơi mọi người thảo luận và xem xét các thay đổi đang được thực hiện.

Các dự án cũng có thể có thảo luận trong các diễn đàn, danh sách gửi thư, hoặc các kênh chat như Slack, Discord hoặc IRC.

🔧 **Các tính năng hiện đại của GitHub**:
- **GitHub Discussions** - Diễn đàn tích hợp cho các cuộc trò chuyện cộng đồng
- **GitHub Sponsors** - Hỗ trợ tài chính cho những người duy trì dự án  
- **Security tab** - Báo cáo lỗ hổng và tư vấn bảo mật
- **Actions tab** - Xem các quy trình tự động và pipeline CI/CD
- **Insights tab** - Phân tích về các nhà đóng góp, commit, và sức khỏe dự án
- **Projects tab** - Công cụ quản lý dự án tích hợp của GitHub

✅ Hãy khám phá kho lưu trữ GitHub mới của bạn và thử một vài điều, như chỉnh sửa cài đặt, thêm thông tin vào repo của bạn, tạo một dự án (như bảng Kanban), và thiết lập GitHub Actions để tự động hóa. Có rất nhiều điều bạn có thể làm!

---

## 🚀 Thử thách 

Được rồi, đã đến lúc thử nghiệm các siêu năng lực GitHub mới của bạn! 🚀 Đây là một thử thách sẽ giúp mọi thứ trở nên rõ ràng theo cách thỏa mãn nhất:

Hãy rủ một người bạn (hoặc thành viên gia đình luôn hỏi bạn đang làm gì với tất cả những thứ "máy tính này") và cùng nhau bắt đầu một cuộc phiêu lưu mã hóa hợp tác! Đây là nơi phép màu thực sự xảy ra – tạo một dự án, để họ fork nó, tạo một số nhánh, và hợp nhất các thay đổi như những chuyên gia mà bạn đang trở thành.

Tôi không nói dối đâu – bạn có thể sẽ cười vào một lúc nào đó (đặc biệt là khi cả hai cố gắng thay đổi cùng một dòng), có thể sẽ gãi đầu bối rối, nhưng chắc chắn bạn sẽ có những khoảnh khắc "aha!" tuyệt vời khiến tất cả việc học trở nên đáng giá. Thêm vào đó, có điều gì đó đặc biệt khi chia sẻ lần hợp nhất thành công đầu tiên với người khác – nó giống như một lễ kỷ niệm nhỏ về việc bạn đã tiến xa đến mức nào!

Chưa có bạn đồng hành mã hóa? Không sao cả! Cộng đồng GitHub đầy những người cực kỳ thân thiện, những người nhớ cảm giác khi mới bắt đầu. Hãy tìm các kho lưu trữ có nhãn "good first issue" – chúng về cơ bản đang nói "Này người mới, hãy học cùng chúng tôi!" Thật tuyệt phải không?

## Câu hỏi sau bài giảng
[Câu hỏi sau bài giảng](https://ff-quizzes.netlify.app/web/en/)

## Ôn tập & Tiếp tục học

Whew! 🎉 Nhìn bạn kìa – bạn vừa chinh phục các kiến thức cơ bản về GitHub như một nhà vô địch thực thụ! Nếu bạn cảm thấy đầu óc hơi đầy lúc này, điều đó hoàn toàn bình thường và thực sự là một dấu hiệu tốt. Bạn vừa học các công cụ mà tôi đã mất hàng tuần để cảm thấy thoải mái khi bắt đầu.

Git và GitHub cực kỳ mạnh mẽ (thật sự mạnh mẽ), và mọi nhà phát triển mà tôi biết – bao gồm cả những người trông như phù thủy bây giờ – đều phải thực hành và vấp ngã một chút trước khi mọi thứ trở nên rõ ràng. Việc bạn đã hoàn thành bài học này có nghĩa là bạn đã trên đường làm chủ một số công cụ quan trọng nhất trong bộ công cụ của nhà phát triển.

Dưới đây là một số tài nguyên tuyệt vời để giúp bạn thực hành và trở nên thậm chí còn tuyệt vời hơn:

- [Hướng dẫn đóng góp cho phần mềm mã nguồn mở](https://opensource.guide/how-to-contribute/#how-to-submit-a-contribution) – Lộ trình của bạn để tạo ra sự khác biệt
- [Bảng cheat Git](https://training.github.com/downloads/github-git-cheat-sheet/) – Giữ cái này bên mình để tham khảo nhanh!

Và hãy nhớ: thực hành tạo tiến bộ, không phải sự hoàn hảo! Càng sử dụng Git và GitHub, bạn sẽ càng thấy tự nhiên hơn. GitHub đã tạo ra một số khóa học tương tác tuyệt vời cho phép bạn thực hành trong môi trường an toàn:

- [Giới thiệu về GitHub](https://github.com/skills/introduction-to-github)
- [Giao tiếp bằng Markdown](https://github.com/skills/communicate-using-markdown)  
- [GitHub Pages](https://github.com/skills/github-pages)
- [Quản lý xung đột hợp nhất](https://github.com/skills/resolve-merge-conflicts)

**Cảm thấy phiêu lưu? Hãy khám phá các công cụ hiện đại này:**
- [Tài liệu GitHub CLI](https://cli.github.com/manual/) – Để cảm thấy như một phù thủy dòng lệnh
- [Tài liệu GitHub Codespaces](https://docs.github.com/en/codespaces) – Mã hóa trên đám mây!
- [Tài liệu GitHub Actions](https://docs.github.com/en/actions) – Tự động hóa mọi thứ
- [Các thực hành tốt nhất về Git](https://www.atlassian.com/git/tutorials/comparing-workflows) – Nâng cấp trò chơi quy trình làm việc của bạn

## Thử thách GitHub Copilot Agent 🚀

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Tạo một dự án phát triển web hợp tác thể hiện toàn bộ quy trình GitHub mà bạn đã học trong bài học này. Thử thách này sẽ giúp bạn thực hành tạo kho lưu trữ, các tính năng hợp tác, và quy trình làm việc Git hiện đại trong một tình huống thực tế.

**Yêu cầu:** Tạo một kho lưu trữ GitHub công khai mới cho dự án "Web Development Resources" đơn giản. Kho lưu trữ nên bao gồm một tệp README.md được cấu trúc tốt liệt kê các công cụ và tài nguyên phát triển web hữu ích, được tổ chức theo danh mục (HTML, CSS, JavaScript, v.v.). Thiết lập kho lưu trữ với các tiêu chuẩn cộng đồng phù hợp bao gồm giấy phép, hướng dẫn đóng góp, và quy tắc ứng xử. Tạo ít nhất hai nhánh tính năng: một để thêm tài nguyên CSS và một để thêm tài nguyên JavaScript. Thực hiện các commit cho mỗi nhánh với các thông điệp commit mô tả, sau đó tạo pull request để hợp nhất các thay đổi trở lại nhánh chính. Kích hoạt các tính năng GitHub như Issues, Discussions, và thiết lập một quy trình GitHub Actions cơ bản để kiểm tra tự động.

## Bài tập 

Nhiệm vụ của bạn, nếu bạn chọn chấp nhận: Hoàn thành khóa học [Giới thiệu về GitHub](https://github.com/skills/introduction-to-github) trên GitHub Skills. Khóa học tương tác này sẽ cho phép bạn thực hành mọi thứ bạn đã học trong môi trường an toàn, có hướng dẫn. Thêm vào đó, bạn sẽ nhận được một huy hiệu tuyệt vời khi hoàn thành! 🏅

**Cảm thấy sẵn sàng cho nhiều thử thách hơn?**
- Thiết lập xác thực SSH cho tài khoản GitHub của bạn (không cần mật khẩu nữa!)
- Thử sử dụng GitHub CLI cho các thao tác Git hàng ngày của bạn
- Tạo một kho lưu trữ với quy trình GitHub Actions
- Khám phá GitHub Codespaces bằng cách mở chính kho lưu trữ này trong trình chỉnh sửa dựa trên đám mây

Hãy nhớ: mọi chuyên gia đều từng là người mới bắt đầu. Bạn làm được mà! 💪

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.