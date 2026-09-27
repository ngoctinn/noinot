# Nối Nốt

## Overview

Nối Nốt là một nền tảng cho phép nhiều ứng dụng và công cụ phục vụ các phần khác nhau của đời sống cùng hoạt động trên một **context chung**.

Một người có thể sử dụng những ứng dụng khác nhau cho:

- công việc và dự án;
- danh bạ và các mối quan hệ;
- lịch và việc cần làm;
- tài chính cá nhân;
- sức khỏe và vận động;
- tài sản và phương tiện;
- nhà cửa;
- tài liệu và ghi chú;
- học tập;
- du lịch;
- hoặc những domain khác.

Mỗi ứng dụng có thể có giao diện, dữ liệu và workflow phù hợp với domain của nó.

Nối Nốt không yêu cầu mọi ứng dụng phải trông giống nhau hoặc dùng cùng một schema.

Điểm chung nằm ở phía dưới: những đối tượng, sự kiện và hành động có liên quan có thể giữ được context với nhau thay vì trở thành các bản dữ liệu hoàn toàn độc lập.

---

# Problem

Phần lớn hoạt động trong đời sống hiện được phân tán giữa nhiều ứng dụng.

Ví dụ:

```text
Contacts
→ thông tin về một người

Calendar
→ cuộc hẹn với người đó

Tasks
→ việc cần làm liên quan

Finance
→ một giao dịch

Documents
→ tài liệu liên quan
```

Mỗi ứng dụng có thể giải quyết rất tốt domain của riêng nó.

Vấn đề xuất hiện khi cùng một context đi qua nhiều ứng dụng.

Một sự kiện có thể liên quan đồng thời tới:

```text
Person
Organization
Place
Document
Task
Calendar event
Transaction
```

nhưng các ứng dụng thường chỉ biết phần dữ liệu mà chúng sở hữu.

Người dùng phải tự nhớ và tự nối những phần còn lại.

Nối Nốt hướng tới việc giữ những liên kết đó ở một lớp chung.

---

# Product model

Nối Nốt có thể được hình dung thành ba lớp:

```text
┌─────────────────────────────────────┐
│             Core Apps               │
│ Inbox · Today · Tasks · Calendar    │
│ Search · Activity                   │
├─────────────────────────────────────┤
│            Domain Apps              │
│ Contacts · Finance · Health ·       │
│ Projects · Assets · Home · ...      │
├─────────────────────────────────────┤
│                Tools                │
│ Document · Media · Data · AI · ...  │
├─────────────────────────────────────┤
│         Shared Context Layer        │
│ Entities · Relationships · Events   │
│ Actions · Time · Resources          │
└─────────────────────────────────────┘
```

Các app phía trên không nhất thiết phải dùng chung toàn bộ data model.

Chúng chỉ cần có khả năng tham gia vào context chung khi điều đó hữu ích.

---

# Core apps

Một số chức năng có ý nghĩa trên nhiều domain và có thể tồn tại ở cấp platform.

## Inbox

Một điểm capture chung cho thông tin chưa cần được tổ chức ngay lập tức.

```text
capture
→ lưu trước
→ bổ sung context sau
```

## Today

Một góc nhìn lên những thứ đang cần sự chú ý tại thời điểm hiện tại, bất kể chúng bắt nguồn từ ứng dụng nào.

## Tasks

Các hành động cần thực hiện.

Một task có thể giữ context về nơi nó xuất phát thay vì chỉ tồn tại như một dòng độc lập.

## Calendar

Một góc nhìn theo thời gian.

Bất kỳ domain nào có sự kiện, deadline hoặc lịch đều có thể xuất hiện ở đây.

## Search

Tìm kiếm xuyên qua những context mà người dùng có quyền truy cập.

## Activity

Theo dõi những thay đổi và sự kiện đã xảy ra theo thời gian.

---

# Domain apps

Domain app là một ứng dụng chuyên biệt cho một phần của đời sống.

