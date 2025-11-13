<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "46d665af66e51524598af34a42b9b663",
  "translation_date": "2025-10-24T13:36:09+00:00",
  "source_file": "9-chat-project/README.md",
  "language_code": "vi"
}
-->

[🏠 Trang chủ](../README.md) | [📖 Mục lục](../README.md#-các-bài-học)

---
# Xây dựng Trợ lý Chat với AI

Bạn còn nhớ trong Star Trek, khi phi hành đoàn trò chuyện với máy tính của tàu, hỏi những câu hỏi phức tạp và nhận được câu trả lời sâu sắc không? Điều tưởng chừng như khoa học viễn tưởng vào những năm 1960 giờ đây là điều bạn có thể xây dựng bằng các công nghệ web mà bạn đã biết.

Trong bài học này, chúng ta sẽ tạo một trợ lý chat AI sử dụng HTML, CSS, JavaScript và một chút tích hợp backend. Bạn sẽ khám phá cách các kỹ năng mà bạn đã học có thể kết nối với các dịch vụ AI mạnh mẽ, có khả năng hiểu ngữ cảnh và tạo ra các câu trả lời ý nghĩa.

Hãy nghĩ về AI như việc có quyền truy cập vào một thư viện khổng lồ, không chỉ tìm kiếm thông tin mà còn tổng hợp nó thành các câu trả lời mạch lạc, phù hợp với câu hỏi cụ thể của bạn. Thay vì phải tìm kiếm qua hàng ngàn trang, bạn sẽ nhận được các câu trả lời trực tiếp và có ngữ cảnh.

Việc tích hợp này diễn ra thông qua các công nghệ web quen thuộc làm việc cùng nhau. HTML tạo giao diện chat, CSS xử lý thiết kế hình ảnh, JavaScript quản lý tương tác người dùng, và một API backend kết nối mọi thứ với các dịch vụ AI. Nó giống như cách các phần khác nhau của một dàn nhạc phối hợp để tạo nên một bản giao hưởng.

Chúng ta đang xây dựng một cầu nối giữa giao tiếp tự nhiên của con người và xử lý máy móc. Bạn sẽ học cả cách triển khai kỹ thuật tích hợp dịch vụ AI và các mẫu thiết kế giúp tương tác trở nên trực quan.

Kết thúc bài học này, việc tích hợp AI sẽ không còn là một quá trình bí ẩn mà giống như một API khác mà bạn có thể làm việc cùng. Bạn sẽ hiểu các mẫu cơ bản vận hành các ứng dụng như ChatGPT và Claude, sử dụng các nguyên tắc phát triển web mà bạn đã học.

Dưới đây là hình ảnh dự án hoàn chỉnh của bạn:

![Giao diện ứng dụng chat hiển thị cuộc trò chuyện giữa người dùng và trợ lý AI](../../../translated_images/screenshot.0a1ee0d123df681b4501eb53ffb267519fcc20aa653eabecef1e7561ddfb1cab.vi.png)

## Hiểu về AI: Từ Bí Ẩn đến Thành Thạo

Trước khi đi vào mã, hãy hiểu rõ chúng ta đang làm việc với cái gì. Nếu bạn đã sử dụng API trước đây, bạn sẽ biết mẫu cơ bản: gửi một yêu cầu, nhận một phản hồi.

API AI tuân theo cấu trúc tương tự, nhưng thay vì truy xuất dữ liệu đã lưu trữ từ cơ sở dữ liệu, chúng tạo ra các phản hồi mới dựa trên các mẫu đã học từ lượng lớn văn bản. Hãy nghĩ về nó như sự khác biệt giữa hệ thống danh mục thư viện và một thủ thư thông thạo có thể tổng hợp thông tin từ nhiều nguồn.

### "AI Tạo Sinh" Thực Sự Là Gì?

Hãy tưởng tượng cách viên đá Rosetta giúp các học giả hiểu chữ tượng hình Ai Cập bằng cách tìm các mẫu giữa ngôn ngữ đã biết và chưa biết. Các mô hình AI hoạt động tương tự – chúng tìm các mẫu trong lượng lớn văn bản để hiểu cách ngôn ngữ hoạt động, sau đó sử dụng các mẫu đó để tạo ra các phản hồi phù hợp với các câu hỏi mới.

**Hãy để tôi giải thích bằng một so sánh đơn giản:**
- **Cơ sở dữ liệu truyền thống**: Giống như yêu cầu giấy khai sinh của bạn – bạn nhận được cùng một tài liệu mỗi lần
- **Công cụ tìm kiếm**: Giống như yêu cầu thủ thư tìm sách về mèo – họ chỉ cho bạn những gì có sẵn
- **AI tạo sinh**: Giống như hỏi một người bạn thông thạo về mèo – họ kể cho bạn những điều thú vị bằng lời của họ, phù hợp với những gì bạn muốn biết

```mermaid
graph LR
    A[Your Question] --> B[AI Model]
    B --> C[Pattern Recognition]
    C --> D[Content Generation]
    D --> E[Contextual Response]
    
    F[Training Data<br/>Books, Articles, Web] --> B
```

### Cách Mô Hình AI Học (Phiên Bản Đơn Giản)

Các mô hình AI học thông qua việc tiếp xúc với các tập dữ liệu khổng lồ chứa văn bản từ sách, bài báo và các cuộc trò chuyện. Thông qua quá trình này, chúng xác định các mẫu trong:
- Cách suy nghĩ được cấu trúc trong giao tiếp bằng văn bản
- Những từ nào thường xuất hiện cùng nhau
- Cách các cuộc trò chuyện thường diễn ra
- Sự khác biệt ngữ cảnh giữa giao tiếp trang trọng và không trang trọng

**Nó giống như cách các nhà khảo cổ giải mã ngôn ngữ cổ**: họ phân tích hàng ngàn ví dụ để hiểu ngữ pháp, từ vựng và ngữ cảnh văn hóa, cuối cùng có thể diễn giải các văn bản mới bằng cách sử dụng các mẫu đã học.

### Tại Sao Lại Là Mô Hình GitHub?

Chúng ta sử dụng Mô Hình GitHub vì một lý do thực tế – nó cung cấp cho chúng ta quyền truy cập vào AI cấp doanh nghiệp mà không cần phải thiết lập cơ sở hạ tầng AI của riêng mình (tin tôi đi, bạn không muốn làm điều đó ngay bây giờ!). Hãy nghĩ về nó như sử dụng API thời tiết thay vì cố dự đoán thời tiết bằng cách thiết lập các trạm thời tiết khắp nơi.

Nó cơ bản là "AI dưới dạng dịch vụ," và phần hay nhất? Nó miễn phí để bắt đầu, vì vậy bạn có thể thử nghiệm mà không lo lắng về việc phát sinh chi phí lớn.

```mermaid
graph LR
    A[Frontend Chat UI] --> B[Your Backend API]
    B --> C[GitHub Models API]
    C --> D[AI Model Processing]
    D --> C
    C --> B
    B --> A
```

Chúng ta sẽ sử dụng Mô Hình GitHub cho tích hợp backend, cung cấp quyền truy cập vào các khả năng AI chuyên nghiệp thông qua giao diện thân thiện với nhà phát triển. [GitHub Models Playground](https://github.com/marketplace/models/azure-openai/gpt-4o-mini/playground) là môi trường thử nghiệm nơi bạn có thể thử nghiệm các mô hình AI khác nhau và hiểu khả năng của chúng trước khi triển khai vào mã.

![Giao diện GitHub Models AI Playground với khu vực chọn mô hình và thử nghiệm](../../../translated_images/playground.d2b927122224ff8ff4028fc842176e353c339147d8925455f36c92fb1655c477.vi.png)

**Dưới đây là những gì làm cho playground trở nên hữu ích:**
- **Thử nghiệm** các mô hình AI khác nhau như GPT-4o-mini, Claude và các mô hình khác (tất cả đều miễn phí!)
- **Kiểm tra** ý tưởng và các câu lệnh của bạn trước khi viết mã
- **Nhận** các đoạn mã sẵn sàng sử dụng bằng ngôn ngữ lập trình yêu thích của bạn
- **Điều chỉnh** các cài đặt như mức độ sáng tạo và độ dài phản hồi để xem chúng ảnh hưởng như thế nào đến kết quả

Sau khi bạn thử nghiệm một chút, chỉ cần nhấp vào tab "Code" và chọn ngôn ngữ lập trình của bạn để nhận mã triển khai mà bạn cần.

![Lựa chọn playground hiển thị các tùy chọn tạo mã cho các ngôn ngữ lập trình khác nhau](../../../translated_images/playground-choice.1d23ba7d407f47584c9f446c77f0bcf70cae794cc9c8d7849a3cca4a3693e6c4.vi.png)

## Thiết Lập Tích Hợp Backend Python

Bây giờ hãy triển khai tích hợp AI bằng Python. Python rất tuyệt vời cho các ứng dụng AI vì cú pháp đơn giản và các thư viện mạnh mẽ. Chúng ta sẽ bắt đầu với mã từ playground của GitHub Models và sau đó tái cấu trúc nó thành một hàm có thể tái sử dụng, sẵn sàng cho sản xuất.

### Hiểu Triển Khai Cơ Bản

Khi bạn lấy mã Python từ playground, bạn sẽ nhận được thứ gì đó trông như thế này. Đừng lo nếu ban đầu nó có vẻ nhiều – hãy cùng phân tích từng phần:

```python
"""Run this model in Python

> pip install openai
"""
import os
from openai import OpenAI

# To authenticate with the model you will need to generate a personal access token (PAT) in your GitHub settings. 
# Create your PAT token by following instructions here: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
client = OpenAI(
    base_url="https://models.github.ai/inference",
    api_key=os.environ["GITHUB_TOKEN"],
)

```python
response = client.chat.completions.create(
    messages=[
        {
            "role": "system",
            "content": "",
        },
        {
            "role": "user",
            "content": "What is the capital of France?",
        }
    ],
    model="openai/gpt-4o-mini",
    temperature=1,
    max_tokens=4096,
    top_p=1
)

print(response.choices[0].message.content)
```

**Dưới đây là những gì đang diễn ra trong mã này:**
- **Chúng ta nhập** các công cụ cần thiết: `os` để đọc các biến môi trường và `OpenAI` để giao tiếp với AI
- **Chúng ta thiết lập** client OpenAI để trỏ đến máy chủ AI của GitHub thay vì OpenAI trực tiếp
- **Chúng ta xác thực** bằng một token GitHub đặc biệt (sẽ nói thêm về điều này sau!)
- **Chúng ta cấu trúc** cuộc trò chuyện với các "vai trò" khác nhau – hãy nghĩ về nó như thiết lập bối cảnh cho một vở kịch
- **Chúng ta gửi** yêu cầu đến AI với một số tham số tinh chỉnh
- **Chúng ta trích xuất** văn bản phản hồi thực tế từ tất cả dữ liệu trả về

### Hiểu Vai Trò Tin Nhắn: Khung Hội Thoại AI

Các cuộc hội thoại AI sử dụng một cấu trúc cụ thể với các "vai trò" khác nhau phục vụ các mục đích riêng biệt:

```python
messages=[
    {
        "role": "system",
        "content": "You are a helpful assistant who explains things simply."
    },
    {
        "role": "user", 
        "content": "What is machine learning?"
    }
]
```

**Hãy nghĩ về nó như đạo diễn một vở kịch:**
- **Vai trò hệ thống**: Giống như chỉ dẫn sân khấu cho diễn viên – nó nói cho AI cách hành xử, tính cách và cách phản hồi
- **Vai trò người dùng**: Câu hỏi hoặc tin nhắn thực tế từ người sử dụng ứng dụng của bạn
- **Vai trò trợ lý**: Phản hồi của AI (bạn không gửi cái này, nhưng nó xuất hiện trong lịch sử hội thoại)

**Ví dụ thực tế**: Hãy tưởng tượng bạn giới thiệu một người bạn với ai đó tại một bữa tiệc:
- **Tin nhắn hệ thống**: "Đây là bạn tôi Sarah, cô ấy là bác sĩ rất giỏi giải thích các khái niệm y học một cách đơn giản"
- **Tin nhắn người dùng**: "Bạn có thể giải thích cách hoạt động của vắc-xin không?"
- **Phản hồi của trợ lý**: Sarah trả lời như một bác sĩ thân thiện, không phải như một luật sư hay đầu bếp

### Hiểu Các Tham Số AI: Tinh Chỉnh Hành Vi Phản Hồi

Các tham số số trong các cuộc gọi API AI kiểm soát cách mô hình tạo ra các phản hồi. Những cài đặt này cho phép bạn điều chỉnh hành vi của AI cho các trường hợp sử dụng khác nhau:

#### Temperature (0.0 đến 2.0): Núm Điều Chỉnh Sáng Tạo

**Nó làm gì**: Kiểm soát mức độ sáng tạo hoặc dự đoán của các phản hồi AI.

**Hãy nghĩ về nó như mức độ ngẫu hứng của một nhạc sĩ jazz:**
- **Temperature = 0.1**: Chơi cùng một giai điệu mỗi lần (rất dự đoán)
- **Temperature = 0.7**: Thêm một số biến thể tinh tế trong khi vẫn dễ nhận ra (sáng tạo cân bằng)
- **Temperature = 1.5**: Jazz thử nghiệm hoàn toàn với những bước ngoặt bất ngờ (rất không dự đoán)

```python
# Very predictable responses (good for factual questions)
response = client.chat.completions.create(
    messages=[{"role": "user", "content": "What is 2+2?"}],
    temperature=0.1  # Will almost always say "4"
)

# Creative responses (good for brainstorming)
response = client.chat.completions.create(
    messages=[{"role": "user", "content": "Write a creative story opening"}],
    temperature=1.2  # Will generate unique, unexpected stories
)
```

#### Max Tokens (1 đến 4096+): Bộ Điều Khiển Độ Dài Phản Hồi

**Nó làm gì**: Đặt giới hạn về độ dài phản hồi của AI.

**Hãy nghĩ về token như tương đương với từ** (khoảng 1 token = 0.75 từ trong tiếng Anh):
- **max_tokens=50**: Ngắn gọn và súc tích (như một tin nhắn văn bản)
- **max_tokens=500**: Một đoạn văn hoặc hai đoạn
- **max_tokens=2000**: Một giải thích chi tiết với các ví dụ

```python
# Short, concise answers
response = client.chat.completions.create(
    messages=[{"role": "user", "content": "Explain JavaScript"}],
    max_tokens=100  # Forces a brief explanation
)

# Detailed, comprehensive answers  
response = client.chat.completions.create(
    messages=[{"role": "user", "content": "Explain JavaScript"}],
    max_tokens=1500  # Allows for detailed explanations with examples
)
```

#### Top_p (0.0 đến 1.0): Tham Số Tập Trung

**Nó làm gì**: Kiểm soát mức độ tập trung của AI vào các phản hồi có khả năng cao nhất.

**Hãy tưởng tượng AI có một vốn từ vựng khổng lồ, được xếp hạng theo mức độ khả năng của từng từ:**
- **top_p=0.1**: Chỉ xem xét 10% từ có khả năng cao nhất (rất tập trung)
- **top_p=0.9**: Xem xét 90% từ có khả năng (sáng tạo hơn)
- **top_p=1.0**: Xem xét mọi thứ (đa dạng tối đa)

**Ví dụ**: Nếu bạn hỏi "Bầu trời thường..."
- **Top_p thấp**: Gần như chắc chắn nói "xanh"
- **Top_p cao**: Có thể nói "xanh", "nhiều mây", "rộng lớn", "thay đổi", "đẹp", v.v.

### Kết Hợp Tất Cả: Kết Hợp Tham Số cho Các Trường Hợp Sử Dụng Khác Nhau

```python
# For factual, consistent answers (like a documentation bot)
factual_params = {
    "temperature": 0.2,
    "max_tokens": 300,
    "top_p": 0.3
}

# For creative writing assistance
creative_params = {
    "temperature": 1.1,
    "max_tokens": 1000,
    "top_p": 0.9
}

# For conversational, helpful responses (balanced)
conversational_params = {
    "temperature": 0.7,
    "max_tokens": 500,
    "top_p": 0.8
}
```

**Hiểu tại sao các tham số này quan trọng**: Các ứng dụng khác nhau cần các loại phản hồi khác nhau. Một bot dịch vụ khách hàng nên nhất quán và thực tế (nhiệt độ thấp), trong khi một trợ lý viết sáng tạo nên giàu trí tưởng tượng và đa dạng (nhiệt độ cao). Hiểu các tham số này giúp bạn kiểm soát tính cách và phong cách phản hồi của AI.
```

**Here's what's happening in this code:**
- **We import** the tools we need: `os` for reading environment variables and `OpenAI` for talking to the AI
- **We set up** the OpenAI client to point to GitHub's AI servers instead of OpenAI directly
- **We authenticate** using a special GitHub token (more on that in a minute!)
- **We structure** our conversation with different "roles" – think of it like setting the scene for a play
- **We send** our request to the AI with some fine-tuning parameters
- **We extract** the actual response text from all the data that comes back

> 🔐 **Security Note**: Never hardcode API keys in your source code! Always use environment variables to store sensitive credentials like your `GITHUB_TOKEN`.

### Creating a Reusable AI Function

Let's refactor this code into a clean, reusable function that we can easily integrate into our web application:

```python
import asyncio
from openai import AsyncOpenAI

# Use AsyncOpenAI for better performance
client = AsyncOpenAI(
    base_url="https://models.github.ai/inference",
    api_key=os.environ["GITHUB_TOKEN"],
)

async def call_llm_async(prompt: str, system_message: str = "You are a helpful assistant."):
    """
    Sends a prompt to the AI model asynchronously and returns the response.
    
    Args:
        prompt: The user's question or message
        system_message: Instructions that define the AI's behavior and personality
    
    Returns:
        str: The AI's response to the prompt
    """
    try:
        response = await client.chat.completions.create(
            messages=[
                {
                    "role": "system",
                    "content": system_message,
                },
                {
                    "role": "user",
                    "content": prompt,
                }
            ],
            model="openai/gpt-4o-mini",
            temperature=1,
            max_tokens=4096,
            top_p=1
        )
        return response.choices[0].message.content
    except Exception as e:
        logger.error(f"AI API error: {str(e)}")
        return "I'm sorry, I'm having trouble processing your request right now."

# Backward compatibility function for synchronous calls
def call_llm(prompt: str, system_message: str = "You are a helpful assistant."):
    """Synchronous wrapper for async AI calls."""
    return asyncio.run(call_llm_async(prompt, system_message))
```

**Hiểu hàm cải tiến này:**
- **Chấp nhận** hai tham số: câu hỏi của người dùng và một tin nhắn hệ thống tùy chọn
- **Cung cấp** một tin nhắn hệ thống mặc định cho hành vi trợ lý chung
- **Sử dụng** các gợi ý kiểu Python đúng cách để tài liệu hóa mã tốt hơn
- **Bao gồm** một docstring chi tiết giải thích mục đích và tham số của hàm
- **Trả về** chỉ nội dung phản hồi, giúp dễ sử dụng trong API web của chúng ta
- **Duy trì** các tham số mô hình giống nhau để đảm bảo hành vi AI nhất quán

### Phép Màu của Tin Nhắn Hệ Thống: Lập Trình Tính Cách AI

Nếu các tham số kiểm soát cách AI suy nghĩ, thì tin nhắn hệ thống kiểm soát AI nghĩ mình là ai. Đây thực sự là một trong những phần thú vị nhất khi làm việc với AI – bạn đang tạo cho AI một tính cách hoàn chỉnh, mức độ chuyên môn và phong cách giao tiếp.

**Hãy nghĩ về tin nhắn hệ thống như việc chọn diễn viên cho các vai diễn khác nhau**: Thay vì có một trợ lý chung chung, bạn có thể tạo các chuyên gia chuyên biệt cho các tình huống khác nhau. Cần một giáo viên kiên nhẫn? Một đối tác sáng tạo? Một cố vấn kinh doanh nghiêm túc? Chỉ cần thay đổi tin nhắn hệ thống!

#### Tại Sao Tin Nhắn Hệ Thống Lại Mạnh Mẽ

Đây là phần thú vị: Các mô hình AI đã được huấn luyện trên vô số cuộc trò chuyện nơi mọi người đảm nhận các vai trò và mức độ chuyên môn khác nhau. Khi bạn đưa cho AI một vai trò cụ thể, nó giống như bật một công tắc kích hoạt tất cả các mẫu đã học đó.

**Nó giống như diễn xuất theo phương pháp cho AI**: Nói với một diễn viên "bạn là một giáo sư già thông thái" và xem cách họ tự động điều chỉnh tư thế, từ vựng và cách cư xử. AI làm điều gì đó đáng kinh ngạc tương tự với các mẫu ngôn ngữ.

#### Tạo Tin Nhắn Hệ Thống Hiệu Quả: Nghệ Thuật và Khoa Học

**Cấu trúc của một tin nhắn hệ thống tuyệt vời:**
1. **Vai trò/Danh tính**: AI là ai?
2. **Chuyên môn**: AI biết gì?
3. **Phong cách giao tiếp**: AI nói như thế nào?
4. **Hướng dẫn cụ thể**: AI nên tập trung vào điều gì?

```python
# ❌ Vague system prompt
"You are helpful."

# ✅ Detailed, effective system prompt
"You are Dr. Sarah Chen, a senior software engineer with 15 years of experience at major tech companies. You explain programming concepts using real-world analogies and always provide practical examples. You're patient with beginners and enthusiastic about helping them understand complex topics."
```

#### Ví dụ Tin Nhắn Hệ Thống với Ngữ Cảnh

Hãy xem cách các tin nhắn hệ thống khác nhau tạo ra các tính cách AI hoàn toàn khác nhau:

```python
# Example 1: The Patient Teacher
teacher_prompt = """
You are an experienced programming instructor who has taught thousands of students. 
You break down complex concepts into simple steps, use analogies from everyday life, 
and always check if the student understands before moving on. You're encouraging 
and never make students feel bad for not knowing something.
"""

# Example 2: The Creative Collaborator  
creative_prompt = """
You are a creative writing partner who loves brainstorming wild ideas. You're 
enthusiastic, imaginative, and always build on the user's ideas rather than 
replacing them. You ask thought-provoking questions to spark creativity and 
offer unexpected perspectives that make stories more interesting.
"""

# Example 3: The Strategic Business Advisor
business_prompt = """
You are a strategic business consultant with an MBA and 20 years of experience 
helping startups scale. You think in frameworks, provide structured advice, 
and always consider both short-term tactics and long-term strategy. You ask 
probing questions to understand the full business context before giving advice.
"""
```

#### Thấy Tin Nhắn Hệ Thống Hoạt Động

Hãy thử cùng một câu hỏi với các tin nhắn hệ thống khác nhau để thấy sự khác biệt rõ rệt:

**Câu hỏi**: "Làm thế nào để xử lý xác thực người dùng trong ứng dụng web của tôi?"

```python
# With teacher prompt:
teacher_response = call_llm(
    "How do I handle user authentication in my web app?",
    teacher_prompt
)
# Typical response: "Great question! Let's break authentication down into simple steps. 
# Think of it like a nightclub bouncer checking IDs..."

# With business prompt:
business_response = call_llm(
    "How do I handle user authentication in my web app?", 
    business_prompt
)
# Typical response: "From a strategic perspective, authentication is crucial for user 
# trust and regulatory compliance. Let me outline a framework considering security, 
# user experience, and scalability..."
```

#### Kỹ Thuật Tin Nhắn Hệ Thống Nâng Cao

**1. Thiết Lập Ngữ Cảnh**: Cung cấp thông tin nền cho AI
```python
system_prompt = """
You are helping a junior developer who just started their first job at a startup. 
They know basic HTML/CSS/JavaScript but are new to backend development and databases. 
Be encouraging and explain things step-by-step without being condescending.
"""
```

**2. Định Dạng Kết Quả**: Nói cho AI cách cấu trúc phản hồi
```python
system_prompt = """
You are a technical mentor. Always structure your responses as:
1. Quick Answer (1-2 sentences)
2. Detailed Explanation 
3. Code Example
4. Common Pitfalls to Avoid
5. Next Steps for Learning
"""
```

**3. Đặt Ràng Buộc**: Xác định những gì AI không nên làm
```python
system_prompt = """
You are a coding tutor focused on teaching best practices. Never write complete 
solutions for the user - instead, guide them with hints and questions so they 
learn by doing. Always explain the 'why' behind coding decisions.
"""
```

#### Tại Sao Điều Này Quan Trọng cho Trợ Lý Chat của Bạn

Hiểu tin nhắn hệ thống mang lại cho bạn sức mạnh đáng kinh ngạc để tạo các trợ lý AI chuyên biệt:
- **Bot dịch vụ khách hàng**: Hữu ích, kiên nhẫn, hiểu chính sách
- **Gia sư học tập**: Khuyến khích, từng bước, kiểm tra sự hiểu biết
- **Đối tác sáng tạo**: Giàu trí tưởng tượng, xây dựng ý tưởng, hỏi "nếu thì sao?"
- **Chuyên gia kỹ thuật**: Chính xác, chi tiết, chú trọng bảo mật

**Điểm mấu chốt**: Bạn không chỉ gọi một API AI – bạn đang tạo một tính cách AI tùy chỉnh phục vụ trường hợp sử dụng cụ thể của bạn. Đây là điều làm cho các ứng dụng AI hiện đại cảm thấy được tùy chỉnh và hữu ích thay vì chung chung.

## Xây Dựng API Web với FastAPI: Trung Tâm Giao Tiếp AI Hiệu Suất Cao của Bạn

Bây giờ hãy xây dựng backend kết nối frontend của bạn với các dịch vụ AI. Chúng ta sẽ sử dụng FastAPI, một framework Python hiện đại xuất sắc trong việc xây dựng API cho các ứng dụng AI.

FastAPI mang lại nhiều lợi ích cho loại dự án này: hỗ trợ async tích hợp để xử lý các yêu cầu đồng thời, tự động tạo tài liệu API, và hiệu suất tuyệt vời. Máy chủ FastAPI của bạn hoạt động như một trung gian nhận yêu cầu từ frontend, giao tiếp với các dịch vụ AI, và trả về các phản hồi được định dạng.

### Tại Sao FastAPI cho Các Ứng Dụng AI?

Bạn có thể thắc mắc: "Tôi không thể gọi AI trực tiếp từ JavaScript frontend của mình sao?" hoặc "Tại sao FastAPI thay vì Flask hay Django?" Câu hỏi hay! 
**Đây là lý do tại sao FastAPI hoàn hảo cho những gì chúng ta đang xây dựng:**
- **Async mặc định**: Có thể xử lý nhiều yêu cầu AI cùng lúc mà không bị treo
- **Tài liệu tự động**: Truy cập `/docs` và nhận một trang tài liệu API tương tác, đẹp mắt miễn phí
- **Xác thực tích hợp**: Bắt lỗi trước khi chúng gây ra vấn đề
- **Siêu nhanh**: Một trong những framework Python nhanh nhất hiện nay
- **Python hiện đại**: Sử dụng tất cả các tính năng mới nhất và tốt nhất của Python

**Và đây là lý do tại sao chúng ta cần một backend:**

**Bảo mật**: API key của bạn giống như một mật khẩu – nếu bạn đặt nó trong JavaScript frontend, bất kỳ ai xem mã nguồn của trang web đều có thể đánh cắp nó và sử dụng các tín dụng AI của bạn. Backend giữ thông tin nhạy cảm an toàn.

**Giới hạn tốc độ & kiểm soát**: Backend cho phép bạn kiểm soát tần suất người dùng có thể gửi yêu cầu, triển khai xác thực người dùng và thêm ghi nhật ký để theo dõi việc sử dụng.

**Xử lý dữ liệu**: Bạn có thể muốn lưu các cuộc trò chuyện, lọc nội dung không phù hợp hoặc kết hợp nhiều dịch vụ AI. Backend là nơi logic này tồn tại.

**Kiến trúc giống mô hình client-server:**
- **Frontend**: Lớp giao diện người dùng để tương tác
- **Backend API**: Lớp xử lý và định tuyến yêu cầu
- **Dịch vụ AI**: Tính toán bên ngoài và tạo phản hồi
- **Biến môi trường**: Lưu trữ cấu hình và thông tin đăng nhập an toàn

### Hiểu luồng yêu cầu-phản hồi

Hãy theo dõi điều gì xảy ra khi người dùng gửi một tin nhắn:

```mermaid
sequenceDiagram
    participant User as 👤 User
    participant Frontend as 🌐 Frontend
    participant API as 🔧 FastAPI Server
    participant AI as 🤖 AI Service
    
    User->>Frontend: Types "Hello AI!"
    Frontend->>API: POST /hello {"message": "Hello AI!"}
    Note over API: Validates request<br/>Adds system prompt
    API->>AI: Sends formatted request
    AI->>API: Returns AI response
    Note over API: Processes response<br/>Logs conversation
    API->>Frontend: {"response": "Hello! How can I help?"}
    Frontend->>User: Displays AI message
```

**Hiểu từng bước:**
1. **Tương tác người dùng**: Người dùng nhập vào giao diện chat
2. **Xử lý frontend**: JavaScript thu thập đầu vào và định dạng nó dưới dạng JSON
3. **Xác thực API**: FastAPI tự động xác thực yêu cầu bằng các mô hình Pydantic
4. **Tích hợp AI**: Backend thêm ngữ cảnh (hệ thống prompt) và gọi dịch vụ AI
5. **Xử lý phản hồi**: API nhận phản hồi từ AI và có thể chỉnh sửa nếu cần
6. **Hiển thị frontend**: JavaScript hiển thị phản hồi trong giao diện chat

### Hiểu kiến trúc API

```mermaid
sequenceDiagram
    participant Frontend
    participant FastAPI
    participant AI Function
    participant GitHub Models
    
    Frontend->>FastAPI: POST /hello {"message": "Hello AI!"}
    FastAPI->>AI Function: call_llm(message, system_prompt)
    AI Function->>GitHub Models: API request
    GitHub Models->>AI Function: AI response
    AI Function->>FastAPI: response text
    FastAPI->>Frontend: {"response": "Hello! How can I help?"}
```

### Tạo ứng dụng FastAPI

Hãy xây dựng API của chúng ta từng bước. Tạo một tệp có tên `api.py` với mã FastAPI sau:

```python
# api.py
from fastapi import FastAPI, HTTPException
from fastapi.middleware.cors import CORSMiddleware
from pydantic import BaseModel
from llm import call_llm
import logging

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

# Create FastAPI application
app = FastAPI(
    title="AI Chat API",
    description="A high-performance API for AI-powered chat applications",
    version="1.0.0"
)

# Configure CORS
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # Configure appropriately for production
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

# Pydantic models for request/response validation
class ChatMessage(BaseModel):
    message: str

class ChatResponse(BaseModel):
    response: str

@app.get("/")
async def root():
    """Root endpoint providing API information."""
    return {
        "message": "Welcome to the AI Chat API",
        "docs": "/docs",
        "health": "/health"
    }

@app.get("/health")
async def health_check():
    """Health check endpoint."""
    return {"status": "healthy", "service": "ai-chat-api"}

@app.post("/hello", response_model=ChatResponse)
async def chat_endpoint(chat_message: ChatMessage):
    """Main chat endpoint that processes messages and returns AI responses."""
    try:
        # Extract and validate message
        message = chat_message.message.strip()
        if not message:
            raise HTTPException(status_code=400, detail="Message cannot be empty")
        
        logger.info(f"Processing message: {message[:50]}...")
        
        # Call AI service (note: call_llm should be made async for better performance)
        ai_response = await call_llm_async(message, "You are a helpful and friendly assistant.")
        
        logger.info("AI response generated successfully")
        return ChatResponse(response=ai_response)
        
    except HTTPException:
        raise
    except Exception as e:
        logger.error(f"Error processing chat message: {str(e)}")
        raise HTTPException(status_code=500, detail="Internal server error")

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=5000, reload=True)
```

**Hiểu cách triển khai FastAPI:**
- **Nhập** FastAPI để có chức năng framework web hiện đại và Pydantic để xác thực dữ liệu
- **Tạo** tài liệu API tự động (có sẵn tại `/docs` khi server chạy)
- **Kích hoạt** middleware CORS để cho phép yêu cầu từ frontend từ các nguồn khác nhau
- **Định nghĩa** các mô hình Pydantic để xác thực và tài liệu yêu cầu/phản hồi tự động
- **Sử dụng** các endpoint async để cải thiện hiệu suất với các yêu cầu đồng thời
- **Triển khai** mã trạng thái HTTP và xử lý lỗi đúng cách với HTTPException
- **Bao gồm** ghi nhật ký có cấu trúc để giám sát và gỡ lỗi
- **Cung cấp** endpoint kiểm tra sức khỏe để giám sát trạng thái dịch vụ

**Ưu điểm chính của FastAPI so với các framework truyền thống:**
- **Xác thực tự động**: Các mô hình Pydantic đảm bảo tính toàn vẹn dữ liệu trước khi xử lý
- **Tài liệu tương tác**: Truy cập `/docs` để có tài liệu API tự động và có thể kiểm tra
- **An toàn kiểu**: Gợi ý kiểu Python ngăn lỗi runtime và cải thiện chất lượng mã
- **Hỗ trợ async**: Xử lý nhiều yêu cầu AI đồng thời mà không bị chặn
- **Hiệu suất**: Xử lý yêu cầu nhanh hơn đáng kể cho các ứng dụng thời gian thực

### Hiểu CORS: Người bảo vệ an ninh của web

CORS (Cross-Origin Resource Sharing) giống như một nhân viên bảo vệ tại tòa nhà kiểm tra xem khách có được phép vào hay không. Hãy hiểu tại sao điều này quan trọng và ảnh hưởng đến ứng dụng của bạn như thế nào.

#### CORS là gì và tại sao nó tồn tại?

**Vấn đề**: Hãy tưởng tượng nếu bất kỳ trang web nào cũng có thể gửi yêu cầu đến trang web ngân hàng của bạn thay mặt bạn mà không có sự cho phép của bạn. Đó sẽ là một cơn ác mộng về bảo mật! Trình duyệt ngăn điều này theo mặc định thông qua "Chính sách cùng nguồn gốc."

**Chính sách cùng nguồn gốc**: Trình duyệt chỉ cho phép các trang web gửi yêu cầu đến cùng tên miền, cổng và giao thức mà chúng được tải từ đó.

**Ví dụ thực tế**: Nó giống như bảo vệ tòa nhà chung cư – chỉ cư dân (cùng nguồn gốc) mới có thể vào tòa nhà theo mặc định. Nếu bạn muốn cho một người bạn (khác nguồn gốc) vào, bạn cần nói rõ với bảo vệ rằng điều đó là ổn.

#### CORS trong môi trường phát triển

Trong quá trình phát triển, frontend và backend của bạn chạy trên các cổng khác nhau:
- Frontend: `http://localhost:3000` (hoặc file:// nếu mở HTML trực tiếp)
- Backend: `http://localhost:5000`

Chúng được coi là "các nguồn gốc khác nhau" mặc dù chúng ở trên cùng một máy tính!

```python
from fastapi.middleware.cors import CORSMiddleware

app = FastAPI(__name__)
CORS(app)   # This tells browsers: "It's okay for other origins to make requests to this API"
```

**Cấu hình CORS thực hiện trong thực tế:**
- **Thêm** các header HTTP đặc biệt vào phản hồi API để nói với trình duyệt "yêu cầu cross-origin này được phép"
- **Xử lý** các yêu cầu "preflight" (trình duyệt đôi khi kiểm tra quyền trước khi gửi yêu cầu thực tế)
- **Ngăn chặn** lỗi "bị chặn bởi chính sách CORS" đáng sợ trong bảng điều khiển trình duyệt của bạn

#### Bảo mật CORS: Phát triển vs Sản xuất

```python
# 🚨 Development: Allows ALL origins (convenient but insecure)
CORS(app)

# ✅ Production: Only allow your specific frontend domain
CORS(app, origins=["https://yourdomain.com", "https://www.yourdomain.com"])

# 🔒 Advanced: Different origins for different environments
if app.debug:  # Development mode
    CORS(app, origins=["http://localhost:3000", "http://127.0.0.1:3000"])
else:  # Production mode
    CORS(app, origins=["https://yourdomain.com"])
```

**Tại sao điều này quan trọng**: Trong phát triển, `CORS(app)` giống như để cửa trước của bạn mở khóa – tiện lợi nhưng không an toàn. Trong sản xuất, bạn muốn chỉ định chính xác các trang web nào có thể nói chuyện với API của bạn.

#### Các tình huống CORS phổ biến và giải pháp

| Tình huống | Vấn đề | Giải pháp |
|-----------|--------|----------|
| **Phát triển cục bộ** | Frontend không thể truy cập backend | Thêm CORSMiddleware vào FastAPI |
| **GitHub Pages + Heroku** | Frontend đã triển khai không thể truy cập API | Thêm URL GitHub Pages của bạn vào nguồn gốc CORS |
| **Tên miền tùy chỉnh** | Lỗi CORS trong sản xuất | Cập nhật nguồn gốc CORS để khớp với tên miền của bạn |
| **Ứng dụng di động** | Ứng dụng không thể truy cập web API | Thêm tên miền của ứng dụng của bạn hoặc sử dụng `*` một cách cẩn thận |

**Mẹo chuyên nghiệp**: Bạn có thể kiểm tra các header CORS trong Công cụ dành cho nhà phát triển của trình duyệt dưới tab Mạng. Tìm các header như `Access-Control-Allow-Origin` trong phản hồi.

### Xử lý lỗi và xác thực

Lưu ý cách API của chúng ta bao gồm xử lý lỗi đúng cách:

```python
# Validate that we received a message
if not message:
    return jsonify({"error": "Message field is required"}), 400
```

**Nguyên tắc xác thực chính:**
- **Kiểm tra** các trường bắt buộc trước khi xử lý yêu cầu
- **Trả về** thông báo lỗi có ý nghĩa dưới dạng JSON
- **Sử dụng** mã trạng thái HTTP phù hợp (400 cho yêu cầu không hợp lệ)
- **Cung cấp** phản hồi rõ ràng để giúp các nhà phát triển frontend gỡ lỗi vấn đề

## Thiết lập và chạy backend của bạn

Bây giờ chúng ta đã sẵn sàng tích hợp AI và server FastAPI, hãy bắt đầu mọi thứ. Quá trình thiết lập bao gồm cài đặt các phụ thuộc Python, cấu hình biến môi trường và khởi động server phát triển của bạn.

### Thiết lập môi trường Python

Hãy thiết lập môi trường phát triển Python của bạn. Các môi trường ảo giống như cách tiếp cận phân chia của Dự án Manhattan – mỗi dự án có không gian riêng biệt với các công cụ và phụ thuộc cụ thể, ngăn chặn xung đột giữa các dự án khác nhau.

```bash
# Navigate to your backend directory
cd backend

# Create a virtual environment (like creating a clean room for your project)
python -m venv venv

# Activate it (Linux/Mac)
source ./venv/bin/activate

# On Windows, use:
# venv\Scripts\activate

# Install the good stuff
pip install openai fastapi uvicorn python-dotenv
```

**Những gì chúng ta vừa làm:**
- **Tạo** một không gian Python riêng của chúng ta nơi chúng ta có thể cài đặt các gói mà không ảnh hưởng đến bất kỳ thứ gì khác
- **Kích hoạt** nó để terminal của chúng ta biết sử dụng môi trường cụ thể này
- **Cài đặt** các yếu tố cần thiết: OpenAI cho phép kỳ diệu AI, FastAPI cho web API của chúng ta, Uvicorn để thực sự chạy nó, và python-dotenv để quản lý bí mật an toàn

**Giải thích các phụ thuộc chính:**
- **FastAPI**: Framework web hiện đại, nhanh với tài liệu API tự động
- **Uvicorn**: Server ASGI siêu nhanh chạy các ứng dụng FastAPI
- **OpenAI**: Thư viện chính thức cho GitHub Models và tích hợp API OpenAI
- **python-dotenv**: Tải biến môi trường an toàn từ các tệp .env

### Cấu hình môi trường: Giữ bí mật an toàn

Trước khi chúng ta bắt đầu API, chúng ta cần nói về một trong những bài học quan trọng nhất trong phát triển web: cách giữ bí mật thực sự bí mật. Biến môi trường giống như một kho an toàn mà chỉ ứng dụng của bạn có thể truy cập.

#### Biến môi trường là gì?

**Hãy nghĩ về biến môi trường như một hộp ký gửi an toàn** – bạn đặt những thứ có giá trị của mình vào đó, và chỉ bạn (và ứng dụng của bạn) có chìa khóa để lấy nó ra. Thay vì viết thông tin nhạy cảm trực tiếp vào mã của bạn (nơi bất kỳ ai cũng có thể thấy), bạn lưu trữ nó an toàn trong môi trường.

**Sự khác biệt:**
- **Cách sai**: Viết mật khẩu của bạn trên một tờ giấy dán và đặt nó trên màn hình của bạn
- **Cách đúng**: Giữ mật khẩu của bạn trong một trình quản lý mật khẩu an toàn mà chỉ bạn có thể truy cập

#### Tại sao biến môi trường quan trọng

```python
# 🚨 NEVER DO THIS - API key visible to everyone
client = OpenAI(
    api_key="ghp_1234567890abcdef...",  # Anyone can steal this!
    base_url="https://models.github.ai/inference"
)

# ✅ DO THIS - API key stored securely
client = OpenAI(
    api_key=os.environ["GITHUB_TOKEN"],  # Only your app can access this
    base_url="https://models.github.ai/inference"
)
```

**Điều gì xảy ra khi bạn hardcode bí mật:**
1. **Lộ trong kiểm soát phiên bản**: Bất kỳ ai có quyền truy cập vào kho Git của bạn đều thấy API key của bạn
2. **Kho công khai**: Nếu bạn đẩy lên GitHub, key của bạn sẽ hiển thị cho toàn bộ internet
3. **Chia sẻ nhóm**: Các nhà phát triển khác làm việc trên dự án của bạn có quyền truy cập vào API key cá nhân của bạn
4. **Vi phạm bảo mật**: Nếu ai đó đánh cắp API key của bạn, họ có thể sử dụng các tín dụng AI của bạn

#### Thiết lập tệp môi trường của bạn

Tạo một tệp `.env` trong thư mục backend của bạn. Tệp này lưu trữ bí mật của bạn cục bộ:

```bash
# .env file - This should NEVER be committed to Git
GITHUB_TOKEN=your_github_personal_access_token_here
FASTAPI_DEBUG=True
ENVIRONMENT=development
```

**Hiểu tệp .env:**
- **Một bí mật mỗi dòng** theo định dạng `KEY=value`
- **Không có khoảng trắng** xung quanh dấu bằng
- **Không cần dấu ngoặc kép** xung quanh giá trị (thường là vậy)
- **Nhận xét** bắt đầu bằng `#`

#### Tạo GitHub Personal Access Token của bạn

Token GitHub của bạn giống như một mật khẩu đặc biệt cho phép ứng dụng của bạn sử dụng các dịch vụ AI của GitHub:

**Các bước tạo token:**
1. **Đi tới GitHub Settings** → Developer settings → Personal access tokens → Tokens (classic)
2. **Nhấp vào "Generate new token (classic)"**
3. **Đặt thời hạn** (30 ngày để thử nghiệm, lâu hơn cho sản xuất)
4. **Chọn phạm vi**: Chọn "repo" và bất kỳ quyền nào khác bạn cần
5. **Tạo token** và sao chép ngay lập tức (bạn không thể xem lại nó!)
6. **Dán vào tệp .env của bạn**

```bash
# Example of what your token looks like (this is fake!)
GITHUB_TOKEN=ghp_1A2B3C4D5E6F7G8H9I0J1K2L3M4N5O6P7Q8R
```

#### Tải biến môi trường trong Python

```python
import os
from dotenv import load_dotenv

# Load environment variables from .env file
load_dotenv()

# Now you can access them securely
api_key = os.environ.get("GITHUB_TOKEN")
if not api_key:
    raise ValueError("GITHUB_TOKEN not found in environment variables!")

client = OpenAI(
    api_key=api_key,
    base_url="https://models.github.ai/inference"
)
```

**Mã này làm gì:**
- **Tải** tệp .env của bạn và làm cho các biến có sẵn cho Python
- **Kiểm tra** nếu token cần thiết tồn tại (xử lý lỗi tốt!)
- **Gây lỗi** rõ ràng nếu token bị thiếu
- **Sử dụng** token một cách an toàn mà không để lộ nó trong mã

#### Bảo mật Git: Tệp .gitignore

Tệp `.gitignore` của bạn nói với Git những tệp nào không bao giờ được theo dõi hoặc tải lên:

```bash
# .gitignore - Add these lines
.env
*.env
.env.local
.env.production
__pycache__/
venv/
.vscode/
```

**Tại sao điều này rất quan trọng**: Một khi bạn thêm `.env` vào `.gitignore`, Git sẽ bỏ qua tệp môi trường của bạn, ngăn bạn vô tình tải lên bí mật của mình lên GitHub.

#### Các môi trường khác nhau, các bí mật khác nhau

Các ứng dụng chuyên nghiệp sử dụng các API key khác nhau cho các môi trường khác nhau:

```bash
# .env.development
GITHUB_TOKEN=your_development_token
DEBUG=True

# .env.production  
GITHUB_TOKEN=your_production_token
DEBUG=False
```

**Tại sao điều này quan trọng**: Bạn không muốn các thử nghiệm phát triển của mình ảnh hưởng đến hạn mức sử dụng AI trong sản xuất, và bạn muốn các mức độ bảo mật khác nhau cho các môi trường khác nhau.

### Khởi động server phát triển của bạn: Đưa FastAPI của bạn vào hoạt động

Bây giờ là khoảnh khắc thú vị – khởi động server phát triển FastAPI của bạn và thấy tích hợp AI của bạn hoạt động! FastAPI sử dụng Uvicorn, một server ASGI siêu nhanh được thiết kế đặc biệt cho các ứng dụng Python async.

#### Hiểu quy trình khởi động server FastAPI

```bash
# Method 1: Direct Python execution (includes auto-reload)
python api.py

# Method 2: Using Uvicorn directly (more control)
uvicorn api:app --host 0.0.0.0 --port 5000 --reload
```

Khi bạn chạy lệnh này, đây là những gì xảy ra phía sau:

**1. Python tải ứng dụng FastAPI của bạn**:
- Nhập tất cả các thư viện cần thiết (FastAPI, Pydantic, OpenAI, v.v.)
- Tải biến môi trường từ tệp `.env` của bạn
- Tạo instance ứng dụng FastAPI với tài liệu tự động

**2. Uvicorn cấu hình server ASGI**:
- Kết nối với cổng 5000 với khả năng xử lý yêu cầu async
- Thiết lập định tuyến yêu cầu với xác thực tự động
- Kích hoạt tải lại nóng cho phát triển (khởi động lại khi thay đổi tệp)
- Tạo tài liệu API tương tác

**3. Server bắt đầu lắng nghe**:
- Terminal của bạn hiển thị: `INFO: Uvicorn running on http://0.0.0.0:5000`
- Server có thể xử lý nhiều yêu cầu AI đồng thời
- API của bạn đã sẵn sàng với tài liệu tự động tại `http://localhost:5000/docs`

#### Những gì bạn nên thấy khi mọi thứ hoạt động

```bash
$ python api.py
INFO:     Will watch for changes in these directories: ['/your/project/path']
INFO:     Uvicorn running on http://0.0.0.0:5000 (Press CTRL+C to quit)
INFO:     Started reloader process [12345] using WatchFiles
INFO:     Started server process [12346]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

**Hiểu đầu ra của FastAPI:**
- **Sẽ theo dõi thay đổi**: Tự động tải lại được kích hoạt cho phát triển
- **Uvicorn đang chạy**: Server ASGI hiệu suất cao đang hoạt động
- **Quá trình tải lại đã bắt đầu**: Trình theo dõi tệp để khởi động lại tự động
- **Khởi động ứng dụng hoàn tất**: Ứng dụng FastAPI được khởi tạo thành công
- **Tài liệu tương tác có sẵn**: Truy cập `/docs` để có tài liệu API tự động

#### Kiểm tra FastAPI của bạn: Nhiều cách mạnh mẽ

FastAPI cung cấp một số cách tiện lợi để kiểm tra API của bạn, bao gồm tài liệu tương tác tự động:

**Phương pháp 1: Tài liệu API tương tác (Khuyến nghị)**
1. Mở trình duyệt của bạn và truy cập `http://localhost:5000/docs`
2. Bạn sẽ thấy Swagger UI với tất cả các endpoint của bạn được tài liệu hóa
3. Nhấp vào `/hello` → "Try it out" → Nhập một tin nhắn thử nghiệm → "Execute"
4. Xem phản hồi trực tiếp trong trình duyệt với định dạng đúng

**Phương pháp 2: Kiểm tra trình duyệt cơ bản**
1. Truy cập `http://localhost:5000` cho endpoint gốc
2. Truy cập `http://localhost:5000/health` để kiểm tra sức khỏe server
3. Điều này xác nhận server FastAPI của bạn đang chạy đúng cách

**Phương pháp 2: Kiểm tra dòng lệnh (Nâng cao)**
```bash
# Test with curl (if available)
curl -X POST http://localhost:5000/hello \
  -H "Content-Type: application/json" \
  -d '{"message": "Hello AI!"}'

# Expected response:
# {"response": "Hello! I'm your AI assistant. How can I help you today?"}
```

**Phương pháp 3: Script kiểm tra Python**
```python
# test_api.py - Create this file to test your API
import requests
import json

# Test the API endpoint
url = "http://localhost:5000/hello"
data = {"message": "Tell me a joke about programming"}

response = requests.post(url, json=data)
if response.status_code == 200:
    result = response.json()
    print("AI Response:", result['response'])
else:
    print("Error:", response.status_code, response.text)
```

#### Khắc phục các vấn đề khởi động thường gặp

| Thông báo lỗi | Ý nghĩa | Cách khắc phục |
|---------------|---------|----------------|
| `ModuleNotFoundError: No module named 'fastapi'` | FastAPI chưa được cài đặt | Chạy `pip install fastapi uvicorn` trong môi trường ảo của bạn |
| `ModuleNotFoundError: No module named 'uvicorn'` | Máy chủ ASGI chưa được cài đặt | Chạy `pip install uvicorn` trong môi trường ảo của bạn |
| `KeyError: 'GITHUB_TOKEN'` | Biến môi trường không được tìm thấy | Kiểm tra tệp `.env` và lệnh gọi `load_dotenv()` |
| `Address already in use` | Cổng 5000 đang bận | Dừng các tiến trình khác đang sử dụng cổng 5000 hoặc thay đổi cổng |
| `ValidationError` | Dữ liệu yêu cầu không khớp với mô hình Pydantic | Kiểm tra định dạng yêu cầu của bạn có khớp với schema mong đợi không |
| `HTTPException 422` | Thực thể không thể xử lý | Xác thực yêu cầu thất bại, kiểm tra `/docs` để biết định dạng chính xác |
| `OpenAI API error` | Xác thực dịch vụ AI thất bại | Xác minh token GitHub của bạn đúng và có quyền phù hợp |

#### Các thực hành tốt nhất trong phát triển

**Tự động tải lại**: FastAPI với Uvicorn cung cấp tính năng tự động tải lại khi bạn lưu thay đổi trong các tệp Python. Điều này cho phép bạn chỉnh sửa mã và kiểm tra ngay lập tức mà không cần khởi động lại thủ công.

```python
# Enable hot reloading explicitly
if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000, debug=True)  # debug=True enables hot reload
```

**Ghi nhật ký cho phát triển**: Thêm ghi nhật ký để hiểu điều gì đang xảy ra:

```python
import logging

# Set up logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

@app.route("/hello", methods=["POST"])
def hello():
    data = request.get_json()
    message = data.get("message", "")
    
    logger.info(f"Received message: {message}")
    
    if not message:
        logger.warning("Empty message received")
        return jsonify({"error": "Message field is required"}), 400
    
    try:
        response = call_llm(message, "You are a helpful and friendly assistant.")
        logger.info(f"AI response generated successfully")
        return jsonify({"response": response})
    except Exception as e:
        logger.error(f"AI API error: {str(e)}")
        return jsonify({"error": "AI service temporarily unavailable"}), 500
```

**Tại sao ghi nhật ký hữu ích**: Trong quá trình phát triển, bạn có thể thấy chính xác những yêu cầu nào đang đến, AI phản hồi ra sao, và lỗi xảy ra ở đâu. Điều này giúp việc gỡ lỗi nhanh hơn nhiều.

### Cấu hình cho GitHub Codespaces: Phát triển trên đám mây dễ dàng

GitHub Codespaces giống như có một máy tính phát triển mạnh mẽ trên đám mây mà bạn có thể truy cập từ bất kỳ trình duyệt nào. Nếu bạn đang làm việc trong Codespaces, có một số bước bổ sung để làm cho backend của bạn có thể truy cập được từ frontend.

#### Hiểu về mạng Codespaces

Trong môi trường phát triển cục bộ, mọi thứ chạy trên cùng một máy tính:
- Backend: `http://localhost:5000`
- Frontend: `http://localhost:3000` (hoặc file://)

Trong Codespaces, môi trường phát triển của bạn chạy trên máy chủ của GitHub, vì vậy "localhost" có ý nghĩa khác. GitHub tự động tạo URL công khai cho các dịch vụ của bạn, nhưng bạn cần cấu hình chúng đúng cách.

#### Các bước cấu hình Codespaces

**1. Khởi động máy chủ backend của bạn**:
```bash
cd backend
python api.py
```

Bạn sẽ thấy thông báo khởi động FastAPI/Uvicorn quen thuộc, nhưng lưu ý rằng nó đang chạy bên trong môi trường Codespace.

**2. Cấu hình khả năng hiển thị cổng**:
- Tìm tab "Ports" ở bảng dưới cùng của VS Code
- Tìm cổng 5000 trong danh sách
- Nhấp chuột phải vào cổng 5000
- Chọn "Port Visibility" → "Public"

**Tại sao cần công khai?** Theo mặc định, các cổng Codespace là riêng tư (chỉ bạn có thể truy cập). Việc công khai cho phép frontend của bạn (chạy trong trình duyệt) giao tiếp với backend.

**3. Lấy URL công khai của bạn**:
Sau khi làm cho cổng công khai, bạn sẽ thấy một URL như:
```
https://your-codespace-name-5000.app.github.dev
```

**4. Cập nhật cấu hình frontend của bạn**:
```javascript
// In your frontend app.js, update the BASE_URL:
this.BASE_URL = "https://your-codespace-name-5000.app.github.dev";
```

#### Hiểu về URL Codespace

URL Codespace tuân theo một mẫu dự đoán:
```
https://[codespace-name]-[port].app.github.dev
```

**Phân tích cấu trúc này:**
- `codespace-name`: Một định danh duy nhất cho Codespace của bạn (thường bao gồm tên người dùng của bạn)
- `port`: Số cổng mà dịch vụ của bạn đang chạy (5000 cho ứng dụng FastAPI của chúng ta)
- `app.github.dev`: Miền của GitHub dành cho các ứng dụng Codespace

#### Kiểm tra thiết lập Codespace của bạn

**1. Kiểm tra backend trực tiếp**:
Mở URL công khai của bạn trong một tab trình duyệt mới. Bạn sẽ thấy:
```
Welcome to the AI Chat API. Send POST requests to /hello with JSON payload containing 'message' field.
```

**2. Kiểm tra với công cụ phát triển trình duyệt**:
```javascript
// Open browser console and test your API
fetch('https://your-codespace-name-5000.app.github.dev/hello', {
  method: 'POST',
  headers: {'Content-Type': 'application/json'},
  body: JSON.stringify({message: 'Hello from Codespaces!'})
})
.then(response => response.json())
.then(data => console.log(data));
```

#### Codespaces vs Phát triển cục bộ

| Khía cạnh | Phát triển cục bộ | GitHub Codespaces |
|-----------|-------------------|-------------------|
| **Thời gian thiết lập** | Lâu hơn (cài đặt Python, các phụ thuộc) | Nhanh chóng (môi trường được cấu hình sẵn) |
| **Truy cập URL** | `http://localhost:5000` | `https://xyz-5000.app.github.dev` |
| **Cấu hình cổng** | Tự động | Thủ công (làm cho cổng công khai) |
| **Lưu trữ tệp** | Máy cục bộ | Kho GitHub |
| **Hợp tác** | Khó chia sẻ môi trường | Dễ dàng chia sẻ liên kết Codespace |
| **Phụ thuộc Internet** | Chỉ cho các cuộc gọi API AI | Cần thiết cho mọi thứ |

#### Mẹo phát triển Codespace

**Biến môi trường trong Codespaces**:
Tệp `.env` của bạn hoạt động giống như trong Codespaces, nhưng bạn cũng có thể đặt biến môi trường trực tiếp trong Codespace:

```bash
# Set environment variable for the current session
export GITHUB_TOKEN="your_token_here"

# Or add to your .bashrc for persistence
echo 'export GITHUB_TOKEN="your_token_here"' >> ~/.bashrc
```

**Quản lý cổng**:
- Codespaces tự động phát hiện khi ứng dụng của bạn bắt đầu lắng nghe trên một cổng
- Bạn có thể chuyển tiếp nhiều cổng cùng lúc (hữu ích nếu bạn thêm cơ sở dữ liệu sau này)
- Các cổng vẫn có thể truy cập miễn là Codespace của bạn đang chạy

**Quy trình làm việc phát triển**:
1. Thực hiện thay đổi mã trong VS Code
2. FastAPI tự động tải lại (nhờ chế độ tải lại của Uvicorn)
3. Kiểm tra thay đổi ngay lập tức qua URL công khai
4. Commit và đẩy lên khi sẵn sàng

> 💡 **Mẹo chuyên nghiệp**: Đánh dấu URL backend Codespace của bạn trong quá trình phát triển. Vì tên Codespace ổn định, URL sẽ không thay đổi miễn là bạn sử dụng cùng một Codespace.

## Tạo giao diện trò chuyện frontend: Nơi con người gặp AI

Bây giờ chúng ta sẽ xây dựng giao diện người dùng – phần quyết định cách mọi người tương tác với trợ lý AI của bạn. Giống như thiết kế giao diện ban đầu của iPhone, chúng ta tập trung vào việc làm cho công nghệ phức tạp trở nên trực quan và dễ sử dụng.

### Hiểu về kiến trúc frontend hiện đại

Giao diện trò chuyện của chúng ta sẽ là một ứng dụng "Single Page Application" hay SPA. Thay vì cách tiếp cận cũ nơi mỗi lần nhấp tải một trang mới, ứng dụng của chúng ta cập nhật mượt mà và ngay lập tức:

**Trang web cũ**: Giống như đọc một cuốn sách vật lý – bạn lật sang các trang hoàn toàn mới
**Ứng dụng trò chuyện của chúng ta**: Giống như sử dụng điện thoại – mọi thứ trôi chảy và cập nhật liền mạch

```mermaid
graph TD
    A[User Types Message] --> B[JavaScript Captures Input]
    B --> C[Validate & Format Data]
    C --> D[Send to Backend API]
    D --> E[Display Loading State]
    E --> F[Receive AI Response]
    F --> G[Update Chat Interface]
    G --> H[Ready for Next Message]
```

### Ba trụ cột của phát triển frontend

Mọi ứng dụng frontend – từ các trang web đơn giản đến các ứng dụng phức tạp như Discord hoặc Slack – đều được xây dựng trên ba công nghệ cốt lõi. Hãy nghĩ về chúng như nền tảng của mọi thứ bạn thấy và tương tác trên web:

**HTML (Cấu trúc)**: Đây là nền tảng của bạn
- Quyết định các phần tử tồn tại (nút, vùng nhập văn bản, container)
- Đưa ý nghĩa cho nội dung (đây là tiêu đề, đây là biểu mẫu, v.v.)
- Tạo cấu trúc cơ bản mà mọi thứ khác xây dựng trên đó

**CSS (Trình bày)**: Đây là nhà thiết kế nội thất của bạn
- Làm cho mọi thứ trông đẹp mắt (màu sắc, phông chữ, bố cục)
- Xử lý các kích thước màn hình khác nhau (điện thoại, laptop, máy tính bảng)
- Tạo các hiệu ứng mượt mà và phản hồi hình ảnh

**JavaScript (Hành vi)**: Đây là bộ não của bạn
- Phản hồi những gì người dùng làm (nhấp chuột, nhập liệu, cuộn)
- Giao tiếp với backend và cập nhật trang
- Làm cho mọi thứ tương tác và động

**Hãy nghĩ về nó như thiết kế kiến trúc:**
- **HTML**: Bản thiết kế cấu trúc (xác định không gian và mối quan hệ)
- **CSS**: Thiết kế thẩm mỹ và môi trường (phong cách hình ảnh và trải nghiệm người dùng)
- **JavaScript**: Hệ thống cơ khí (chức năng và tương tác)

### Tại sao kiến trúc JavaScript hiện đại quan trọng

Ứng dụng trò chuyện của chúng ta sẽ sử dụng các mẫu JavaScript hiện đại mà bạn sẽ thấy trong các ứng dụng chuyên nghiệp. Hiểu các khái niệm này sẽ giúp bạn phát triển như một nhà phát triển:

**Kiến trúc dựa trên lớp**: Chúng ta sẽ tổ chức mã của mình thành các lớp, giống như tạo bản thiết kế cho các đối tượng
**Async/Await**: Cách hiện đại để xử lý các hoạt động mất thời gian (như các cuộc gọi API)
**Lập trình dựa trên sự kiện**: Ứng dụng của chúng ta phản hồi các hành động của người dùng (nhấp chuột, nhấn phím) thay vì chạy trong một vòng lặp
**DOM Manipulation**: Cập nhật nội dung trang web một cách động dựa trên tương tác của người dùng và phản hồi API

### Thiết lập cấu trúc dự án

Tạo thư mục frontend với cấu trúc tổ chức này:

```text
frontend/
├── index.html      # Main HTML structure
├── app.js          # JavaScript functionality
└── styles.css      # Visual styling
```

**Hiểu về kiến trúc:**
- **Phân tách** các mối quan tâm giữa cấu trúc (HTML), hành vi (JavaScript), và trình bày (CSS)
- **Duy trì** cấu trúc tệp đơn giản dễ điều hướng và chỉnh sửa
- **Tuân theo** các thực hành tốt nhất trong phát triển web về tổ chức và khả năng bảo trì

### Xây dựng nền tảng HTML: Cấu trúc ngữ nghĩa cho khả năng truy cập

Hãy bắt đầu với cấu trúc HTML. Phát triển web hiện đại nhấn mạnh "HTML ngữ nghĩa" – sử dụng các phần tử HTML mô tả rõ ràng mục đích của chúng, không chỉ là hình thức. Điều này làm cho ứng dụng của bạn dễ truy cập với các trình đọc màn hình, công cụ tìm kiếm, và các công cụ khác.

**Tại sao HTML ngữ nghĩa quan trọng**: Hãy tưởng tượng mô tả ứng dụng trò chuyện của bạn cho ai đó qua điện thoại. Bạn sẽ nói "có một tiêu đề với tiêu đề, một khu vực chính nơi các cuộc trò chuyện xuất hiện, và một biểu mẫu ở dưới cùng để nhập tin nhắn." HTML ngữ nghĩa sử dụng các phần tử phù hợp với mô tả tự nhiên này.

Tạo `index.html` với đánh dấu được cấu trúc cẩn thận này:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Chat Assistant</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="chat-container">
        <header class="chat-header">
            <h1>AI Chat Assistant</h1>
            <p>Ask me anything!</p>
        </header>
        
        <main class="chat-messages" id="messages" role="log" aria-live="polite">
            <!-- Messages will be dynamically added here -->
        </main>
        
        <form class="chat-form" id="chatForm">
            <div class="input-group">
                <input 
                    type="text" 
                    id="messageInput" 
                    placeholder="Type your message here..." 
                    required
                    aria-label="Chat message input"
                >
                <button type="submit" id="sendBtn" aria-label="Send message">
                    Send
                </button>
            </div>
        </form>
    </div>
    <script src="app.js"></script>
</body>
</html>
```

**Hiểu về từng phần tử HTML và mục đích của nó:**

#### Cấu trúc tài liệu
- **`<!DOCTYPE html>`**: Thông báo cho trình duyệt đây là HTML5 hiện đại
- **`<html lang="en">`**: Xác định ngôn ngữ trang cho trình đọc màn hình và công cụ dịch
- **`<meta charset="UTF-8">`**: Đảm bảo mã hóa ký tự đúng cho văn bản quốc tế
- **`<meta name="viewport"...>`**: Làm cho trang đáp ứng trên thiết bị di động bằng cách kiểm soát thu phóng và tỷ lệ

#### Các phần tử ngữ nghĩa
- **`<header>`**: Xác định rõ ràng phần trên cùng với tiêu đề và mô tả
- **`<main>`**: Chỉ định khu vực nội dung chính (nơi các cuộc trò chuyện diễn ra)
- **`<form>`**: Ngữ nghĩa chính xác cho đầu vào của người dùng, cho phép điều hướng bàn phím đúng cách

#### Các tính năng truy cập
- **`role="log"`**: Thông báo cho trình đọc màn hình khu vực này chứa nhật ký các tin nhắn theo thứ tự thời gian
- **`aria-live="polite"`**: Thông báo các tin nhắn mới cho trình đọc màn hình mà không làm gián đoạn
- **`aria-label`**: Cung cấp nhãn mô tả cho các điều khiển biểu mẫu
- **`required`**: Trình duyệt xác thực rằng người dùng nhập tin nhắn trước khi gửi

#### Tích hợp CSS và JavaScript
- **Thuộc tính `class`**: Cung cấp các móc nối cho CSS (ví dụ: `chat-container`, `input-group`)
- **Thuộc tính `id`**: Cho phép JavaScript tìm và thao tác các phần tử cụ thể
- **Vị trí script**: Tệp JavaScript được tải ở cuối để HTML tải trước

**Tại sao cấu trúc này hoạt động:**
- **Luồng logic**: Tiêu đề → Nội dung chính → Biểu mẫu nhập khớp với thứ tự đọc tự nhiên
- **Có thể truy cập bằng bàn phím**: Người dùng có thể tab qua tất cả các phần tử tương tác
- **Thân thiện với trình đọc màn hình**: Các mốc rõ ràng và mô tả cho người dùng khiếm thị
- **Đáp ứng trên thiết bị di động**: Thẻ meta viewport cho phép thiết kế đáp ứng
- **Nâng cấp tiến bộ**: Hoạt động ngay cả khi CSS hoặc JavaScript không tải

### Thêm JavaScript tương tác: Logic ứng dụng web hiện đại

Bây giờ hãy xây dựng JavaScript mang giao diện trò chuyện của chúng ta vào cuộc sống. Chúng ta sẽ sử dụng các mẫu JavaScript hiện đại mà bạn sẽ gặp trong phát triển web chuyên nghiệp, bao gồm các lớp ES6, async/await, và lập trình dựa trên sự kiện.

#### Hiểu về kiến trúc JavaScript hiện đại

Thay vì viết mã thủ tục (một loạt các hàm chạy theo thứ tự), chúng ta sẽ tạo một **kiến trúc dựa trên lớp**. Hãy nghĩ về một lớp như một bản thiết kế để tạo các đối tượng – giống như cách bản thiết kế của kiến trúc sư có thể được sử dụng để xây dựng nhiều ngôi nhà.

**Tại sao sử dụng lớp cho ứng dụng web?**
- **Tổ chức**: Tất cả chức năng liên quan được nhóm lại với nhau
- **Tái sử dụng**: Bạn có thể tạo nhiều phiên trò chuyện trên cùng một trang
- **Khả năng bảo trì**: Dễ dàng gỡ lỗi và chỉnh sửa các tính năng cụ thể
- **Tiêu chuẩn chuyên nghiệp**: Mẫu này được sử dụng trong các framework như React, Vue, và Angular

Tạo `app.js` với JavaScript hiện đại, được cấu trúc tốt này:

```javascript
// app.js - Modern chat application logic

class ChatApp {
    constructor() {
        // Get references to DOM elements we'll need to manipulate
        this.messages = document.getElementById("messages");
        this.form = document.getElementById("chatForm");
        this.input = document.getElementById("messageInput");
        this.sendButton = document.getElementById("sendBtn");
        
        // Configure your backend URL here
        this.BASE_URL = "http://localhost:5000"; // Update this for your environment
        this.API_ENDPOINT = `${this.BASE_URL}/hello`;
        
        // Set up event listeners when the chat app is created
        this.initializeEventListeners();
    }
    
    initializeEventListeners() {
        // Listen for form submission (when user clicks Send or presses Enter)
        this.form.addEventListener("submit", (e) => this.handleSubmit(e));
        
        // Also listen for Enter key in the input field (better UX)
        this.input.addEventListener("keypress", (e) => {
            if (e.key === "Enter" && !e.shiftKey) {
                e.preventDefault();
                this.handleSubmit(e);
            }
        });
    }
    
    async handleSubmit(event) {
        event.preventDefault(); // Prevent form from refreshing the page
        
        const messageText = this.input.value.trim();
        if (!messageText) return; // Don't send empty messages
        
        // Provide user feedback that something is happening
        this.setLoading(true);
        
        // Add user message to chat immediately (optimistic UI)
        this.appendMessage(messageText, "user");
        
        // Clear input field so user can type next message
        this.input.value = '';
        
        try {
            // Call the AI API and wait for response
            const reply = await this.callAPI(messageText);
            
            // Add AI response to chat
            this.appendMessage(reply, "assistant");
        } catch (error) {
            console.error('API Error:', error);
            this.appendMessage("Sorry, I'm having trouble connecting right now. Please try again.", "error");
        } finally {
            // Re-enable the interface regardless of success or failure
            this.setLoading(false);
        }
    }
    
    async callAPI(message) {
        const response = await fetch(this.API_ENDPOINT, {
            method: "POST",
            headers: { 
                "Content-Type": "application/json" 
            },
            body: JSON.stringify({ message })
        });
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const data = await response.json();
        return data.response;
    }
    
    appendMessage(text, role) {
        const messageElement = document.createElement("div");
        messageElement.className = `message ${role}`;
        messageElement.innerHTML = `
            <div class="message-content">
                <span class="message-text">${this.escapeHtml(text)}</span>
                <span class="message-time">${new Date().toLocaleTimeString()}</span>
            </div>
        `;
        
        this.messages.appendChild(messageElement);
        this.scrollToBottom();
    }
    
    escapeHtml(text) {
        const div = document.createElement('div');
        div.textContent = text;
        return div.innerHTML;
    }
    
    scrollToBottom() {
        this.messages.scrollTop = this.messages.scrollHeight;
    }
    
    setLoading(isLoading) {
        this.sendButton.disabled = isLoading;
        this.input.disabled = isLoading;
        this.sendButton.textContent = isLoading ? "Sending..." : "Send";
    }
}

// Initialize the chat application when the page loads
document.addEventListener("DOMContentLoaded", () => {
    new ChatApp();
});
```

#### Hiểu về từng khái niệm JavaScript

**Cấu trúc lớp ES6**:
```javascript
class ChatApp {
    constructor() {
        // This runs when you create a new ChatApp instance
        // It's like the "setup" function for your chat
    }
    
    methodName() {
        // Methods are functions that belong to the class
        // They can access class properties using "this"
    }
}
```

**Mẫu Async/Await**:
```javascript
// Old way (callback hell):
fetch(url)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// Modern way (async/await):
try {
    const response = await fetch(url);
    const data = await response.json();
    console.log(data);
} catch (error) {
    console.error(error);
}
```

**Lập trình dựa trên sự kiện**:
Thay vì liên tục kiểm tra xem có điều gì xảy ra không, chúng ta "lắng nghe" các sự kiện:
```javascript
// When form is submitted, run handleSubmit
this.form.addEventListener("submit", (e) => this.handleSubmit(e));

// When Enter key is pressed, also run handleSubmit
this.input.addEventListener("keypress", (e) => { /* ... */ });
```

**DOM Manipulation**:
```javascript
// Create new elements
const messageElement = document.createElement("div");

// Modify their properties
messageElement.className = "message user";
messageElement.innerHTML = "Hello world!";

// Add to the page
this.messages.appendChild(messageElement);
```

#### Bảo mật và thực hành tốt nhất

**Ngăn chặn XSS**:
```javascript
escapeHtml(text) {
    const div = document.createElement('div');
    div.textContent = text;  // This automatically escapes HTML
    return div.innerHTML;
}
```

**Tại sao điều này quan trọng**: Nếu người dùng nhập `<script>alert('hack')</script>`, hàm này đảm bảo nó hiển thị dưới dạng văn bản thay vì thực thi dưới dạng mã.

**Xử lý lỗi**:
```javascript
try {
    const reply = await this.callAPI(messageText);
    this.appendMessage(reply, "assistant");
} catch (error) {
    // Show user-friendly error instead of breaking the app
    this.appendMessage("Sorry, I'm having trouble...", "error");
}
```

**Cân nhắc trải nghiệm người dùng**:
- **Giao diện lạc quan**: Thêm tin nhắn của người dùng ngay lập tức, không chờ phản hồi từ máy chủ
- **Trạng thái tải**: Vô hiệu hóa nút và hiển thị "Đang gửi..." trong khi chờ
- **Cuộn tự động**: Giữ các tin nhắn mới nhất hiển thị
- **Xác thực đầu vào**: Không gửi tin nhắn trống
- **Phím tắt**: Phím Enter gửi tin nhắn (giống như các ứng dụng trò chuyện thực tế)

#### Hiểu về luồng ứng dụng

1. **Trang tải** → Sự kiện `DOMContentLoaded` được kích hoạt → `new ChatApp()` được tạo
2. **Constructor chạy** → Lấy các tham chiếu phần tử DOM → Thiết lập các trình lắng nghe sự kiện
3. **Người dùng nhập tin nhắn** → Nhấn Enter hoặc nhấp Gửi → `handleSubmit` chạy
4. **handleSubmit** → Xác thực đầu vào → Hiển thị trạng thái tải → Gọi API
5. **API phản hồi** → Thêm tin nhắn AI vào trò chuyện → Kích hoạt lại giao diện
6. **Sẵn sàng cho tin nhắn tiếp theo** → Người dùng có thể tiếp tục trò chuyện
Kiến trúc này có khả năng mở rộng – bạn có thể dễ dàng thêm các tính năng như chỉnh sửa tin nhắn, tải lên tệp, hoặc nhiều luồng hội thoại mà không cần viết lại cấu trúc cốt lõi.

### Tạo kiểu giao diện trò chuyện của bạn

Bây giờ hãy tạo một giao diện trò chuyện hiện đại, hấp dẫn về mặt hình ảnh bằng CSS. Việc tạo kiểu tốt giúp ứng dụng của bạn trông chuyên nghiệp hơn và cải thiện trải nghiệm người dùng tổng thể. Chúng ta sẽ sử dụng các tính năng CSS hiện đại như Flexbox, CSS Grid và các thuộc tính tùy chỉnh để thiết kế đáp ứng và dễ tiếp cận.

Tạo tệp `styles.css` với các kiểu toàn diện sau:

```css
/* styles.css - Modern chat interface styling */

:root {
    --primary-color: #2563eb;
    --secondary-color: #f1f5f9;
    --user-color: #3b82f6;
    --assistant-color: #6b7280;
    --error-color: #ef4444;
    --text-primary: #1e293b;
    --text-secondary: #64748b;
    --border-radius: 12px;
    --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
}

.chat-container {
    width: 100%;
    max-width: 800px;
    height: 600px;
    background: white;
    border-radius: var(--border-radius);
    box-shadow: var(--shadow);
    display: flex;
    flex-direction: column;
    overflow: hidden;
}

.chat-header {
    background: var(--primary-color);
    color: white;
    padding: 20px;
    text-align: center;
}

.chat-header h1 {
    font-size: 1.5rem;
    margin-bottom: 5px;
}

.chat-header p {
    opacity: 0.9;
    font-size: 0.9rem;
}

.chat-messages {
    flex: 1;
    padding: 20px;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    gap: 15px;
    background: var(--secondary-color);
}

.message {
    display: flex;
    max-width: 80%;
    animation: slideIn 0.3s ease-out;
}

.message.user {
    align-self: flex-end;
}

.message.user .message-content {
    background: var(--user-color);
    color: white;
    border-radius: var(--border-radius) var(--border-radius) 4px var(--border-radius);
}

.message.assistant {
    align-self: flex-start;
}

.message.assistant .message-content {
    background: white;
    color: var(--text-primary);
    border-radius: var(--border-radius) var(--border-radius) var(--border-radius) 4px;
    border: 1px solid #e2e8f0;
}

.message.error .message-content {
    background: var(--error-color);
    color: white;
    border-radius: var(--border-radius);
}

.message-content {
    padding: 12px 16px;
    box-shadow: var(--shadow);
    position: relative;
}

.message-text {
    display: block;
    line-height: 1.5;
    word-wrap: break-word;
}

.message-time {
    display: block;
    font-size: 0.75rem;
    opacity: 0.7;
    margin-top: 5px;
}

.chat-form {
    padding: 20px;
    border-top: 1px solid #e2e8f0;
    background: white;
}

.input-group {
    display: flex;
    gap: 10px;
    align-items: center;
}

#messageInput {
    flex: 1;
    padding: 12px 16px;
    border: 2px solid #e2e8f0;
    border-radius: var(--border-radius);
    font-size: 1rem;
    outline: none;
    transition: border-color 0.2s ease;
}

#messageInput:focus {
    border-color: var(--primary-color);
}

#messageInput:disabled {
    background: #f8fafc;
    opacity: 0.6;
    cursor: not-allowed;
}

#sendBtn {
    padding: 12px 24px;
    background: var(--primary-color);
    color: white;
    border: none;
    border-radius: var(--border-radius);
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.2s ease;
    min-width: 80px;
}

