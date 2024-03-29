# tpphu.github.io

# Sequence Diagram


## Các loại participant

Có các loại participant:

- participant (default)
- actor
- boundary
- control
- entity
- database
- collections
- queue


```plantuml
@startuml
' Đây là comment
participant Participant as Foo
actor       Actor       as Foo1
' keyword: `as` là để mình alias cái tên cho ngắn lại cho cái việc
' vẽ ra reference sau đó dễ dàng.
boundary    Boundary    as Foo2
control     Control     as Foo3
entity      Entity      as Foo4
database    Database    as Foo5
collections Collections as Foo6
queue       Queue       as Foo7
/' Đây là comment nhiều dòng
   Đây là comment nhiều dòng
'/
Foo -> Foo1 : To actor 
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo -> Foo7: To queue
@enduml
```

#

# Examples

## Basic Example

### Với PlantUML
```plantuml
@startuml
participant "Người dùng" as A
participant "Hệ thống" as B
participant "Cơ sở dữ liệu" as C

A -> B: Gửi yêu cầu
B -> C: Truy vấn dữ liệu
C --> B: Trả về kết quả
B --> A: Hiển thị kết quả
@enduml
```

## Với MermaidJS
```mermaid
sequenceDiagram
  participant A as Người dùng
  participant B as Hệ thống
  participant C as Cơ sở dữ liệu

  A->>B: Gửi yêu cầu
  B->>C: Truy vấn dữ liệu
  C-->>B: Trả về kết quả
  B-->>A: Hiển thị kết quả
```

### Đăng nhập

```plantuml
@startuml
actor "Người Dùng" as user
participant "Giao Diện" as UI
participant "Bộ Xác Thực" as Auth
database "Cơ Sở Dữ Liệu" as DB

user -> UI: Nhập thông tin đăng nhập
UI -> Auth: Kiểm tra thông tin
Auth -> DB: Truy vấn thông tin người dùng
DB --> Auth: Kết quả truy vấn
Auth --> UI: Kết quả xác thực
UI --> user: Hiển thị kết quả
@enduml
```

### Quy trình đặt hàng

```plantuml
@startuml
actor KháchHàng
participant "Website" as Web
participant "Hệ Thống Đặt Hàng" as OrderSys
database "Kho Hàng" as Warehouse

KháchHàng -> Web: Chọn sản phẩm
Web -> OrderSys: Tạo đơn hàng mới
OrderSys -> Warehouse: Kiểm tra tồn kho
Warehouse --> OrderSys: Kết quả tồn kho
OrderSys --> Web: Trạng thái đặt hàng
Web --> KháchHàng: Hiển thị kết quả
@enduml
```


### Gửi và Nhận Tin Nhắn

```plantuml
@startuml
entity "Người Gửi" as Sender
entity "Server" as Server
entity "Người Nhận" as Receiver

Sender -> Server: Gửi tin nhắn
activate Server
Server -> Receiver: Chuyển tin nhắn
activate Receiver
Receiver --> Server: Xác nhận nhận được
deactivate Receiver
Server --> Sender: Xác nhận đã gửi
deactivate Server
@enduml
```