Ví dụ:

```text
Contacts
Finance
Health
Fitness
Projects
Notes
Assets
Vehicles
Home
Learning
Travel
```

Danh sách này không cố định.

Nối Nốt không giả định rằng mọi người đều cần tất cả các domain trên.

Một domain cũng không nhất thiết phải trở thành một ứng dụng riêng nếu không cần UX hoặc workflow chuyên biệt.

---

## Example: Contacts

Contacts có thể quản lý:

```text
People
Organizations
Contact information
Interactions
Relationships
```

Một Person trong Contacts có thể đồng thời liên quan tới:

```text
Project
Meeting
Task
Organization
Document
```

Các ứng dụng khác không cần tạo một bản Person riêng.

---

## Example: Finance

Finance có thể có model riêng:

```text
Account
Transaction
Budget
Category
Recurring payment
```

Nhưng một transaction vẫn có thể liên quan tới context ngoài Finance.

Ví dụ:

```text
Transaction
→ relates_to → Trip

Transaction
→ relates_to → Vehicle

Transaction
→ relates_to → Project
```

Finance vẫn là một ứng dụng tài chính chuyên biệt.

Context chung chỉ bổ sung mối liên hệ khi nó hữu ích.

---

## Example: Health

Health có thể có những object và workflow riêng:

```text
Appointment
Measurement
Record
Medication
Provider
```

Một appointment có thể đồng thời có:

```text
Person
Place
Calendar time
Document
Task
```

Calendar không cần sở hữu appointment đó.

Nó chỉ hiển thị phần temporal context của nó.

---

## Example: Assets

Một tài sản có thể có:

```text
Owner
Documents
Purchase information
Maintenance history
Related expenses
Events
```

Khi một sự kiện bảo trì xảy ra, các phần khác của hệ thống có thể sử dụng context đó nếu cần.

---

# Tools

Nối Nốt cũng có thể cung cấp các công cụ xử lý dữ liệu.

Ví dụ:

```text
Document tools
Image tools
Audio tools
Video tools
Data tools
AI tools
Converters
Analyzers
```

Tool khác domain app ở chỗ nó chủ yếu thao tác lên một input.

Ví dụ:

```text
Document
   ↓
Convert / extract / analyze
   ↓
Output
```

Nối Nốt có thể giữ provenance:

```text
Output
→ derived_from → Input
→ belongs_to → existing context
```

Nhờ vậy kết quả của một công cụ không trở thành một file tách rời hoàn toàn khỏi nơi nó được tạo ra.

---

# Shared context

Context layer là phần kết nối các ứng dụng và công cụ.

Nó có thể sử dụng một số primitive chung.

## Entity

Một đối tượng có thể được nhận diện độc lập.

Ví dụ:

```text
Person
Organization
Project
Place
Document
Asset
```

Các domain có thể định nghĩa thêm entity type riêng.

Không phải mọi dữ liệu đều cần trở thành entity.

---

## Relationship

Mô tả một mối liên hệ.

```text
Person → works_on → Project

Asset → owned_by → Person

Document → relates_to → Project
```

Relationship cho phép context tồn tại xuyên qua ranh giới giữa các ứng dụng.

---

## Event

Một điều đã xảy ra.

```text
task.completed
appointment.scheduled
document.created
payment.recorded
maintenance.completed
```

Event có thể:

- cập nhật state;
- xuất hiện trong history;
- làm một thông tin khác trở nên relevant;
- hoặc dẫn tới một action.

---

## Action

Một việc có thể hoặc cần được thực hiện.

Action có thể được hiển thị trong Tasks hoặc Today nhưng vẫn giữ context nơi nó bắt nguồn.

---

## Time

Thời gian có thể được gắn với entity, event hoặc action.

Calendar là một projection của những thứ có temporal context.

---

## Resource

Một tài nguyên liên quan tới context.

Ví dụ:

```text
Document
File
Image
Audio
Video
Link
```

---

# Cross-app context