#sendBtn:hover:not(:disabled) {
    background: #1d4ed8;
}

#sendBtn:disabled {
    background: #94a3b8;
    cursor: not-allowed;
}

@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateY(10px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Responsive design for mobile devices */
@media (max-width: 768px) {
    body {
        padding: 10px;
    }
    
    .chat-container {
        height: calc(100vh - 20px);
        border-radius: 8px;
    }
    
    .message {
        max-width: 90%;
    }
    
    .input-group {
        flex-direction: column;
        gap: 10px;
    }
    
    #messageInput {
        width: 100%;
    }
    
    #sendBtn {
        width: 100%;
    }
}

/* Accessibility improvements */
@media (prefers-reduced-motion: reduce) {
    .message {
        animation: none;
    }
    
    * {
        transition: none !important;
    }
}

/* Dark mode support */
@media (prefers-color-scheme: dark) {
    .chat-container {
        background: #1e293b;
        color: #f1f5f9;
    }
    
    .chat-messages {
        background: #0f172a;
    }
    
    .message.assistant .message-content {
        background: #334155;
        color: #f1f5f9;
        border-color: #475569;
    }
    
    .chat-form {
        background: #1e293b;
        border-color: #475569;
    }
    
    #messageInput {
        background: #334155;
        color: #f1f5f9;
        border-color: #475569;
    }
}
```

**Hiểu kiến trúc CSS:**
- **Sử dụng** các thuộc tính tùy chỉnh CSS (biến) để tạo chủ đề nhất quán và dễ bảo trì
- **Áp dụng** bố cục Flexbox để thiết kế đáp ứng và căn chỉnh chính xác
- **Bao gồm** các hiệu ứng chuyển động mượt mà cho sự xuất hiện của tin nhắn mà không gây mất tập trung
- **Cung cấp** sự khác biệt trực quan giữa tin nhắn của người dùng, phản hồi của AI và trạng thái lỗi
- **Hỗ trợ** thiết kế đáp ứng hoạt động tốt trên cả máy tính để bàn và thiết bị di động
- **Xem xét** khả năng tiếp cận với các tùy chọn giảm chuyển động và tỷ lệ tương phản phù hợp
- **Cung cấp** hỗ trợ chế độ tối dựa trên tùy chọn hệ thống của người dùng

### Cấu hình URL Backend của bạn

Bước cuối cùng là cập nhật `BASE_URL` trong JavaScript của bạn để khớp với máy chủ backend:

```javascript
// For local development
this.BASE_URL = "http://localhost:5000";

