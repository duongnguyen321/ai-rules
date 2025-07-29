# Hướng dẫn sử dụng claude code + Tool PRPs

## PRPs là gì?

> Product Requirement Prompt (PRP) Framework

PRPs được hiểu đơn giản là một file markdown tổng hợp toàn bộ kiến thức cần thiết cho AI(`claude code`) để hoàn thành dự án(`hoặc một task`)

## Cấu trúc của PRPs

Cấu trúc của một PRPs sẽ bao gồm:

- Phân tích nghiệp vụ dự án(`BA docs`)
- Phân tích công nghệ sử dụng và hướng dẫn code(`DEV docs`)
- Cấu trúc dự án(`Source map`)
- Ref, rules, code styles, link figma, style design,... của dự án
- Task todo list

## Tại sao phải cần PRPs

- Không hiểu rõ nghiệp vụ giữa Dev-BA-Design?
- Không hiểu rõ cấu trúc dự án?
- Cần một format chung trong code giúp cả team làm cùng nhau tốt hơn?
- BA và PM cần theo dõi và hiểu tổng quan về dự án?
- Sử dụng AI trong code dự án, tuy nhiên code linh tinh hoặc không follow chặt chẽ vì thiếu context?
- Tiết kiệm context khi AI scan toàn bộ dự án và vibe code dễ dàng hơn(đặc biệt là `claude code` rất đắt)

## Hướng dẫn cài đặt và sử dụng

1. Cài đặt `claude code`

```bash
npm i -g @anthropic-ai/claude-code
```

2. Đăng ký tài khoản(`PRO`) trên claude và đăng nhập `claude code` trong terminal

3. Mở dự án cần làm trong terminal

```bash
cd <path-to-project>
```

4. Copy folder `.claude` trong source này, paste vào root của dự án

5. Tuy `claude code` có thể chạy riêng biệt hoàn toàn. Nhưng nên kết hợp thêm các MCP sau để giúp hỗ trợ tốt hơn trong dự án:

```bash
claude mcp add serena -- uvx --from git+https://github.com/oraios/serena serena-mcp-server --context ide-assistant --project $(pwd)
```

```bash
claude mcp add context7 -- bunx -y @upstash/context7-mcp
```

```bash
claude mcp add figma -- bunx -y figma-developer-mcp --figma-api-key=<GITHUB_API_KEY> --stdio
```

6. Mở `claude code` dự án

6.1 Nếu dự án đã có code:

```bash
claude "Onboard/init MCP Serena as resource for semantic code edits. Use MCP Context7 to research source code: analyze patterns, deps, bugs; suggest fixes."
```

> Sau khi chạy, `claude code` sẽ xin phép sử dụng command, cứ chọn dont ask again(dòng yes thứ 2)

6.2 Nếu dự án chưa có code thì **Bắt buộc phải init dự án trước bằng command bình thường** sau đó chạy command **6.1**

7. Sau khi init xong dự án, ở nguyên trong terminal `claude code` và chạy command sau:

```bash
/generate-prp [feature-name]
```

Với `[feature-name]` là mô tả đầy đủ và kỹ càng nhất có thể về:

- Mô tả về tính năng nếu đang phát triển tính năng mới
- Mô tả về toàn bộ dự án nếu bắt đầu phát triển dự án mới

8. Sau khi chạy command, `claude code` sẽ gửi một list câu hỏi, cần trả lời chúng.

Cần trả lời trong duy nhất một lần trả lời. Có thể viết ra một tab khác rồi copy vào cho dễ.

- Cần phải define `RÕ RÀNG` từng tính năng, từng case của tính năng đó.

- Cần phải định nghĩa rõ ràng về framework, ngôn ngữ, code convention sử dụng.

- Nên giải thích rõ ràng về cấu trúc source code dự án giúp việc cấu trúc code rõ ràng hơn.

- Nếu có các rules, ref, code styles, link figma, style design,... của dự án, cần gửi thêm.

- Nếu có task todo list, cần gửi thêm.

- Nếu có các tài liệu liên quan, cần gửi thêm.

9. Sau khi trả lời xong, `claude code` sẽ tự động tạo ra file `/PRPs/{ten_feat}.md`

Cần phải đọc, review lại, sửa lại nếu cần thiết.

10. Sau khi hoàn thiện quá trình sửa, compare giữa BA+Tech Lead+Design Lead+PM để đảm bảo đã đủ context và đầy đủ. Chạy command sau trong claude code

```bash
/execute-prp [prp-name]
```

Với `[prp-name]` là tên của file PRP cần execute. Có thể không có, nếu không có thì sẽ làm toàn bộ.

> Kể cả có cung cấp tên file hay không, thì AI vẫn đọc context toàn bộ các file prp để đảm bảo follow dự án tốt hơn. Vì thế không cần lo về việc có thể tiếp tục không.

11. Đợi... Sửa lại UI hoặc bất cứ thứ gì cần sửa

> AI không code hết được toàn bộ, tuy nhiên có thể tiết kiệm thời gian+công sức ~50% :v

## Hướng dẫn sử dụng claude code tốt hơn

- Vì context size của claude không dài như `gpt-4` hay `gemini-2.5` nên cần phải tóm tắt context bằng cách sử dụng command sau nếu dưới 15% `auto-compact` (Khi sử dụng sẽ hiểu cái này)

```bash
/compact
```

- Khi cần làm gì đó, hãy thêm `plan todo`, để `claude code` tạo todo trước khi code, giúp nó code tốt hơn và không miss nhiệm vụ

- [Xem video này](https://www.youtube.com/watch?v=TiNpzxoBPz0)