Điểm cốt lõi của Nối Nốt không phải số lượng ứng dụng.

Giá trị xuất hiện khi context có thể tiếp tục qua ranh giới giữa chúng.

Ví dụ:

```text
Contact
   ↓
Meeting
   ↓
Calendar
   ↓
Task
   ↓
Project
```

Hoặc:

```text
Asset
   ↓
Maintenance event
   ↓
Task
   ↓
Calendar
   ↓
Expense
```

Hoặc:

```text
Health appointment
   ↓
Provider
   ↓
Calendar
   ↓
Document
   ↓
Follow-up task
```

Mỗi domain vẫn giữ UX riêng.

Chỉ những phần context cần thiết mới được chia sẻ.

---

# What Nối Nốt is not

Nối Nốt không nhằm biến mọi loại dữ liệu thành cùng một loại object.

Nó cũng không yêu cầu người dùng thao tác trực tiếp với graph, schema hoặc ontology để thực hiện những việc thông thường.

Nó không phải chỉ là:

```text
Task manager
Note-taking app
Calendar
Knowledge graph
Database builder
```

và cũng không phải đơn thuần:

> nhiều ứng dụng được đặt chung trong một giao diện.

Khác biệt nằm ở khả năng để các ứng dụng và công cụ cùng tham gia vào một context chung.

---

# Initial scope

Phiên bản đầu tiên không cần xây nhiều domain app.

Mục tiêu của V1 là kiểm chứng một assumption:

> Một context được tạo ở một phần của hệ thống có thể tiếp tục hữu ích ở phần khác mà không buộc người dùng phải tự copy, nhập lại hoặc ghi nhớ mối liên hệ đó.

V1 có thể tập trung vào:

```text
Inbox
Today
Tasks
Calendar
Search
Projects
Resources
```

cùng:

```text
basic entities
basic relationships
basic events
cross-context references
```

Một workflow hoàn chỉnh quan trọng hơn số lượng ứng dụng.

```text
Capture
   ↓
Connect context
   ↓
Act
   ↓
Schedule
   ↓
Complete
   ↓
Record history
```

---

# Extensibility

Nếu core model chứng minh được giá trị, các domain app mới có thể được bổ sung dần.

Ví dụ:

```text
Contacts
Finance
Health
Fitness
Vehicles
Home
Learning
Travel
```

Một app mới có thể:

1. định nghĩa model riêng cho domain;
2. cung cấp UX chuyên biệt;
3. sử dụng các capability chung của platform;
4. liên kết một phần dữ liệu với context ngoài domain khi cần.

Theo cách này, Nối Nốt có thể mở rộng mà không buộc tất cả domain phải dùng cùng một UI hoặc schema.

---

# Long-term direction

Vision dài hạn của Nối Nốt là trở thành một **personal context platform** nơi nhiều phần của đời sống có thể được quản lý bằng những ứng dụng chuyên biệt nhưng vẫn giữ được mối liên hệ cần thiết giữa chúng.

```text
Apps
     ↓
Shared Context
     ↓
Actions / Events / History
```

Xa hơn, context có thể không chỉ đến từ các ứng dụng nằm bên trong Nối Nốt.

Những hệ thống bên ngoài cũng có thể tham gia vào context theo quyền và phạm vi mà người dùng cho phép.

Nối Nốt khi đó không nhất thiết phải thay thế mọi ứng dụng.

Nó có thể trở thành lớp giúp các ứng dụng khác nhau hiểu đủ context để tiếp tục công việc từ nơi khác.

---

# Core hypothesis

Nối Nốt dựa trên một giả thuyết:

> Những phần khác nhau của đời sống cần các ứng dụng chuyên biệt, nhưng không nhất thiết phải tồn tại trong những silo context hoàn toàn độc lập.

Dự án cần kiểm chứng liệu một shared context layer có thể tạo ra đủ giá trị mà không làm tăng quá nhiều độ phức tạp cho người dùng.

