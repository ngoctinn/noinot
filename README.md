# Nối Nốt

## One-line description

Nối Nốt là một nền tảng giúp một người biểu diễn những thứ quan trọng trong cuộc sống — con người, công việc, dự án, đồ vật, nơi chốn, tài liệu, việc cần làm và sự kiện — dưới dạng các đối tượng có quan hệ với nhau, để thông tin và hành động có thể tiếp tục từ phần này sang phần khác thay vì bị tách rời trong nhiều ứng dụng.

## Problem

Các hoạt động trong cuộc sống thường được quản lý bằng nhiều công cụ riêng biệt: task nằm trong ứng dụng việc cần làm, lịch ở calendar, tài liệu ở nơi khác, project ở công cụ quản lý công việc, còn thông tin về con người, đồ vật hoặc sự kiện lại nằm ở những nơi khác nữa.

Vấn đề không chỉ là phải mở nhiều ứng dụng, mà là **context giữa chúng bị mất**. Một cuộc phỏng vấn có thể liên quan đến một công ty, một vị trí ứng tuyển, một tài liệu CV, một số task chuẩn bị và một lịch hẹn, nhưng các thông tin đó thường không biết đến nhau. Người dùng phải tự nhớ và tự nối chúng lại.

Khi số lượng công việc, tài liệu, mối quan hệ, tài sản và hoạt động tăng lên, việc duy trì những liên kết này bằng trí nhớ hoặc nhập dữ liệu thủ công trở nên khó khăn.

## Core idea

Hạt nhân của Nối Nốt là coi những thứ trong cuộc sống là các **entity** — tức những đối tượng có thể được nhận diện và liên kết với nhau.

Một entity có thể là:

- một người;
- một project;
- một công việc cần làm;
- một sự kiện;
- một nơi;
- một tài liệu;
- một đồ vật;
- hoặc một nguồn thông tin khác có ý nghĩa với người dùng.

Các entity có thể có quan hệ và sự kiện liên quan đến nhau.

Ví dụ:

```text
Tôi
 ├── tham gia → Project A
 ├── sở hữu → Xe máy
 └── ứng tuyển → Công ty B

Project A
 ├── có → Task
 └── liên quan → Tài liệu

Phỏng vấn
 ├── với → Công ty B
 ├── diễn ra → Thứ Hai
 └── cần chuẩn bị → Task
```

Các phần chức năng như Tasks, Calendar hay Projects không sở hữu những thế giới tách biệt. Chúng là những cách khác nhau để xem và thao tác trên cùng một context của cuộc sống.

Một thay đổi ở một phần vì vậy có thể trở thành thông tin hoặc hành động ở phần khác.

## How it works

Người dùng trước hết đưa một thông tin hoặc sự kiện vào hệ thống.

```text
người dùng capture một việc
→ hệ thống xác định nó thuộc context nào
→ liên kết nó với những entity liên quan
→ thông tin xuất hiện ở những nơi phù hợp
```

Ví dụ:

```text
người dùng lưu một buổi phỏng vấn
→ buổi phỏng vấn được liên kết với công ty và hồ sơ ứng tuyển
→ thời gian xuất hiện trong Calendar
→ các việc cần chuẩn bị xuất hiện trong Tasks
→ ngày hôm đó nó xuất hiện trong Today
```

Các entity cũng có thể phát sinh sự kiện.

```text
một sự kiện xảy ra
→ hệ thống biết entity nào liên quan
→ các phần quan tâm tới sự kiện đó có thể phản ứng
```

Ví dụ:

```text
Task được hoàn thành
→ trạng thái Project thay đổi
→ Today không còn hiển thị task
→ lịch sử của Project ghi nhận hoạt động
```

Ở giai đoạn sau, một số phản ứng có thể được tự động hóa, nhưng người dùng vẫn là người quyết định các hành động quan trọng.

## Example scenario

Một người đang tìm việc Backend Developer.

Họ lưu một vị trí tuyển dụng vào Nối Nốt và liên kết nó với công ty đang tuyển. Từ vị trí đó, họ tạo các việc như cập nhật CV, đọc lại yêu cầu tuyển dụng và chuẩn bị project để trình bày. Deadline ứng tuyển và lịch phỏng vấn được đưa vào Calendar nhưng vẫn giữ liên kết với cùng hồ sơ ứng tuyển.

