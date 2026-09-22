# IT-shadowing

Trang luyện shadowing tiếng Nhật cho developer làm dự án hệ thống bệnh viện và đơn thuốc
(電子カルテ・処方箋システム). Một file HTML tĩnh, chạy offline, không cần cài gì.

**Bản deploy:** https://nkocvodoi.github.io/IT-Shadowing/

## Cách luyện

1. Bấm một câu bất kỳ để nghe riêng câu đó.
2. Bấm **Chạy shadowing**: máy đọc từng câu, rồi chừa một khoảng lặng đúng bằng độ dài câu —
   bạn nói đè lên khoảng lặng đó.
3. Vòng 1 nghe không nói, vòng 2 nói nhỏ theo cùng lúc, vòng 3 tắt romaji và nghĩa tiếng Việt
   rồi nói lại từ trí nhớ.

Mỗi câu có ba dòng: tiếng Nhật, **romaji**, nghĩa tiếng Việt. Hai nút `Romaji` và `Nghĩa Việt`
bật/tắt độc lập; lựa chọn được nhớ trong trình duyệt.

Phím tắt: `Space` chạy/dừng · `R` nghe lại câu hiện tại · `B` bật tắt romaji · `V` bật tắt nghĩa.

## Nội dung

| Mục | Khung câu |
| --- | --- |
| ① | 結論 → 理由 → 提案 |
| ② | 問題 → 原因 → 影響 → 対応 |
| ③ | Xác nhận yêu cầu, hỏi khi chưa hiểu |
| ④ | Đề xuất mềm mại: 理由 → 提案 → 効果 |
| ⑤ | Phản đối lịch sự: 共感 → 反対 → 理由 → 提案 |
| ⑥ | Đổi cách nói theo người nghe (エンジニア・営業・病院様) |
| ⑦ | Hội thoại 1-1 và câu cứu nguy khi bí |

## Giọng đọc

Trang dùng Web Speech API của trình duyệt, cần một giọng tiếng Nhật cài sẵn trong máy:

- macOS / iOS: đã có sẵn (Kyoko, Otoya).
- Windows: Settings → Time & language → Language → thêm 日本語 và tải gói Speech.
- Android: cài Google 音声サービス.
- Chrome trên Linux thường không có giọng ja-JP; dùng Edge hoặc Safari.

Nếu không tìm thấy giọng nào, trang sẽ hiện cảnh báo ở đầu và vẫn cho đọc câu bằng mắt.

## Chạy tại máy

Mở thẳng `index.html` bằng trình duyệt, hoặc:

```
python3 -m http.server 8000
```

## Deploy

GitHub Pages lấy thẳng từ nhánh: Settings → Pages → Source **Deploy from a branch**, chọn `main`
và thư mục `/ (root)`. Mỗi lần push vào `main` là GitHub tự build lại, không cần Actions.
File `.nojekyll` để Jekyll khỏi đụng vào nội dung.

## Thêm hoặc sửa câu

Toàn bộ nội dung nằm trong mảng `SETS` ở cuối `index.html`:

```js
{r:"結論", ja:"...", ro:"...", vi:"..."}   // một câu
{g:"Tên tình huống"}                        // dòng ngăn nhóm, không đọc
```

Với số và từ viết tắt, viết cách đọc bằng katakana (`シーアイ・シーディー`, `五百エラー`)
để máy đọc đúng, rồi ghi romaji theo đúng cách đọc đó.
