# I. BIỂU THỨC LAMDA #
## 1. Lambda là gì? ##
- Lambda = một hàm nhỏ không tên, hay còn gọi là hàm ẩn danh.
- Mục đích: truyền hành động như dữ liệu, ví dụ: "so sánh 2 số", "in ra 1 giá trị", "tính tổng" mà không cần tạo hẳn một class hay method mới.

## 2. Cấu trúc cơ bản ##
	(tham số) -> hành động / giá trị trả về
- Tham số (trái ->): cái bạn đưa vào
- Thân lambda (phải ->): hành động hoặc giá trị trả về
- Ví dụ: x -> x * 2. Nhận x, trả về x * 2

## 3. Cách đọc lambda ##
- (a, b) -> a + b => "Nhận a và b, trả về tổng a + b"
- () -> System.out.println("Hello") => “Không nhận gì, chỉ in Hello”
- Tip: Mỗi lần thử lambda, tự hỏi:
  - Tham số là gì?
  - Hành động là gì?
  - Kết quả trả về là gì?

## 4. Lambda liên quan gì đến functional interface? ##
- Là Interface chỉ có duy nhất một phương thức trừu tượng (abstract method)
- Lambda luôn gắn với interface chỉ có 1 phương thức trừu tượng (ví dụ: Runnable, Comparator, Predicate)
- Nó là cách viết ngắn gọn của class ẩn danh.

## 5. Vậy lamda có được sử dụng, ứng dụng nhiều trong tương lai hay không? ##
- Có, chắc chắn là rất rộng rãi và thường xuyên sử dụng, và lý do là lambda giúp code ngắn gọn, rõ ràng, dễ kết hợp với các API hiện đại.
- Từ Java 8 trở đi, lambda xuất hiện cùng Stream API => làm việc với Collection cực mạnh: lọc, map, sắp xếp, tính toán…
- Ví dụ: sắp xếp danh sách, tính tổng, lọc dữ liệu, thao tác đồng thời (parallel) =>s lambda là chuẩn mực hiện nay.
- Hầu hết thư viện hiện đại đều hỗ trợ lambda hoặc functional interface => Sẽ gặp nó nhiều trong dự án thực tế
- Các ứng dụng thực tế:
  + Sắp xếp, lọc, map, reduce danh sách trong app
  + Event handling / callback trong GUI hoặc web
  + Xử lý dữ liệu song song (parallel streams)
  + Kết hợp với API hiện đại: Stream, CompletableFuture, RxJava…
- Tóm lại: nắm vững lambda là kỹ năng bắt buộc nếu muốn code Java hiện đại, vì hầu hết code “chuyên nghiệp” và các thư viện mới đều sử dụng nó.

## 6. Con đường học Lambda – Stream – Collection ##
```
[1] Lambda cơ bản
   |
   |-- Nhìn như "hàm thu nhỏ"
   |-- Cú pháp: (tham số) -> hành động
   |-- Ví dụ: x -> x*2, (a,b)->a+b
   |
[2] Lambda + Collection cơ bản
   |
   |-- Sử dụng với sort, forEach
   |-- Ví dụ: list.sort((a,b)->a.length()-b.length())
   |-- Mục tiêu: thực hành lambda trực tiếp, không Stream
   |
[3] Stream API cơ bản
   |
   |-- filter, map, forEach
   |-- Lambda làm tham số cho từng phần tử
   |-- Ví dụ: list.stream().filter(x->x%2==0).forEach(System.out::println)
   |
[4] Stream nâng cao
   |
   |-- sorted, distinct, reduce, collect
   |-- Kết hợp nhiều thao tác liên tiếp
   |
[5] Lambda + Parallel / Async
   |
   |-- ParallelStream, CompletableFuture
   |-- Dùng lambda xử lý dữ liệu song song
   |
[6] Lambda trong thư viện hiện đại
   |
   |-- RxJava, Spring, GUI events
   |-- Lambda + functional interface, callback
```
- Ý tưởng chính
  - Lambda = nền tảng
  - Stream + Collection = cách áp dụng lambda xử lý dữ liệu tập hợp
  - Parallel / Async = nâng cao, vẫn dùng lambda
  - Thư viện hiện đại = mọi nơi bạn sẽ gặp lambda

# II. FUNCTIONAL INTERFACE #
## 1. Functional interface là gì? ##
- Là interface chỉ có 1 phương thức trừu tượng (abstract method)
- Lambda sẽ "thay thế" phương thức này
- Có thể có default hoặc static method, vẫn hợp lệ

## 2. Một số functional interface chuẩn hay dùng ##
- Runnable – không tham số, không trả về
- Ý nghĩa: Lambda sẽ làm một hành động, không nhận tham số, không trả về gì.
```
public static void main(String[] args) {
        Runnable r = () -> System.out.println("Hello Lambda!");
        r.run(); // in ra: Hello Lambda!
}
```