Khi mở Today, người dùng không cần vào riêng Job Tracker, Tasks và Calendar mà có thể thấy những việc cần làm hôm nay cùng context của chúng.

Sau buổi phỏng vấn, note về những câu hỏi đã gặp vẫn thuộc cùng hồ sơ đó và đồng thời có thể trở thành tài liệu học tập cho những lần phỏng vấn tiếp theo.

Như vậy:

```text
Company
   ↓
Job Application
   ├── CV
   ├── Tasks
   ├── Interview
   │      ↓
   │   Calendar
   │
   └── Interview Notes
             ↓
          Learning
```

Dữ liệu không bị copy thành nhiều bản độc lập; các phần chỉ tham chiếu và sử dụng cùng context.

## Core capabilities

### 1. Life entities

Cho phép biểu diễn những đối tượng cơ bản trong cuộc sống và định danh chúng độc lập với từng ứng dụng.

### 2. Relationships

Cho phép mô tả quan hệ giữa các entity.

Ví dụ:

```text
Person → participates_in → Project
Task → belongs_to → Project
Event → involves → Person
Document → relates_to → Job Application
```

### 3. Events

Ghi nhận những điều xảy ra đối với entity, chẳng hạn:

```text
task.completed
interview.scheduled
project.created
document.added
```

Các phần khác trong hệ thống có thể phản ứng dựa trên những event này.

### 4. Tasks and time

Cho phép biến context thành hành động cụ thể và gắn hành động với thời gian.

### 5. Inbox

Một điểm tiếp nhận ban đầu để người dùng nhanh chóng đưa việc, ý tưởng, link, tài liệu hoặc thông tin vào hệ thống trước khi tổ chức chúng.

### 6. Today

Một góc nhìn tổng hợp những gì cần sự chú ý của người dùng tại thời điểm hiện tại, bất kể chúng bắt nguồn từ phần nào của hệ thống.

### 7. Search

Cho phép tìm một chủ đề và thấy các entity liên quan từ nhiều phần của cuộc sống thay vị phải tìm riêng trong từng ứng dụng.

### 8. Cross-context actions

Cho phép một entity hoặc event ở một phần dẫn tới hành động ở phần khác.

Ví dụ:

```text
Interview
→ Calendar event
→ preparation tasks
```

hoặc:

```text
Vehicle maintenance due
→ Task
→ Calendar
```

## Initial scope

Phiên bản đầu tiên không cố gắng số hóa toàn bộ cuộc sống.

Mục tiêu của V1 là chứng minh được ý tưởng quan trọng nhất:

> Các đối tượng thuộc những phần khác nhau của cuộc sống có thể được biểu diễn, liên kết và sử dụng chung thay vì tồn tại trong các silo riêng biệt.

### In scope

V1 tập trung vào một người dùng và một số loại context gần với hoạt động hằng ngày:

- Inbox để capture thông tin;
- entity và relationship cơ bản;
- Tasks;
- Calendar;
- Projects;
- các tài liệu hoặc resource có liên quan;
- Today để tổng hợp những việc hiện tại;
- tìm kiếm giữa các entity;
- một số event và liên kết xuyên phần, ví dụ Project → Task → Calendar.

Một workflow hoàn chỉnh quan trọng hơn số lượng loại entity.

Ví dụ V1 cần làm tốt:

```text
Capture
   ↓
Connect context
   ↓
Create action
   ↓
Schedule
   ↓
Do
   ↓
Record result
```

### Out of scope

Giai đoạn đầu chưa cần:

- quản lý toàn bộ tài chính cá nhân;
- hệ thống nhà thông minh;
- theo dõi sức khỏe;
- quản lý thú cưng hoặc cây trồng;
- mạng xã hội hoặc cộng đồng;
- mô hình hóa thành phố hoặc môi trường;
- tự động ra quyết định thay người dùng;
- federation giữa nhiều hệ thống độc lập;
- cố gắng hỗ trợ mọi loại entity ngay từ đầu.