// For GitHub Codespaces (replace with your actual URL)
this.BASE_URL = "https://your-codespace-name-5000.app.github.dev";
```

**Xác định URL backend của bạn:**
- **Phát triển cục bộ**: Sử dụng `http://localhost:5000` nếu chạy cả frontend và backend trên máy cục bộ
- **Codespaces**: Tìm URL backend của bạn trong tab Ports sau khi làm cho cổng 5000 công khai
- **Sản xuất**: Thay thế bằng tên miền thực tế của bạn khi triển khai lên dịch vụ lưu trữ

> 💡 **Mẹo kiểm tra**: Bạn có thể kiểm tra trực tiếp backend của mình bằng cách truy cập URL gốc trong trình duyệt. Bạn sẽ thấy thông báo chào mừng từ máy chủ FastAPI của bạn.

## Kiểm tra và triển khai

Bây giờ bạn đã xây dựng cả thành phần frontend và backend, hãy kiểm tra xem mọi thứ hoạt động cùng nhau và khám phá các tùy chọn triển khai để chia sẻ trợ lý trò chuyện của bạn với người khác.

### Quy trình kiểm tra cục bộ

Thực hiện các bước sau để kiểm tra ứng dụng hoàn chỉnh của bạn:

```mermaid
graph TD
    A[Start Backend Server] --> B[Configure Environment Variables]
    B --> C[Test API Endpoints]
    C --> D[Open Frontend in Browser]
    D --> E[Test Chat Functionality]
    E --> F[Debug Any Issues]
```

