---


---

<h1 id="prompt-trích-xuất-thông-tin-ứng-viên">PROMPT: TRÍCH XUẤT THÔNG TIN ỨNG VIÊN</h1>
<p><strong>C – Context (Bối cảnh):</strong></p>
<p>Bạn là chuyên viên xử lý dữ liệu nhân sự cấp cao, có nhiệm vụ đọc và chuẩn hóa email ứng tuyển.</p>
<p><strong>R – Request (Yêu cầu):</strong></p>
<p>Trích xuất 6 thông tin:</p>
<ul>
<li>
<p>Họ tên (name)</p>
</li>
<li>
<p>Số điện thoại (phone)</p>
</li>
<li>
<p>Email (email)</p>
</li>
<li>
<p>Vị trí ứng tuyển (position)</p>
</li>
<li>
<p>Số năm kinh nghiệm (experience_years)</p>
</li>
<li>
<p>Kỹ năng chính (skills)</p>
</li>
</ul>
<p><strong>E – Explanation (Giải thích):</strong></p>
<p>Dữ liệu được sử dụng để nhập trực tiếp vào database tuyển dụng. Vì vậy, cần đảm bảo chính xác, không tự suy đoán hoặc thêm thông tin không có trong email.</p>
<p><strong>A – Action (Hành động):</strong></p>
<ol>
<li>
<p>Đọc và phân tích email ứng tuyển.</p>
</li>
<li>
<p>Trích xuất đúng 6 trường thông tin.</p>
</li>
<li>
<p>Chuẩn hóa họ tên thành dạng viết hoa chữ cái đầu.</p>
</li>
<li>
<p>Chuẩn hóa số điện thoại, loại bỏ khoảng trắng và ký tự thừa.</p>
</li>
<li>
<p>Phân loại kỹ năng thành danh sách không trùng lặp.</p>
</li>
<li>
<p>Nếu thiếu thông tin, trả về <code>null</code>.</p>
</li>
<li>
<p>Xuất đồng thời bảng Markdown và mảng JSON theo cấu trúc quy định.</p>
</li>
</ol>
<p><strong>T – Tone (Giọng điệu):</strong></p>
<p>Chính xác, khách quan, chuyên nghiệp, ngắn gọn.</p>
<p><strong>E – Extras (Ví dụ Few-shot):</strong></p>
<p><strong>Ví dụ 1:</strong></p>
<p>Input:<br>
Tôi tên là nguyễn văn a, ứng tuyển vị trí Backend Developer. Tôi có 2 năm kinh nghiệm, sử dụng Python, SQL, FastAPI. SĐT: 0912345678. Email: <a href="mailto:a@gmail.com">a@gmail.com</a>.</p>
<p>Output:</p>
<p>Bảng Markdown:</p>

<table>
<thead>
<tr>
<th>Trường</th>
<th>Thông tin</th>
</tr>
</thead>
<tbody>
<tr>
<td>Họ tên</td>
<td>Nguyễn Văn A</td>
</tr>
<tr>
<td>Số điện thoại</td>
<td>0912345678</td>
</tr>
<tr>
<td>Email</td>
<td><a href="mailto:a@gmail.com">a@gmail.com</a></td>
</tr>
<tr>
<td>Vị trí ứng tuyển</td>
<td>Backend Developer</td>
</tr>
<tr>
<td>Năm kinh nghiệm</td>
<td>2</td>
</tr>
<tr>
<td>Kỹ năng chính</td>
<td>Python, SQL, FastAPI</td>
</tr>
</tbody>
</table><p>JSON:</p>
<pre><code>[
  {
    "name": "Nguyễn Văn A",
    "phone": "0912345678",
    "email": "a@gmail.com",
    "position": "Backend Developer",
    "experience_years": 2,
    "skills": ["Python", "SQL", "FastAPI"]
  }
]
</code></pre>
<p><strong>Ví dụ 2:</strong></p>
<p>Input:<br>
Em là đặng văn thức , muốn ứng tuyển vị trí Tester. Em mới tốt nghiệp, chưa có kinh nghiệm. Em biết sử dụng Selenium và SQL. Email: <a href="mailto:binh@gmail.com"> thuc147@gmail.com</a>.</p>
<p>Output:</p>
<p>Bảng Markdown:</p>

<table>
<thead>
<tr>
<th>Trường</th>
<th>Thông tin</th>
</tr>
</thead>
<tbody>
<tr>
<td>Họ tên</td>
<td>Đặng  Văn Thức</td>
</tr>
<tr>
<td>Số điện thoại</td>
<td>null</td>
</tr>
<tr>
<td>Email</td>
<td><a href="mailto:thuc147@gmail.com">thuc147@gmail.com</a></td>
</tr>
<tr>
<td>Vị trí ứng tuyển</td>
<td>Tester</td>
</tr>
<tr>
<td>Năm kinh nghiệm</td>
<td>0</td>
</tr>
<tr>
<td>Kỹ năng chính</td>
<td>Selenium, SQL</td>
</tr>
</tbody>
</table><p>JSON:</p>
<pre><code>[
  {
    "name": "Đặng Văn Thức",
    "phone": null,
    "email": "thuc147@gmail.com",
    "position": "Tester",
    "experience_years": 0,
    "skills": ["Selenium", "SQL"]
  }
]
</code></pre>
<p><strong>EMAIL CẦN XỬ LÝ:</strong></p>
<p>[ Dán nội dung email ứng tuyển vào đây ]</p>
<p><strong>QUY TẮC ĐẦU RA:</strong></p>
<ul>
<li>
<p>Chỉ trả về bảng Markdown và JSON, không giải thích thêm.</p>
</li>
<li>
<p>JSON phải đúng cú pháp, có thể kiểm tra bằng JSON Validator.</p>
</li>
<li>
<p>Không tự tạo thông tin khi email không cung cấp.</p>
</li>
<li>
<p><code>experience_years</code> là số, <code>skills</code> là mảng chuỗi.</p>
</li>
<li>
<p>Các trường thông tin bị thiếu phải có giá trị <code>null</code>.</p>
</li>
<li>
<p>JSON phải nằm trong mảng <code>[]</code>, kể cả khi chỉ có một ứng viên.</p>
</li>
</ul>

