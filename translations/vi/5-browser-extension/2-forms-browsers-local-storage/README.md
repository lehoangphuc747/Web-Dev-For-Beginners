<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8c8cd4af6086cc1d47e1d43aa4983d20",
  "translation_date": "2025-10-24T13:53:46+00:00",
  "source_file": "5-browser-extension/2-forms-browsers-local-storage/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../../README.md) | [◀️ Quay lại](../README.md) | [▶️ Bài tiếp theo](../3-background-tasks-and-performance/README.md)

---
# Dự án Tiện ích Trình duyệt Phần 2: Gọi API, sử dụng Local Storage

## Câu hỏi trước bài giảng

[Câu hỏi trước bài giảng](https://ff-quizzes.netlify.app/web/quiz/25)

## Giới thiệu

Bạn còn nhớ tiện ích trình duyệt mà bạn đã bắt đầu xây dựng không? Hiện tại bạn đã có một biểu mẫu trông đẹp mắt, nhưng nó vẫn còn khá tĩnh. Hôm nay, chúng ta sẽ làm cho nó trở nên sống động bằng cách kết nối với dữ liệu thực và cung cấp khả năng ghi nhớ.

Hãy nghĩ về các máy tính điều khiển nhiệm vụ Apollo - chúng không chỉ hiển thị thông tin cố định. Chúng liên tục giao tiếp với tàu vũ trụ, cập nhật dữ liệu từ xa và ghi nhớ các thông số quan trọng của nhiệm vụ. Đó là loại hành vi động mà chúng ta sẽ xây dựng hôm nay. Tiện ích của bạn sẽ kết nối với internet, lấy dữ liệu môi trường thực và ghi nhớ các cài đặt của bạn cho lần sử dụng tiếp theo.

Tích hợp API có thể nghe có vẻ phức tạp, nhưng thực chất chỉ là dạy mã của bạn cách giao tiếp với các dịch vụ khác. Dù bạn đang lấy dữ liệu thời tiết, nguồn cấp dữ liệu mạng xã hội hay thông tin về dấu chân carbon như chúng ta sẽ làm hôm nay, tất cả đều xoay quanh việc thiết lập các kết nối kỹ thuật số này. Chúng ta cũng sẽ khám phá cách trình duyệt có thể lưu trữ thông tin - giống như cách các thư viện sử dụng danh mục thẻ để ghi nhớ vị trí của sách.

Kết thúc bài học này, bạn sẽ có một tiện ích trình duyệt có thể lấy dữ liệu thực, lưu trữ tùy chọn của người dùng và cung cấp trải nghiệm mượt mà. Hãy bắt đầu nào!

✅ Làm theo các phân đoạn được đánh số trong các tệp tương ứng để biết nơi đặt mã của bạn.

## Thiết lập các phần tử để thao tác trong tiện ích

Trước khi JavaScript của bạn có thể thao tác giao diện, nó cần tham chiếu đến các phần tử HTML cụ thể. Hãy nghĩ về nó như một kính thiên văn cần được hướng vào các ngôi sao cụ thể - trước khi Galileo có thể nghiên cứu các mặt trăng của sao Mộc, ông phải xác định và tập trung vào chính sao Mộc.

Trong tệp `index.js` của bạn, chúng ta sẽ tạo các biến `const` để lưu tham chiếu đến từng phần tử biểu mẫu quan trọng. Điều này giống như cách các nhà khoa học gắn nhãn thiết bị của họ - thay vì tìm kiếm toàn bộ phòng thí nghiệm mỗi lần, họ có thể truy cập trực tiếp vào những gì họ cần.

```javascript
// form fields
const form = document.querySelector('.form-data');
const region = document.querySelector('.region-name');
const apiKey = document.querySelector('.api-key');

// results
const errors = document.querySelector('.errors');
const loading = document.querySelector('.loading');
const results = document.querySelector('.result-container');
const usage = document.querySelector('.carbon-usage');
const fossilfuel = document.querySelector('.fossil-fuel');
const myregion = document.querySelector('.my-region');
const clearBtn = document.querySelector('.clear-btn');
```

**Mã này làm gì:**
- **Lấy** các phần tử biểu mẫu bằng cách sử dụng `document.querySelector()` với các bộ chọn lớp CSS
- **Tạo** các tham chiếu đến các trường nhập liệu cho tên khu vực và khóa API
- **Thiết lập** kết nối với các phần tử hiển thị kết quả cho dữ liệu sử dụng carbon
- **Cài đặt** quyền truy cập vào các phần tử giao diện người dùng như chỉ báo tải và thông báo lỗi
- **Lưu trữ** mỗi tham chiếu phần tử trong một biến `const` để dễ dàng tái sử dụng trong mã của bạn

## Thêm các trình lắng nghe sự kiện

Bây giờ chúng ta sẽ làm cho tiện ích của bạn phản hồi các hành động của người dùng. Các trình lắng nghe sự kiện là cách mã của bạn theo dõi các tương tác của người dùng. Hãy nghĩ về chúng như các nhà điều hành trong các tổng đài điện thoại thời kỳ đầu - họ lắng nghe các cuộc gọi đến và kết nối các mạch đúng khi ai đó muốn thực hiện một kết nối.

```javascript
form.addEventListener('submit', (e) => handleSubmit(e));
clearBtn.addEventListener('click', (e) => reset(e));
init();
```

**Hiểu các khái niệm này:**
- **Gắn** một trình lắng nghe gửi đến biểu mẫu kích hoạt khi người dùng nhấn Enter hoặc nhấp vào gửi
- **Kết nối** một trình lắng nghe nhấp chuột vào nút xóa để đặt lại biểu mẫu
- **Truyền** đối tượng sự kiện `(e)` đến các hàm xử lý để kiểm soát thêm
- **Gọi** hàm `init()` ngay lập tức để thiết lập trạng thái ban đầu của tiện ích

✅ Lưu ý cú pháp hàm mũi tên rút gọn được sử dụng ở đây. Cách tiếp cận JavaScript hiện đại này sạch hơn so với các biểu thức hàm truyền thống, nhưng cả hai đều hoạt động tốt như nhau!

## Xây dựng các hàm khởi tạo và đặt lại

Hãy tạo logic khởi tạo cho tiện ích của bạn. Hàm `init()` giống như hệ thống điều hướng của một con tàu kiểm tra các thiết bị của nó - nó xác định trạng thái hiện tại và điều chỉnh giao diện cho phù hợp. Nó kiểm tra xem ai đó đã sử dụng tiện ích của bạn trước đây chưa và tải các cài đặt trước của họ.

Hàm `reset()` cung cấp cho người dùng một khởi đầu mới - giống như cách các nhà khoa học đặt lại thiết bị của họ giữa các thí nghiệm để đảm bảo dữ liệu sạch.

```javascript
function init() {
	// Check if user has previously saved API credentials
	const storedApiKey = localStorage.getItem('apiKey');
	const storedRegion = localStorage.getItem('regionName');

	// Set extension icon to generic green (placeholder for future lesson)
	// TODO: Implement icon update in next lesson

	if (storedApiKey === null || storedRegion === null) {
		// First-time user: show the setup form
		form.style.display = 'block';
		results.style.display = 'none';
		loading.style.display = 'none';
		clearBtn.style.display = 'none';
		errors.textContent = '';
	} else {
		// Returning user: load their saved data automatically
		displayCarbonUsage(storedApiKey, storedRegion);
		results.style.display = 'none';
		form.style.display = 'none';
		clearBtn.style.display = 'block';
	}
}

function reset(e) {
	e.preventDefault();
	// Clear stored region to allow user to choose a new location
	localStorage.removeItem('regionName');
	// Restart the initialization process
	init();
}
```

**Phân tích những gì xảy ra ở đây:**
- **Lấy** khóa API và khu vực được lưu trữ từ bộ nhớ cục bộ của trình duyệt
- **Kiểm tra** xem đây có phải là người dùng lần đầu (không có thông tin đăng nhập được lưu trữ) hay người dùng quay lại
- **Hiển thị** biểu mẫu thiết lập cho người dùng mới và ẩn các phần tử giao diện khác
- **Tải** dữ liệu đã lưu tự động cho người dùng quay lại và hiển thị tùy chọn đặt lại
- **Quản lý** trạng thái giao diện người dùng dựa trên dữ liệu có sẵn

**Các khái niệm chính về Local Storage:**
- **Lưu trữ** dữ liệu giữa các phiên trình duyệt (khác với session storage)
- **Lưu trữ** dữ liệu dưới dạng cặp khóa-giá trị bằng cách sử dụng `getItem()` và `setItem()`
- **Trả về** `null` khi không có dữ liệu tồn tại cho một khóa nhất định
- **Cung cấp** một cách đơn giản để ghi nhớ tùy chọn và cài đặt của người dùng

> 💡 **Hiểu về Bộ nhớ Trình duyệt**: [LocalStorage](https://developer.mozilla.org/docs/Web/API/Window/localStorage) giống như việc cung cấp cho tiện ích của bạn bộ nhớ lâu dài. Hãy xem xét cách Thư viện Alexandria cổ đại lưu trữ các cuộn giấy - thông tin vẫn có sẵn ngay cả khi các học giả rời đi và quay lại.
>
> **Đặc điểm chính:**
> - **Lưu trữ** dữ liệu ngay cả khi bạn đóng trình duyệt
> - **Tồn tại** sau khi khởi động lại máy tính và trình duyệt bị treo
> - **Cung cấp** không gian lưu trữ đáng kể cho các tùy chọn của người dùng
> - **Truy cập** ngay lập tức mà không có độ trễ mạng

> **Lưu ý quan trọng**: Tiện ích trình duyệt của bạn có bộ nhớ cục bộ riêng biệt, tách biệt với các trang web thông thường. Điều này cung cấp bảo mật và ngăn chặn xung đột với các trang web khác.

Bạn có thể xem dữ liệu đã lưu của mình bằng cách mở Công cụ dành cho nhà phát triển của trình duyệt (F12), điều hướng đến tab **Application**, và mở rộng phần **Local Storage**.

![Local storage pane](../../../../translated_images/localstorage.472f8147b6a3f8d141d9551c95a2da610ac9a3c6a73d4a1c224081c98bae09d9.vi.png)

> ⚠️ **Cân nhắc về bảo mật**: Trong các ứng dụng sản xuất, việc lưu trữ khóa API trong LocalStorage có thể gây rủi ro bảo mật vì JavaScript có thể truy cập dữ liệu này. Đối với mục đích học tập, cách tiếp cận này là ổn, nhưng các ứng dụng thực tế nên sử dụng lưu trữ an toàn phía máy chủ cho các thông tin nhạy cảm.

## Xử lý gửi biểu mẫu

Bây giờ chúng ta sẽ xử lý những gì xảy ra khi ai đó gửi biểu mẫu của bạn. Theo mặc định, trình duyệt sẽ tải lại trang khi biểu mẫu được gửi, nhưng chúng ta sẽ chặn hành vi này để tạo trải nghiệm mượt mà hơn.

Cách tiếp cận này giống như cách điều khiển nhiệm vụ xử lý giao tiếp với tàu vũ trụ - thay vì đặt lại toàn bộ hệ thống cho mỗi lần truyền, họ duy trì hoạt động liên tục trong khi xử lý thông tin mới.

Tạo một hàm để lấy sự kiện gửi biểu mẫu và trích xuất đầu vào của người dùng:

```javascript
function handleSubmit(e) {
	e.preventDefault();
	setUpUser(apiKey.value, region.value);
}
```

**Trong đoạn mã trên, chúng ta đã:**
- **Ngăn chặn** hành vi gửi biểu mẫu mặc định sẽ làm mới trang
- **Trích xuất** giá trị đầu vào của người dùng từ các trường khóa API và khu vực
- **Truyền** dữ liệu biểu mẫu đến hàm `setUpUser()` để xử lý
- **Duy trì** hành vi ứng dụng một trang bằng cách tránh làm mới trang

✅ Hãy nhớ rằng các trường biểu mẫu HTML của bạn bao gồm thuộc tính `required`, vì vậy trình duyệt sẽ tự động xác thực rằng người dùng cung cấp cả khóa API và khu vực trước khi hàm này chạy.

## Thiết lập tùy chọn người dùng

Hàm `setUpUser` chịu trách nhiệm lưu trữ thông tin đăng nhập của người dùng và bắt đầu cuộc gọi API đầu tiên. Điều này tạo ra một chuyển đổi mượt mà từ thiết lập sang hiển thị kết quả.

```javascript
function setUpUser(apiKey, regionName) {
	// Save user credentials for future sessions
	localStorage.setItem('apiKey', apiKey);
	localStorage.setItem('regionName', regionName);
	
	// Update UI to show loading state
	loading.style.display = 'block';
	errors.textContent = '';
	clearBtn.style.display = 'block';
	
	// Fetch carbon usage data with user's credentials
	displayCarbonUsage(apiKey, regionName);
}
```

**Từng bước, đây là những gì xảy ra:**
- **Lưu** khóa API và tên khu vực vào bộ nhớ cục bộ để sử dụng trong tương lai
- **Hiển thị** chỉ báo tải để thông báo cho người dùng rằng dữ liệu đang được lấy
- **Xóa** bất kỳ thông báo lỗi nào trước đó khỏi màn hình
- **Hiển thị** nút xóa để người dùng đặt lại cài đặt sau này
- **Khởi tạo** cuộc gọi API để lấy dữ liệu sử dụng carbon thực

Hàm này tạo ra trải nghiệm người dùng liền mạch bằng cách quản lý cả việc lưu trữ dữ liệu và cập nhật giao diện người dùng trong một hành động phối hợp.

## Hiển thị dữ liệu sử dụng carbon

Bây giờ chúng ta sẽ kết nối tiện ích của bạn với các nguồn dữ liệu bên ngoài thông qua API. Điều này biến tiện ích của bạn từ một công cụ độc lập thành một thứ có thể truy cập thông tin thời gian thực từ khắp nơi trên internet.

**Hiểu về API**

[API](https://www.webopedia.com/TERM/A/API.html) là cách các ứng dụng khác nhau giao tiếp với nhau. Hãy nghĩ về chúng như hệ thống điện báo kết nối các thành phố xa xôi vào thế kỷ 19 - các nhà điều hành sẽ gửi yêu cầu đến các trạm xa và nhận phản hồi với thông tin được yêu cầu. Mỗi lần bạn kiểm tra mạng xã hội, hỏi trợ lý giọng nói một câu hỏi, hoặc sử dụng ứng dụng giao hàng, API đang tạo điều kiện cho các trao đổi dữ liệu này.

**Các khái niệm chính về REST API:**
- **REST** là viết tắt của 'Representational State Transfer'
- **Sử dụng** các phương thức HTTP tiêu chuẩn (GET, POST, PUT, DELETE) để tương tác với dữ liệu
- **Trả về** dữ liệu ở các định dạng dự đoán được, thường là JSON
- **Cung cấp** các điểm cuối URL nhất quán cho các loại yêu cầu khác nhau

✅ [API CO2 Signal](https://www.co2signal.com/) mà chúng ta sẽ sử dụng cung cấp dữ liệu cường độ carbon thời gian thực từ các lưới điện trên toàn thế giới. Điều này giúp người dùng hiểu tác động môi trường của việc sử dụng điện của họ!

> 💡 **Hiểu về JavaScript không đồng bộ**: Từ khóa [`async`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/async_function) cho phép mã của bạn xử lý nhiều hoạt động đồng thời. Khi bạn yêu cầu dữ liệu từ máy chủ, bạn không muốn toàn bộ tiện ích của mình bị đóng băng - điều đó giống như kiểm soát không lưu dừng tất cả các hoạt động trong khi chờ một máy bay phản hồi.
>
> **Lợi ích chính:**
> - **Duy trì** sự phản hồi của tiện ích trong khi dữ liệu đang tải
> - **Cho phép** mã khác tiếp tục thực thi trong khi yêu cầu mạng
> - **Cải thiện** khả năng đọc mã so với các mẫu callback truyền thống
> - **Cho phép** xử lý lỗi một cách mượt mà cho các vấn đề mạng

Đây là một video nhanh về `async`:

[![Async và Await để quản lý promises](https://img.youtube.com/vi/YwmlRkrxvkk/0.jpg)](https://youtube.com/watch?v=YwmlRkrxvkk "Async và Await để quản lý promises")

> 🎥 Nhấp vào hình ảnh trên để xem video về async/await.

Tạo hàm để lấy và hiển thị dữ liệu sử dụng carbon:

```javascript
// Modern fetch API approach (no external dependencies needed)
async function displayCarbonUsage(apiKey, region) {
	try {
		// Fetch carbon intensity data from CO2 Signal API
		const response = await fetch('https://api.co2signal.com/v1/latest', {
			method: 'GET',
			headers: {
				'auth-token': apiKey,
				'Content-Type': 'application/json'
			},
			// Add query parameters for the specific region
			...new URLSearchParams({ countryCode: region }) && {
				url: `https://api.co2signal.com/v1/latest?countryCode=${region}`
			}
		});

		// Check if the API request was successful
		if (!response.ok) {
			throw new Error(`API request failed: ${response.status}`);
		}

		const data = await response.json();
		const carbonData = data.data;

		// Calculate rounded carbon intensity value
		const carbonIntensity = Math.round(carbonData.carbonIntensity);

		// Update the user interface with fetched data
		loading.style.display = 'none';
		form.style.display = 'none';
		myregion.textContent = region.toUpperCase();
		usage.textContent = `${carbonIntensity} grams (grams CO₂ emitted per kilowatt hour)`;
		fossilfuel.textContent = `${carbonData.fossilFuelPercentage.toFixed(2)}% (percentage of fossil fuels used to generate electricity)`;
		results.style.display = 'block';

		// TODO: calculateColor(carbonIntensity) - implement in next lesson

	} catch (error) {
		console.error('Error fetching carbon data:', error);
		
		// Show user-friendly error message
		loading.style.display = 'none';
		results.style.display = 'none';
		errors.textContent = 'Sorry, we couldn\'t fetch data for that region. Please check your API key and region code.';
	}
}
```

**Phân tích những gì xảy ra ở đây:**
- **Sử dụng** API `fetch()` hiện đại thay vì các thư viện bên ngoài như Axios để có mã sạch hơn, không phụ thuộc
- **Thực hiện** kiểm tra lỗi đúng cách với `response.ok` để bắt lỗi API sớm
- **Xử lý** các hoạt động không đồng bộ với `async/await` để có luồng mã dễ đọc hơn
- **Xác thực** với API CO2 Signal bằng cách sử dụng header `auth-token`
- **Phân tích** dữ liệu JSON phản hồi và trích xuất thông tin cường độ carbon
- **Cập nhật** nhiều phần tử giao diện người dùng với dữ liệu môi trường được định dạng
- **Cung cấp** thông báo lỗi thân thiện với người dùng khi các cuộc gọi API thất bại

**Các khái niệm JavaScript hiện đại được minh họa:**
- **Template literals** với cú pháp `${}` để định dạng chuỗi sạch
- **Xử lý lỗi** với các khối try/catch để có ứng dụng mạnh mẽ
- **Mẫu async/await** để xử lý yêu cầu mạng một cách mượt mà
- **Phân rã đối tượng** để trích xuất dữ liệu cụ thể từ phản hồi API
- **Phương pháp chaining** cho nhiều thao tác DOM

✅ Hàm này minh họa một số khái niệm quan trọng trong phát triển web - giao tiếp với máy chủ bên ngoài, xử lý xác thực, xử lý dữ liệu, cập nhật giao diện, và quản lý lỗi một cách mượt mà. Đây là những kỹ năng cơ bản mà các nhà phát triển chuyên nghiệp sử dụng thường xuyên.

🎉 **Những gì bạn đã hoàn thành:** Bạn đã tạo một tiện ích trình duyệt:
- **Kết nối** với internet và lấy dữ liệu môi trường thực
- **Lưu trữ** cài đặt người dùng giữa các phiên
- **Xử lý** lỗi một cách mượt mà thay vì bị treo
- **Cung cấp** trải nghiệm người dùng mượt mà, chuyên nghiệp

Kiểm tra công việc của bạn bằng cách chạy `npm run build` và làm mới tiện ích của bạn trong trình duyệt. Bây giờ bạn đã có một công cụ theo dõi dấu chân carbon hoạt động. Bài học tiếp theo sẽ thêm chức năng biểu tượng động để hoàn thiện tiện ích.

---

## Thử thách GitHub Copilot Agent 🚀

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Nâng cấp tiện ích trình duyệt bằng cách thêm các cải tiến xử lý lỗi và các tính năng trải nghiệm người dùng. Thử thách này sẽ giúp bạn thực hành làm việc với API, bộ nhớ cục bộ và thao tác DOM bằng các mẫu JavaScript hiện đại.

**Yêu cầu:** Tạo phiên bản nâng cấp của hàm displayCarbonUsage bao gồm: 1) Cơ chế thử lại cho các cuộc gọi API thất bại với backoff theo cấp số nhân, 2) Xác thực đầu vào cho mã khu vực trước khi thực hiện cuộc gọi API, 3) Hoạt ảnh tải với các chỉ báo tiến độ, 4) Bộ nhớ đệm các phản hồi API trong localStorage với dấu thời gian hết hạn (bộ nhớ đệm trong 30 phút), và 5) Một tính năng để hiển thị dữ liệu lịch sử từ các cuộc gọi API trước đó. Cũng thêm các bình luận JSDoc kiểu TypeScript để tài liệu hóa tất cả các tham số hàm và kiểu trả về.

Tìm hiểu thêm về [chế độ agent](https://code.visualstudio.com/blogs/2025/02/24/introducing-copilot-agent-mode) tại đây.

## 🚀 Thử thách

Mở rộng hiểu biết của bạn về API bằng cách khám phá sự phong phú của các API trình duyệt có sẵn cho phát triển web. Chọn một trong các API trình duyệt này và xây dựng một minh họa nhỏ:

- [Geolocation API](https://developer.mozilla.org/docs/Web/API/Geolocation_API) - Lấy vị trí hiện tại của người dùng
- [Notification API](https://developer.mozilla.org/docs/Web/API/Notifications_API) - Gửi thông báo trên máy tính
- [HTML Drag and Drop API](https://developer.mozilla.org/docs/Web/API/HTML_Drag_and_Drop_API) - Tạo giao diện kéo thả tương tác
- [Web Storage API](https://developer.mozilla.org/docs/Web/API/Web_Storage_API) - Kỹ thuật lưu trữ cục bộ nâng cao
- [Fetch API](https://developer.mozilla.org/docs/Web/API/Fetch_API) - Thay thế hiện đại cho XMLHttpRequest

**Câu hỏi nghiên cứu cần xem xét:**
- API này giải quyết vấn đề thực tế nào?
- API xử lý lỗi và các trường hợp ngoại lệ như thế nào?
- Những cân nhắc về bảo mật nào tồn tại khi sử dụng API này?
- API này được hỗ trợ rộng rãi như thế nào trên các trình duyệt khác nhau?

Sau khi nghiên cứu, xác định những đặc điểm nào làm cho một API thân thiện với nhà phát triển và đáng tin cậy.

## Câu hỏi sau bài giảng

[Câu hỏi sau bài giảng](https://ff-quizzes.netlify.app/web/quiz/26)

## Ôn tập & Tự học
Bạn đã học về LocalStorage và API trong bài học này, cả hai đều rất hữu ích cho nhà phát triển web chuyên nghiệp. Bạn có thể nghĩ về cách hai điều này hoạt động cùng nhau không? Hãy suy nghĩ về cách bạn sẽ thiết kế một trang web để lưu trữ các mục được sử dụng bởi một API.

## Bài tập

[Chọn một API](assignment.md)

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, khuyến nghị sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.