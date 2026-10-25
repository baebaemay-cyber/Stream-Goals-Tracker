# Stream Goals Tracker

เว็บติดตามภารกิจสตรีมแบบ static (ไม่ต้องมีเซิร์ฟเวอร์) ใช้กับ GitHub Pages ได้เลย

## ไฟล์
- `index.html` – หน้าเว็บ
- `config.js` – เวลาเริ่ม/จำนวนชั่วโมง และ (ถ้าต้องการ) YouTube API key
- `data.json` – เป้าหมาย ยอดปัจจุบัน และลิงก์ของแต่ละภารกิจ

## ขึ้น GitHub Pages
1. สร้าง repository ใหม่ แล้วอัปโหลดไฟล์ทั้งหมด
2. Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / `(root)` → Save
3. รอ 1–2 นาที เว็บจะอยู่ที่ `https://<username>.github.io/<repo>/`

## อัปเดตยอด
แก้ `current` (และ `updated` เช่น `"23:00"`) ใน `data.json` แล้ว commit
(แก้ผ่านหน้าเว็บ GitHub ได้เลย: เปิดไฟล์ → ไอคอนดินสอ → Commit changes)
หน้าเว็บโหลดข้อมูลใหม่ทุก 60 วินาที แต่ GitHub Pages อาจใช้เวลา 1–2 นาทีหลัง commit

Spotify และ Melon ไม่มี API สาธารณะสำหรับยอดสตรีม จึงต้องอัปเดตด้วยมือ

## ดึงยอด YouTube อัตโนมัติ (ไม่บังคับ)
1. สร้าง API key ใน Google Cloud Console (เปิด YouTube Data API v3)
2. จำกัดคีย์ที่ *HTTP referrers* เป็นโดเมนเว็บของคุณ (`https://<username>.github.io/*`) และจำกัด API เหลือแค่ YouTube Data API v3
3. ใส่คีย์ใน `config.js` → `YT_API_KEY`

คีย์จะมองเห็นได้ในโค้ดหน้าเว็บ จึงต้องจำกัด referrer ตามข้อ 2 เสมอ

## ดูตัวอย่างในเครื่อง
`python3 -m http.server` แล้วเปิด http://localhost:8000