**Quy trình kiểm tra từng bước:**

1. **Khởi động máy chủ backend của bạn**:
   ```bash
   cd backend
   source venv/bin/activate  # or venv\Scripts\activate on Windows
   python api.py
   ```

2. **Xác minh API hoạt động**:
   - Mở `http://localhost:5000` trong trình duyệt của bạn
   - Bạn sẽ thấy thông báo chào mừng từ máy chủ FastAPI của bạn

3. **Mở frontend của bạn**:
   - Điều hướng đến thư mục frontend của bạn
   - Mở `index.html` trong trình duyệt web của bạn
   - Hoặc sử dụng tiện ích Live Server của VS Code để có trải nghiệm phát triển tốt hơn

4. **Kiểm tra chức năng trò chuyện**:
   - Nhập một tin nhắn vào trường nhập liệu
   - Nhấp vào "Gửi" hoặc nhấn Enter
   - Xác minh AI phản hồi phù hợp
   - Kiểm tra bảng điều khiển trình duyệt để tìm bất kỳ lỗi JavaScript nào

### Xử lý sự cố thường gặp

| Vấn đề | Triệu chứng | Giải pháp |
|--------|------------|-----------|
| **Lỗi CORS** | Frontend không thể kết nối với backend | Đảm bảo FastAPI CORSMiddleware được cấu hình đúng |
| **Lỗi API Key** | Phản hồi 401 Unauthorized | Kiểm tra biến môi trường `GITHUB_TOKEN` của bạn |
| **Kết nối bị từ chối** | Lỗi mạng trong frontend | Xác minh URL backend và rằng máy chủ Flask đang chạy |
| **Không có phản hồi từ AI** | Phản hồi trống hoặc lỗi | Kiểm tra nhật ký backend để tìm lỗi hạn mức API hoặc vấn đề xác thực |

