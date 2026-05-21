# Boutikhomes Workspace Portal

เว็บหน้าหลักสำหรับ Boutikhomes ใช้เป็น dashboard กลางให้ทีมเลือกฝ่ายและเข้าระบบต่าง ๆ

## สรุปคำตอบเรื่อง Apps Script

หน้าแรกนี้ **ยังไม่ต้องใช้ Google Apps Script** เพราะเป็นแค่ portal/static website:

- เปิดบน GitHub Pages ได้ทันที
- ไม่ต้อง login Google
- ไม่อ่านหรือบันทึกข้อมูล
- ใช้เป็นหน้ารวมลิงก์ไปแต่ละระบบ

ควรใช้ Apps Script เฉพาะระบบที่ต้อง:

- บันทึก Lead / Walk-in ลง Google Sheet
- อ่านข้อมูลจาก Google Sheet
- ตรวจสิทธิ์จากอีเมล Google
- จัดการ permission ที่ต้องปลอดภัยจริง

## โครงไฟล์

- `index.html` - หน้าเว็บหลักสำหรับ GitHub Pages
- `.nojekyll` - ให้ GitHub Pages serve static file ตรง ๆ
- `.gitignore` - กันไฟล์ระบบที่ไม่ควรขึ้น repo

## วิธีสร้าง Repo ตั้งแต่ต้น

1. เข้า GitHub แล้วกด New repository
2. ตั้งชื่อ เช่น `Boutikhomes-Workspace`
3. เลือก Public ถ้าจะใช้ GitHub Pages ฟรี
4. อัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ขึ้น repo
5. ไปที่ Settings → Pages
6. Source: `Deploy from a branch`
7. Branch: `main`
8. Folder: `/root`
9. กด Save

หลังจาก GitHub Pages build เสร็จ URL จะประมาณนี้:

```text
https://boutikhomes.github.io/Boutikhomes-Workspace/
```

## จุดที่ต้องแก้ภายหลัง

ใน `index.html` ตอนนี้ลิงก์ของแต่ละฝ่ายยังเป็น placeholder เช่น `#sales`, `#marketing`, `#management`

เมื่อมี URL จริงแล้วให้แก้ในส่วนการ์ด:

```html
<a class="dept" href="https://script.google.com/macros/s/.../exec">
```

ตัวอย่างการวางระบบ:

- หน้า portal หลัก: GitHub Pages
- Sales CRM: Google Apps Script Web App หรือ backend ที่เขียนข้อมูลลง Sheet
- Marketing Dashboard: GitHub Pages ถ้าเป็น static, Apps Script ถ้าต้องล็อกสิทธิ์รายอีเมล
- Permission Admin: Apps Script หรือ backend เท่านั้น ไม่ควรทำบน static GitHub Pages ล้วน ๆ

## Recommended Next Step

เริ่มจาก push portal นี้ขึ้น GitHub Pages ก่อน แล้วค่อยเพิ่มลิงก์จริงทีละระบบเมื่อ deploy เสร็จ
