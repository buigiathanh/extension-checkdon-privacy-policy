# Chính sách quyền riêng tư — Shopee Check Đơn Hoàn (CheckDon)

**Ngày có hiệu lực:** 23/08/2026  
**Phiên bản áp dụng:** Extension “Shopee Check Đơn Hoàn” và dịch vụ API CheckDon liên quan

Chính sách này mô tả cách CheckDon thu thập, lưu trữ, sử dụng và bảo vệ thông tin khi bạn sử dụng tiện ích trình duyệt **Shopee Check Đơn Hoàn** (sau đây gọi là “Extension”) và máy chủ backend hỗ trợ Extension (sau đây gọi là “Dịch vụ”).

Bằng việc cài đặt Extension và/hoặc tạo tài khoản CheckDon, bạn xác nhận đã đọc và đồng ý với Chính sách này.

---

## 1. Chúng tôi là ai

CheckDon cung cấp Extension giúp người bán trên **Shopee Seller Center** (`banhang.shopee.vn`) xem nhanh số lượng / lịch sử đơn hoàn liên quan đến từng người mua khi đang quản lý đơn hàng.

Extension **không phải** sản phẩm của Shopee và **không** liên kết chính thức với Shopee. Shopee là thương hiệu của bên thứ ba.

---

## 2. Phạm vi áp dụng

Chính sách này áp dụng cho:

- Extension trình duyệt CheckDon (Manifest V3);
- Trang đăng nhập / đăng ký / danh sách đơn hoàn trong Extension;
- API CheckDon mà Extension gọi để xác thực và đồng bộ dữ liệu.

Chính sách **không** áp dụng cho trang Shopee, trình duyệt, hoặc dịch vụ bên thứ ba khác mà bạn truy cập độc lập.

---

## 3. Dữ liệu chúng tôi thu thập

### 3.1. Thông tin tài khoản CheckDon (do bạn cung cấp)

Khi đăng ký hoặc đăng nhập, chúng tôi thu thập:

| Dữ liệu | Mục đích |
|--------|----------|
| Họ tên | Hiển thị và quản lý tài khoản |
| Email | Đăng nhập, liên hệ hỗ trợ liên quan tài khoản |
| Số điện thoại | Định danh tài khoản, hỗ trợ |
| Mật khẩu | Xác thực đăng nhập |

**Lưu ý bảo mật mật khẩu:** mật khẩu được **băm (hash)** trước khi lưu trên máy chủ (không lưu mật khẩu dạng plaintext). Extension **không** lưu mật khẩu trên máy của bạn sau khi đăng nhập thành công.

### 3.2. Dữ liệu phiên đăng nhập (lưu trên thiết bị của bạn)

Sau khi đăng nhập thành công, Extension lưu cục bộ trong `chrome.storage.local`:

- Token xác thực (JWT);
- Thông tin người dùng công khai gắn với phiên (ví dụ: id, họ tên, email, số điện thoại);
- Thời điểm lưu phiên.

Dữ liệu này chỉ dùng để giữ trạng thái đăng nhập và gọi API CheckDon. Bạn có thể xóa bằng cách đăng xuất hoặc gỡ Extension / xóa dữ liệu site của Extension trong trình duyệt.

### 3.3. Dữ liệu cửa hàng Shopee (đồng bộ từ Seller Center)

Khi bạn đã đăng nhập CheckDon và đang dùng Shopee Seller Center, Extension có thể nhận và gửi lên máy chủ CheckDon thông tin cửa hàng lấy từ phản hồi API của Shopee trên trang bạn đang mở, bao gồm:

- Mã cửa hàng (`shop_id`);
- Tên người dùng / username cửa hàng;
- Ảnh đại diện cửa hàng (portrait / URL ảnh), nếu có.

Mục đích: liên kết tài khoản CheckDon với cửa hàng bạn đang quản lý để đồng bộ và hiển thị đúng ngữ cảnh.

### 3.4. Dữ liệu đơn hoàn / người mua (từ trang quản lý đơn Shopee)

Để hiển thị số đơn hoàn cạnh tên khách và lưu lịch sử phục vụ tính năng, Extension có thể thu thập và gửi lên máy chủ CheckDon các thông tin liên quan đơn hoàn / đơn hàng hiển thị trên Seller Center, ví dụ:

- Mã đơn nội bộ / mã đơn hiển thị (`order_id`, `order_sn`);
- Định danh người mua (`buyer_id`, `buyer_shop_id` nếu có);
- Tên / username người mua;
- Lý do yêu cầu hoàn hàng (`request_reason_text`) khi có trên danh sách đơn hoàn.

Dữ liệu này gắn với tài khoản CheckDon của bạn và được dùng để:

- Đếm / hiển thị số lần hoàn theo người mua trên giao diện Seller Center;
- Lưu và xem danh sách đơn hoàn gần đây trong Extension.

### 3.5. Dữ liệu chúng tôi **không** cố ý thu thập

Trong phạm vi thiết kế hiện tại, Extension **không**:

- Thu thập mật khẩu đăng nhập Shopee của bạn;
- Đọc hay gửi cookie đăng nhập Shopee sang máy chủ CheckDon;
- Theo dõi lịch sử duyệt web ngoài các trang khớp quyền đã khai báo (chủ yếu `banhang.shopee.vn` và máy chủ API CheckDon);
- Truy cập microphone, camera, vị trí, danh bạ hay tệp cá nhân ngoài nhu cầu của Extension;
- Bán dữ liệu cá nhân cho bên thứ ba vì mục đích quảng cáo.

Extension chỉ hoạt động trên trang Shopee Seller Center theo quyền `host_permissions` đã khai báo trong `manifest.json`, và dùng quyền `storage` để lưu phiên đăng nhập cục bộ.

---

## 4. Cách dữ liệu được thu thập

1. **Bạn nhập trực tiếp** khi đăng ký / đăng nhập CheckDon.  
2. **Extension lắng nghe phản hồi API** mà trình duyệt nhận khi bạn dùng Seller Center (ví dụ danh sách đơn, chi tiết đơn, danh sách đơn hoàn, thông tin đăng nhập cửa hàng), rồi gửi phần dữ liệu cần thiết lên API CheckDon khi bạn đã đăng nhập.  
3. **Máy chủ CheckDon** lưu dữ liệu tài khoản, cửa hàng và đơn hoàn để cung cấp tính năng.

Một số yêu cầu API nhạy cảm được bảo vệ thêm bằng mã hóa payload và chữ ký yêu cầu giữa Extension và máy chủ.

---

## 5. Mục đích sử dụng dữ liệu

Chúng tôi sử dụng dữ liệu để:

- Tạo và duy trì tài khoản CheckDon;
- Xác thực phiên đăng nhập và bảo vệ API;
- Đồng bộ cửa hàng và đơn hoàn phục vụ tính năng “check đơn hoàn”;
- Hiển thị thống kê / danh sách đơn hoàn trong Extension và trên giao diện Seller Center;
- Vận hành, khắc phục lỗi, cải thiện độ ổn định và bảo mật sản phẩm;
- Tuân thủ nghĩa vụ pháp lý khi được yêu cầu hợp pháp.

Chúng tôi **không** dùng dữ liệu của bạn để gửi quảng cáo của bên thứ ba, và **không** bán dữ liệu cá nhân.

---

## 6. Cơ sở xử lý / sự đồng ý

Bạn đồng ý cho phép xử lý dữ liệu khi:

- Tạo tài khoản và sử dụng Extension;
- Tiếp tục dùng Seller Center trong khi Extension đang bật và đã đăng nhập CheckDon (đồng bộ dữ liệu đơn / shop như mô tả ở trên).

Bạn có thể ngừng đồng bộ bằng cách đăng xuất CheckDon, tắt hoặc gỡ Extension.

---

## 7. Lưu trữ và bảo mật

- **Trên thiết bị:** token và hồ sơ phiên lưu trong bộ nhớ cục bộ của Extension (`chrome.storage.local`).  
- **Trên máy chủ:** tài khoản, cửa hàng và đơn hoàn lưu trên cơ sở dữ liệu của Dịch vụ CheckDon.  
- **Mật khẩu:** chỉ lưu dưới dạng hash.  
- **Truyền tải:** giao tiếp Extension ↔ API dùng HTTPS khi triển khai production; một số payload được mã hóa và ký thêm.  
- **Token:** có thời hạn; token hết hạn hoặc không hợp lệ sẽ bị xóa khỏi thiết bị và yêu cầu đăng nhập lại.

Dù chúng tôi áp dụng biện pháp bảo mật hợp lý, không hệ thống nào tuyệt đối an toàn. Bạn nên bảo vệ thiết bị, không chia sẻ tài khoản CheckDon, và đăng xuất khi dùng máy dùng chung.

---

## 8. Chia sẻ dữ liệu với bên thứ ba

Chúng tôi có thể chia sẻ dữ liệu chỉ trong các trường hợp sau:

- **Nhà cung cấp hạ tầng** (ví dụ hosting, cơ sở dữ liệu) khi cần để vận hành Dịch vụ, với nghĩa vụ bảo mật phù hợp;
- **Yêu cầu pháp lý** từ cơ quan có thẩm quyền theo luật áp dụng;
- **Bảo vệ quyền lợi hợp pháp** của CheckDon, người dùng hoặc công chúng khi cần thiết và hợp pháp.