**Các bước gỡ lỗi phổ biến:**
- **Kiểm tra** bảng điều khiển Developer Tools của trình duyệt để tìm lỗi JavaScript
- **Xác minh** tab Network hiển thị các yêu cầu và phản hồi API thành công
- **Xem lại** đầu ra terminal của backend để tìm lỗi Python hoặc vấn đề API
- **Xác nhận** các biến môi trường được tải và truy cập đúng cách

## Thử thách GitHub Copilot Agent 🚀

Sử dụng chế độ Agent để hoàn thành thử thách sau:

**Mô tả:** Nâng cấp trợ lý trò chuyện bằng cách thêm lịch sử hội thoại và khả năng lưu trữ tin nhắn. Thử thách này sẽ giúp bạn hiểu cách quản lý trạng thái trong các ứng dụng trò chuyện và triển khai lưu trữ dữ liệu để cải thiện trải nghiệm người dùng.

**Yêu cầu:** Sửa đổi ứng dụng trò chuyện để bao gồm lịch sử hội thoại được lưu trữ giữa các phiên. Thêm chức năng lưu tin nhắn trò chuyện vào bộ nhớ cục bộ, hiển thị lịch sử hội thoại khi trang tải, và bao gồm nút "Xóa lịch sử". Cũng triển khai các chỉ báo đang nhập và dấu thời gian tin nhắn để làm cho trải nghiệm trò chuyện thực tế hơn.

