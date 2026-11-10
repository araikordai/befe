# PLAYLOG — live game ratings

แคตตาล็อกมีเกม 100 เกม คะแนนเฉลี่ยและจำนวนโหวตมาจากคะแนนจริงใน Supabase เท่านั้น เกมที่ยังไม่มีคนโหวตจะแสดงว่าไม่มีคะแนน ระบบไม่ใส่คะแนนตัวอย่าง

## ไฟล์หลัก
- `frontend/` เว็บไซต์
- `backend/server.js` API สำหรับ Render
- `data/games.json` ข้อมูลแคตตาล็อก 100 เกม
- `supabase/migrations/` โครงสร้างฐานข้อมูลและระบบสมาชิก
- `supabase/seed.sql` ข้อมูลเกม 100 รายการ โดยไม่มีคะแนนหรือรีวิวตัวอย่าง
- `render.yaml` ตั้งค่า Render

## เพิ่มแคตตาล็อก 100 เกมใน Supabase
1. เปิด SQL Editor ของ Supabase
2. รัน `supabase/migrations/20261110000100_playlog_ratings.sql`
3. รัน `supabase/seed.sql`

`supabase/seed.sql` ใช้เพิ่มหรืออัปเดตข้อมูลเกมตามรหัส โดยไม่แตะคะแนนโหวตของสมาชิก

## สร้างไฟล์ seed ใหม่
แก้ `data/games.json` แล้วรัน `npm run seed:sql` เพื่อสร้าง `supabase/seed.sql`

## การเชื่อมต่อบริการ
- Render: สร้าง Web Service จาก `render.yaml` แล้วตั้ง `SUPABASE_URL` และ `SUPABASE_ANON_KEY`
- Vercel: ตั้ง `RENDER_API_URL` เป็น URL ของบริการ Render
- Supabase Auth: เปิดการสมัครและเข้าสู่ระบบด้วยอีเมล/รหัสผ่าน และตั้ง Site URL กับ redirect URL ของเว็บ

อย่าใช้ service-role key ใน frontend หรือส่งขึ้น Git

## ใช้งานในเครื่อง
คัดลอก `.env.example` เป็น `.env` ใส่ค่าการเชื่อมต่อ แล้วรัน:

```bash
npm install
npm start
```