Những phần này chỉ có ý nghĩa nếu core model đã chứng minh được rằng các domain nhỏ hơn thực sự có thể liên kết với nhau hữu ích.

## Long-term direction

Vision dài hạn là mở rộng Nối Nốt từ context của một cá nhân thành một lớp chung để mô tả những thành phần khác nhau của thế giới xung quanh họ.

Có thể phát triển dần theo hướng:

```text
Individual
    ↓
Household / Family
    ↓
Home / Devices / Assets
    ↓
Pets / Plants
    ↓
Groups / Organizations
    ↓
Community
    ↓
Environment
```

Ví dụ một căn nhà, chiếc xe, thú cưng hoặc cảm biến môi trường cũng có thể được xem là entity có trạng thái, quan hệ và event.

Khi đó:

```text
nhiệt độ môi trường tăng
          ↓
        Event
    ┌─────┼──────┐
    ↓     ↓      ↓
 Person  Home    Pet
```

Mỗi phần có thể phản ứng khác nhau với cùng một sự kiện.

Xa hơn nữa, nhiều hệ thống độc lập có thể chia sẻ một phần context với nhau theo quyền mà chủ thể cho phép. Đây mới là vision dài hạn; nó không phải requirement của phiên bản đầu.

## Open questions

**1. Entity model nên chung đến mức nào?**  
Nếu abstraction quá ít, các domain sẽ lại trở thành silo. Nếu abstraction quá chung, model có thể khó sử dụng và khó hiểu.

**2. Những dữ liệu nào thực sự nên trở thành entity?**  
Không phải mọi thông tin trong cuộc sống đều đáng được cấu trúc hoặc theo dõi.

**3. Mức tự động hóa phù hợp là bao nhiêu?**  
Cần xác định lúc nào hệ thống chỉ nên cung cấp context hoặc đề xuất và lúc nào có thể tự thực hiện hành động.

**4. Người dùng có thực sự nhận được giá trị từ việc liên kết context không?**  
Đây là assumption quan trọng nhất cần kiểm chứng bằng V1. Nếu việc liên kết tạo ra nhiều công sức quản lý hơn giá trị nó mang lại thì core interaction cần thay đổi.

**5. Privacy và ownership sẽ được xử lý ở mức nào?**  
Điều này chưa phải trọng tâm implementation của V1 nhưng trở thành quyết định nền tảng nếu hệ thống sau này chứa ngày càng nhiều dữ liệu về đời sống, gia đình hoặc thế giới vật lý.

**6. Dự án cuối cùng phục vụ riêng chủ sở hữu hay hướng tới nhiều người dùng?**  
V1 có thể tập trung cho một cá nhân, nhưng lựa chọn dài hạn này có thể ảnh hưởng đáng kể đến cách sản phẩm phát triển.

# Tóm tắt

Nối Nốt là một nền tảng giúp một người tổ chức cuộc sống dựa trên mối quan hệ giữa những thứ họ quan tâm thay vì chia chúng thành nhiều ứng dụng độc lập. Con người, project, việc cần làm, lịch hẹn, tài liệu, đồ vật và nơi chốn có thể được biểu diễn thành các entity có quan hệ với nhau. Khi một sự kiện xảy ra ở một phần, context đó có thể được sử dụng ở những phần khác, chẳng hạn một buổi phỏng vấn đồng thời liên quan tới công ty, hồ sơ ứng tuyển, task chuẩn bị và lịch. Các giao diện như Tasks, Calendar, Projects hay Today chỉ là những cách khác nhau để xem và thao tác trên cùng dữ liệu liên kết này. Phiên bản đầu tập trung vào một người dùng, Inbox, Tasks, Calendar, Projects, resource và những liên kết cơ bản giữa chúng để kiểm chứng xem mô hình này có thực sự hữu ích trong đời sống hằng ngày hay không. Nếu core này hoạt động tốt, hệ thống có thể mở rộng dần sang gia đình, nhà cửa, tài sản, thiết bị, động vật, thực vật và môi trường. Vision dài hạn là tạo ra một lớp context chung nơi nhiều loại đối tượng có thể được liên kết và phản ứng với cùng các sự kiện mà không buộc tất cả chúng phải nằm trong một ứng dụng duy nhất.