Tìm hiểu thêm về [chế độ agent](https://code.visualstudio.com/blogs/2025/02/24/introducing-copilot-agent-mode) tại đây.

## Bài tập: Xây dựng trợ lý AI cá nhân của bạn

Bây giờ bạn sẽ tạo một triển khai trợ lý AI của riêng mình. Thay vì chỉ sao chép mã hướng dẫn, đây là cơ hội để bạn áp dụng các khái niệm trong việc xây dựng một thứ phản ánh sở thích và trường hợp sử dụng của riêng bạn.

### Yêu cầu dự án

Hãy thiết lập dự án của bạn với một cấu trúc sạch sẽ, có tổ chức:

```text
my-ai-assistant/
├── backend/
│   ├── api.py          # Your FastAPI server
│   ├── llm.py          # AI integration functions
│   ├── .env            # Your secrets (keep this safe!)
│   └── requirements.txt # Python dependencies
├── frontend/
│   ├── index.html      # Your chat interface
│   ├── app.js          # The JavaScript magic
│   └── styles.css      # Make it look amazing
└── README.md           # Tell the world about your creation
```

### Nhiệm vụ triển khai cốt lõi

**Phát triển Backend:**
- **Sử dụng** mã FastAPI của chúng tôi và tùy chỉnh theo cách của bạn
- **Tạo** một tính cách AI độc đáo – có thể là trợ lý nấu ăn hữu ích, đối tác viết sáng tạo, hoặc bạn đồng hành học tập?
- **Thêm** xử lý lỗi mạnh mẽ để ứng dụng của bạn không bị hỏng khi có sự cố
- **Viết** tài liệu rõ ràng cho bất kỳ ai muốn hiểu cách API của bạn hoạt động

**Phát triển Frontend:**
- **Xây dựng** giao diện trò chuyện cảm giác trực quan và thân thiện
- **Viết** JavaScript sạch, hiện đại mà bạn tự hào khi giới thiệu với các nhà phát triển khác
- **Thiết kế** kiểu dáng tùy chỉnh phản ánh tính cách của AI của bạn – vui nhộn và đầy màu sắc? Sạch sẽ và tối giản? Hoàn toàn tùy thuộc vào bạn!
- **Đảm bảo** nó hoạt động tốt trên cả điện thoại và máy tính

**Yêu cầu cá nhân hóa:**
- **Chọn** một tên và tính cách độc đáo cho trợ lý AI của bạn – có thể là thứ phản ánh sở thích của bạn hoặc các vấn đề bạn muốn giải quyết
- **Tùy chỉnh** thiết kế trực quan để phù hợp với phong cách của trợ lý của bạn
- **Viết** một thông điệp chào mừng hấp dẫn khiến mọi người muốn bắt đầu trò chuyện
- **Kiểm tra** trợ lý của bạn với các loại câu hỏi khác nhau để xem cách nó phản hồi

### Ý tưởng nâng cấp (Tùy chọn)

Muốn đưa dự án của bạn lên một tầm cao mới? Dưới đây là một số ý tưởng thú vị để khám phá:

| Tính năng | Mô tả | Kỹ năng bạn sẽ thực hành |
|-----------|-------|--------------------------|
| **Lịch sử tin nhắn** | Ghi nhớ các cuộc hội thoại ngay cả sau khi làm mới trang | Làm việc với localStorage, xử lý JSON |
| **Chỉ báo đang nhập** | Hiển thị "AI đang nhập..." trong khi chờ phản hồi | Hiệu ứng CSS, lập trình bất đồng bộ |
| **Dấu thời gian tin nhắn** | Hiển thị thời gian gửi mỗi tin nhắn | Định dạng ngày/giờ, thiết kế UX |
| **Xuất trò chuyện** | Cho phép người dùng tải xuống cuộc hội thoại của họ | Xử lý tệp, xuất dữ liệu |
| **Chuyển đổi chủ đề** | Chuyển đổi giữa chế độ sáng/tối | Các biến CSS, tùy chọn người dùng |
| **Nhập giọng nói** | Thêm chức năng chuyển giọng nói thành văn bản | Web APIs, khả năng tiếp cận |

### Kiểm tra và tài liệu

**Đảm bảo chất lượng:**
- **Kiểm tra** ứng dụng của bạn với các loại đầu vào và trường hợp ngoại lệ khác nhau
- **Xác minh** thiết kế đáp ứng hoạt động trên các kích thước màn hình khác nhau
- **Kiểm tra** khả năng tiếp cận với điều hướng bằng bàn phím và trình đọc màn hình
- **Xác nhận** HTML và CSS tuân thủ các tiêu chuẩn

**Yêu cầu tài liệu:**
- **Viết** README.md giải thích về dự án của bạn và cách chạy nó
- **Bao gồm** ảnh chụp màn hình giao diện trò chuyện của bạn đang hoạt động
- **Tài liệu hóa** bất kỳ tính năng hoặc tùy chỉnh độc đáo nào bạn đã thêm
- **Cung cấp** hướng dẫn thiết lập rõ ràng cho các nhà phát triển khác

### Hướng dẫn nộp bài

**Các sản phẩm dự án:**
1. Thư mục dự án hoàn chỉnh với tất cả mã nguồn
2. README.md với mô tả dự án và hướng dẫn thiết lập
3. Ảnh chụp màn hình minh họa trợ lý trò chuyện của bạn đang hoạt động
4. Phản ánh ngắn gọn về những gì bạn đã học và những thách thức bạn đã gặp phải

**Tiêu chí đánh giá:**
- **Chức năng**: Trợ lý trò chuyện có hoạt động như mong đợi không?
- **Chất lượng mã**: Mã có được tổ chức tốt, có chú thích và dễ bảo trì không?
- **Thiết kế**: Giao diện có hấp dẫn về mặt hình ảnh và thân thiện với người dùng không?
- **Sáng tạo**: Triển khai của bạn có độc đáo và được cá nhân hóa không?
- **Tài liệu**: Hướng dẫn thiết lập có rõ ràng và đầy đủ không?

> 💡 **Mẹo thành công**: Bắt đầu với các yêu cầu cơ bản trước, sau đó thêm các nâng cấp khi mọi thứ hoạt động. Tập trung vào việc tạo trải nghiệm cốt lõi mượt mà trước khi thêm các tính năng nâng cao.

## Giải pháp

[Giải pháp](./solution/README.md)

## Thử thách bổ sung

Sẵn sàng đưa trợ lý AI của bạn lên một tầm cao mới? Hãy thử các thử thách nâng cao này để hiểu sâu hơn về tích hợp AI và kỹ thuật phát triển web.

### Tùy chỉnh tính cách

Điều kỳ diệu thực sự xảy ra khi bạn tạo cho trợ lý AI của mình một tính cách độc đáo. Thử nghiệm với các lời nhắc hệ thống khác nhau để tạo ra các trợ lý chuyên biệt:

**Ví dụ trợ lý chuyên nghiệp:**
```python
call_llm(message, "You are a professional business consultant with 20 years of experience. Provide structured, actionable advice with specific steps and considerations.")
```

**Ví dụ trợ lý viết sáng tạo:**
```python
call_llm(message, "You are an enthusiastic creative writing coach. Help users develop their storytelling skills with imaginative prompts and constructive feedback.")
```

**Ví dụ cố vấn kỹ thuật:**
```python
call_llm(message, "You are a patient senior developer who explains complex programming concepts using simple analogies and practical examples.")
```

### Nâng cấp Frontend

Biến đổi giao diện trò chuyện của bạn với các cải tiến về hình ảnh và chức năng sau:

**Tính năng CSS nâng cao:**
- **Triển khai** các hiệu ứng chuyển động và chuyển đổi tin nhắn mượt mà
- **Thêm** thiết kế bong bóng trò chuyện tùy chỉnh với các hình dạng và gradient CSS
- **Tạo** hiệu ứng chỉ báo đang nhập cho khi AI "đang suy nghĩ"
- **Thiết kế** các phản ứng emoji hoặc hệ thống đánh giá tin nhắn

**Cải tiến JavaScript:**
- **Thêm** phím tắt (Ctrl+Enter để gửi, Escape để xóa nhập liệu)
- **Triển khai** chức năng tìm kiếm và lọc tin nhắn
- **Tạo** tính năng xuất hội thoại (tải xuống dưới dạng văn bản hoặc JSON)
- **Thêm** tự động lưu vào localStorage để tránh mất tin nhắn

### Tích hợp AI nâng cao

**Nhiều tính cách AI:**
- **Tạo** một menu thả xuống để chuyển đổi giữa các tính cách AI khác nhau
- **Lưu** tính cách ưa thích của người dùng vào localStorage
- **Triển khai** chuyển đổi ngữ cảnh duy trì luồng hội thoại

**Tính năng phản hồi thông minh:**
- **Thêm** nhận thức ngữ cảnh hội thoại (AI nhớ các tin nhắn trước đó)
- **Triển khai** các gợi ý thông minh dựa trên chủ đề hội thoại
- **Tạo** các nút trả lời nhanh cho các câu hỏi phổ biến

> 🎯 **Mục tiêu học tập**: Các thử thách bổ sung này giúp bạn hiểu các mẫu phát triển web nâng cao và kỹ thuật tích hợp AI được sử dụng trong các ứng dụng sản xuất.

## Tóm tắt và bước tiếp theo

Chúc mừng! Bạn đã xây dựng thành công một trợ lý trò chuyện tích hợp AI hoàn chỉnh từ đầu. Dự án này đã mang lại cho bạn kinh nghiệm thực tế với các công nghệ phát triển web hiện đại và tích hợp AI – những kỹ năng ngày càng có giá trị trong lĩnh vực công nghệ hiện nay.

### Những gì bạn đã đạt được

Trong suốt bài học này, bạn đã làm chủ một số công nghệ và khái niệm chính:

**Phát triển Backend:**
- **Tích hợp** với GitHub Models API để có chức năng AI
- **Xây dựng** một API RESTful bằng Flask với xử lý lỗi đúng cách
- **Triển khai** xác thực an toàn bằng cách sử dụng các biến môi trường
- **Cấu hình** CORS cho các yêu cầu chéo giữa frontend và backend

**Phát triển Frontend:**
- **Tạo** giao diện trò chuyện đáp ứng bằng HTML ngữ nghĩa
- **Triển khai** JavaScript hiện đại với async/await và kiến trúc dựa trên lớp
- **Thiết kế** giao diện người dùng hấp dẫn với CSS Grid, Flexbox và hiệu ứng chuyển động
- **Thêm** các tính năng khả năng tiếp cận và nguyên tắc thiết kế đáp ứng

**Tích hợp Full-Stack:**
- **Kết nối** frontend và backend thông qua các yêu cầu API HTTP
- **Xử lý** tương tác người dùng theo thời gian thực và luồng dữ liệu bất đồng bộ
- **Triển khai** xử lý lỗi và phản hồi người dùng trong toàn bộ ứng dụng
- **Kiểm tra** quy trình làm việc ứng dụng hoàn chỉnh từ đầu vào của người dùng đến phản hồi của AI

### Kết quả học tập chính

```mermaid
mindmap
  root((AI Chat App Skills))
    API Integration
      Authentication
      Error Handling
      Async Programming
    Web Development
      HTML5 Semantics
      Modern CSS
      ES6+ JavaScript
    User Experience
      Responsive Design
      Accessibility
      Real-time Interaction
    AI Understanding
      Prompt Engineering
      Model Parameters
      Conversation Flow
```

Dự án này đã giới thiệu cho bạn các nguyên tắc cơ bản về xây dựng ứng dụng tích hợp AI, đại diện cho tương lai của phát triển web. Bạn hiện đã hiểu cách tích hợp các khả năng AI vào các ứng dụng web truyền thống, tạo ra trải nghiệm người dùng hấp dẫn, thông minh và đáp ứng.

### Ứng dụng chuyên nghiệp

Các kỹ năng bạn đã phát triển trong bài học này có thể áp dụng trực tiếp vào các sự nghiệp phát triển phần mềm hiện đại:

- **Phát triển web full-stack** sử dụng các framework và API hiện đại
- **Tích hợp AI** trong các ứng dụng web và ứng dụng di động
- **Thiết kế và phát triển API** cho kiến trúc microservices
- **Phát triển giao diện người dùng** với trọng tâm vào khả năng tiếp cận và thiết kế đáp ứng
- **Thực hành DevOps** bao gồm cấu hình môi trường và triển khai

### Tiếp tục hành trình phát triển AI của bạn

**Các bước học tập tiếp theo:**
- **Khám phá** các mô hình AI và API nâng cao hơn (GPT-4, Claude, Gemini)
- **Học** về các kỹ thuật thiết kế lời nhắc để có phản hồi AI tốt hơn
- **Nghiên cứu** thiết kế hội thoại và các nguyên tắc trải nghiệm người dùng chatbot
- **Điều tra** an toàn AI, đạo đức và các thực hành phát triển AI có trách nhiệm
- **Xây dựng** các ứng dụng phức tạp hơn với bộ nhớ hội thoại và nhận thức ngữ cảnh

**Ý tưởng dự án nâng cao:**
- Phòng trò chuyện nhiều người dùng với AI quản lý
- Chatbot dịch vụ khách hàng tích hợp AI
- Trợ lý dạy học với học tập cá nhân hóa
- Cộng tác viên viết sáng tạo với các tính cách AI khác nhau
- Trợ lý tài liệu kỹ thuật cho các nhà phát triển

## Bắt đầu với GitHub Codespaces

Muốn thử dự án này trong môi trường phát triển trên đám mây? GitHub Codespaces cung cấp một thiết lập phát triển hoàn chỉnh trong trình duyệt của bạn, hoàn hảo để thử nghiệm các ứng dụng AI mà không cần yêu cầu thiết lập cục bộ.

### Thiết lập môi trường phát triển của bạn

**Bước 1: Tạo từ mẫu**
- **Điều hướng** đến [Web Dev For Beginners repository](https://github.com/microsoft/Web-Dev-For-Beginners)
- **Nhấp** vào "Use this template" ở góc trên bên phải (đảm bảo bạn đã đăng nhập vào GitHub)

![Giao diện tạo từ mẫu hiển thị nút "Use this template" màu xanh lá cây](../../../translated_images/template.67ad477109d29a2b04599a83c964c87fcde041256d4f04d3589cbb00c696f76c.vi.png)

**Bước 2: Khởi chạy Codespaces**
- **Mở** repository bạn vừa tạo
- **Nhấp** vào nút "Code" màu xanh lá cây và chọn "Codespaces
- **Chuyển tiếp cổng** để kiểm tra ứng dụng của bạn

**Những gì Codespaces cung cấp:**
- **Loại bỏ** các vấn đề thiết lập và cấu hình môi trường cục bộ
- **Cung cấp** môi trường phát triển nhất quán trên các thiết bị khác nhau
- **Bao gồm** các công cụ và tiện ích mở rộng được cấu hình sẵn cho phát triển web
- **Đề xuất** tích hợp liền mạch với GitHub để kiểm soát phiên bản và cộng tác

> 🚀 **Mẹo chuyên nghiệp**: Codespaces rất lý tưởng để học và tạo mẫu ứng dụng AI vì nó tự động xử lý tất cả các thiết lập môi trường phức tạp, giúp bạn tập trung vào việc xây dựng và học hỏi thay vì gặp rắc rối với cấu hình.

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.