Chúng tôi **không** chia sẻ dữ liệu đơn hàng / người mua của bạn với bên thứ ba để họ tự marketing.

Shopee có thể có chính sách riêng khi bạn dùng Seller Center; CheckDon không kiểm soát cách Shopee xử lý dữ liệu của họ.

---

## 9. Thời gian lưu giữ

- Dữ liệu tài khoản và dữ liệu nghiệp vụ (shop, đơn hoàn) được giữ trong thời gian tài khoản còn hoạt động và còn cần cho tính năng, trừ khi bạn yêu cầu xóa sớm hơn (trong phạm vi kỹ thuật khả thi).  
- Phiên cục bộ trên thiết bị được giữ đến khi bạn đăng xuất, xóa dữ liệu Extension, hoặc token hết hạn / bị thu hồi.  
- Có thể giữ bản sao tối thiểu khi luật yêu cầu hoặc để giải quyết tranh chấp.

---

## 10. Quyền của bạn

Tùy luật áp dụng (ví dụ pháp luật Việt Nam về bảo vệ dữ liệu cá nhân), bạn có thể yêu cầu:

- Được biết / truy cập dữ liệu cá nhân chúng tôi đang giữ về bạn;
- Chỉnh sửa thông tin tài khoản không chính xác;
- Xóa tài khoản hoặc dữ liệu liên quan (trong phạm vi kỹ thuật và pháp lý cho phép);
- Rút lại sự đồng ý bằng cách ngừng sử dụng và/hoặc yêu cầu xóa dữ liệu;
- Khiếu nại với cơ quan có thẩm quyền nếu bạn cho rằng quyền riêng tư bị xâm phạm.

Để thực hiện các quyền trên, hãy liên hệ theo mục **14. Liên hệ** bên dưới. Chúng tôi có thể yêu cầu xác minh danh tính trước khi xử lý.

**Tự quản lý trên thiết bị:**

- Đăng xuất khỏi CheckDon để xóa token cục bộ;
- Gỡ Extension hoặc xóa dữ liệu site của Extension trong trình duyệt.

---

## 11. Trẻ em

Extension hướng tới người bán / quản lý cửa hàng. Chúng tôi không cố ý thu thập dữ liệu của trẻ em dưới 16 tuổi. Nếu bạn cho rằng chúng tôi đã nhận dữ liệu của trẻ em ngoài ý muốn, hãy liên hệ để được xóa.

---

## 12. Chuyển dữ liệu xuyên biên giới

Máy chủ hoặc nhà cung cấp hạ tầng có thể đặt tại Việt Nam hoặc quốc gia khác. Khi dữ liệu được chuyển / lưu ngoài lãnh thổ nơi bạn cư trú, chúng tôi áp dụng biện pháp bảo vệ phù hợp với mục đích vận hành Dịch vụ và quy định áp dụng.

---

## 13. Thay đổi Chính sách

Chúng tôi có thể cập nhật Chính sách này khi sản phẩm hoặc pháp luật thay đổi. Ngày “có hiệu lực” ở đầu trang sẽ được cập nhật. Việc tiếp tục sử dụng Extension sau khi Chính sách mới được công bố được hiểu là bạn chấp nhận phiên bản cập nhật (trừ khi luật yêu cầu hình thức đồng ý khác).

Bản mới nhất được công bố tại tệp / trang Privacy Policy chính thức của CheckDon (URL công khai dùng khi đăng tải Extension lên cửa hàng trình duyệt).

---

## 14. Liên hệ

Nếu có câu hỏi về quyền riêng tư, yêu cầu truy cập / sửa / xóa dữ liệu, vui lòng liên hệ:

- **Sản phẩm:** Shopee Check Đơn Hoàn (CheckDon)  
- **Email hỗ trợ:** `[hotro@checkdon.com]`  

Chúng tôi sẽ phản hồi trong thời gian hợp lý.

---

## 15. Tóm tắt ngắn (dành cho cửa hàng ứng dụng)

| Hạng mục | Nội dung |
|----------|----------|
| Dữ liệu người dùng | Họ tên, email, SĐT, mật khẩu (đã hash) |
| Lưu cục bộ | Token đăng nhập + hồ sơ phiên |
| Dữ liệu từ Shopee Seller Center | Shop id/username/portrait; đơn hoàn & định danh người mua liên quan |
| Mục đích | Tài khoản CheckDon + hiển thị / lưu thống kê đơn hoàn |
| Quyền Extension | `storage`; truy cập `banhang.shopee.vn` và API CheckDon |
| Bán dữ liệu | Không |
| Theo dõi web ngoài phạm vi | Không cố ý |
