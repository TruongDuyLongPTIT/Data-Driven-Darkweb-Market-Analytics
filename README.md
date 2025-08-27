# Data-Driven-Darkweb-Market-Analytics
- **Dữ liệu nguồn: Darknet Market Archives 2013-2015 (dnmarchives)**
  + **Giới thiệu bộ dữ liệu sử dụng:**

    Bộ dữ liệu Darknet Market Archives 2013–2015 (dnmarchives) là một tập hợp lớn các bản sao (mirrors) từ các chợ đen (darknet markets) và diễn đàn liên quan trên mạng Tor. Nó bao gồm khoảng 4,438 mirrors và hơn 43,596,420 file, với kích thước nén khoảng 50GB (giải nén lên đến 1.6TB). Bộ dữ liệu này tập trung vào các hoạt động từ năm 2011 đến 2015 (chủ yếu 2013–2015), chứa dữ liệu từ 89 chợ đen, hơn 37 diễn đàn, và khoảng 5 trang web hỗ trợ khác. Nội dung chủ yếu là dữ liệu thô để nghiên cứu về hệ sinh thái darknet, tội phạm mạng, và kinh tế ngầm.

    + Ví dụ, đây là 1 trang web bán Cần sa (Cannabis) trên 1 chợ đen (tên là Silk Road): [HASHSI~1.HTM](https://github.com/user-attachments/files/22004752/HASHSI.1.HTM)
          <img width="1899" height="1013" alt="image" src="https://github.com/user-attachments/assets/c4f7afd7-8e23-43fc-9dca-9bb062c7ccba" />

  + **Cấu trúc bộ dữ liệu (gồm 3 nhóm chính):**
    + **Markets (89 chợ đen):**
      + Mô tả: Chứa bản sao của các chợ đen, bao gồm listings sản phẩm, giá cả, phản hồi, và hình ảnh.
      + Cấu trúc: Các file .tar.xz theo tên chợ, chứa thư mục con theo ngày crawl (YYYY-MM-DD).
      + Nội dung mẫu:
        + Listings sản phẩm (HTML): Mô tả, giá (thường bằng Bitcoin), và phản hồi người dùng.
        + Hình ảnh: Ảnh sản phẩm, chiếm phần lớn dung lượng.
        + Ví dụ file: agora.tar.xz (~5.87GB) chứa thư mục 2014-04-21-whom-astorposts/ với HTML, CSS, và hình ảnh từ chợ Agora.
        + Số lượng file liên quan: Khoảng 100 file, chiếm phần lớn kích thước.
    
    + **Forums (>37 diễn đàn):**
      + Mô tả: Chứa bản sao của các diễn đàn liên quan đến chợ đen, bao gồm threads, posts, và comments.
      + Cấu trúc: File .tar.xz theo tên diễn đàn, chứa thư mục con theo ngày crawl, với HTML và đôi khi SQL dumps.
      + Nội dung mẫu:
        + Threads và comments (HTML): Thảo luận về giao dịch, sản phẩm, và phản hồi.
        + SQL dumps: Dữ liệu cơ sở dữ liệu (posts, comments, users).
        + Ví dụ file: silkroad1-forums-20130703-anonymous.tar.xz (~11.72MB) chứa thư mục con với HTML của diễn đàn Silk Road 1; 2017-03-10-decaryhetu-sr1forumscrape.sql.xz chứa SQL dump từ diễn đàn Silk Road 1.
        + Số lượng file liên quan: Khoảng 50 file, chiếm khoảng 20-30% dung lượng.
    
    + **Miscellaneous (~5 trang web và file hỗ trợ):**
      + Mô tả: Các trang web hỗ trợ hoặc dữ liệu bổ sung, như công cụ tìm kiếm darknet hoặc thống kê.
      + Cấu trúc: File .tar.xz chứa CSV, SQL, hoặc HTML.
      + Nội dung mẫu:
        + CSV exports: Listings và feedback từ chợ (từ Grams).
        + SQL dumps: Dữ liệu thống kê (từ DNStats).
        + File khác: Documents, MP3, OGG, SQLite metadata.
        + Ví dụ file: grams-2014-06-09-to-2016-04-17-daily-csv-exports.tar.xz (~1.32MB–5.87GB) chứa CSV từ Grams; 2017-03-25-dnstats.sql.xz (~110.85MB) chứa SQL dump từ DNStats; dnmarchives_meta.sqlite chứa metadata bộ dữ liệu.
        + Số lượng file liên quan: Khoảng 10-15 file, chiếm phần nhỏ dung lượng.

  + **Lý do chọn bộ dữ liệu này:**
      + Dữ liệu khá lớn, toàn bộ tập dữ liệu kích thước 52GB (khi nén), khi giải nén thì kích thước khoảng 1.6TB => **Đủ lớn để luyện tập tối ưu khi xử lý Bigdata**
      + Dữ liệu lấy từ nhiều nguồn (89+ chợ đen, 37+ diễn đàn, và 1 số trang web và công cụ khác) nên tính bất đồng bộ cao => **Luyện tập chuẩn hóa dữ liệu để đạt được sự nhất quán.**
      + Dữ liệu định dạng cực kỳ đa dạng: .csv, .xlsx, .html, .sql, .txt, .docx, .sav, dữ liệu comment/replies trong các forums, dữ liệu dạng ảnh... => **Học cách xử lý dữ liệu có định dạng phong phú và có cấu trúc cực kỳ phức tạp.**
      + Chủ đề thú vị, ít gặp. Có giá trị cho phân tích và phục vụ cho một số nghiêp vụ và các nghiên cứu hoạt động tội phạm trong thực tế.
        
  + **Nhược điểm khi chọn bộ dữ liệu này:**
      + Bộ dữ liệu này kết thúc thu thập vào 2015 và các darkweb này cũng đã bị đánh sập => Nên không còn rèn được kỹ năng crawl dữ liệu từ nguồn.
      + Không có dữ liệu mới sinh ra => Không xử lý real-time hay lập lịch xử lý batch được (Project này chỉ xử lý cả bộ dữ liệu trong 1 lần).
      + Không có hoạt động sửa/xóa dữ liệu => Không luyện tập được các kỹ năng cập nhật sự thay đổi của dữ liệu và dữ liệu cũng ít có tính lịch sử (dữ liệu không có nhiều phiên bản thay đổi, không có các version snapshot để lưu lịch sử thay đổi).
        
- **Mục đích:**
    + Đưa ra số liệu thống kê về tình hình buôn bán chất cấm, vũ khí, mã độc,... và các giao dịch phạm pháp khác.
    + Phục vụ cho phân tích, nghiên cứu hành vi của tội phạm từ đó có thể đưa ra hành động triệt phá, chặn bắt.
    + Phân tích đồ thị mạng lưới tội phạm (Ai mua, ai bán, mua bán cái gì) - cố gắng làm nếu đủ khả năng.
    + **Luyện tập khả năng xử lý dữ liệu thế giới thực (đa nguồn, đa dạng, phức tạp).**
      
- **Danh sách báo cáo & thống kê:**
    + **Báo cáo/thống kê về market (tập trung làm trước):**
      + Phân tích hàng hóa/dịch vụ buôn bán: 
        + Thống kê loại sản phẩm phổ biến (ma túy, card tín dụng, tài khoản bị hack, vũ khí, malware, dịch vụ thuê hacker…).
        + Xu hướng thay đổi theo thời gian (ví dụ: khi một market sập thì mặt hàng nào tăng mạnh ở market khác).
          
      + Phân tích giá cả & xu hướng kinh tế ngầm:
        + Biểu đồ giá trung bình cho từng loại hàng hóa theo thời gian.
        + So sánh giá giữa các market khác nhau.
          
      + Phân tích người bán (vendors):
        + Phân phối vendor theo số lượng listing.
        + Phát hiện các vendor lớn, vendor “đa ngành”, vendor chuyên biệt.
          
      + Phân tích đánh giá/feedback:
        + Tỷ lệ review tích cực/tiêu cực của từng vendor, từng loại hàng.
          
     + **Báo cáo/phân tích về forums (phân tích các comment): Pending...**
        + Dữ liệu comment khá khó xử lý (Cần lọc, phân loại, sentiment analyst - phân tích cảm xúc comment)
        + Đã thử 1 số phương pháp như rule-based, các model pre-trained cho sentiment analyst nhưng vẫn khó để đạt được độ tin cậy cao, vì ngôn ngữ đa dạng, câu có hàm nghĩa, ẩn ý, cấu trúc câu phức tạp.
        + Test thấy mỗi phương pháp dùng LLM API (chatGPT, gemini) thì các LLM này hiểu ngữ cảnh và phân tích chính xác, nhưng tốc độ không nhanh và tốn tiền.
          
- **Kiến trúc luồng dữ liệu:**
- **Kỹ năng:**
