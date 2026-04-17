# Ask Mew Social - Openclaw Export



---

# สิ่งที่ต้องเตรียม

Source: https://ask.mewsocial.com/browse/openclaw/oc-setup/setup-checklist

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Setup
สิ่งที่ต้องเตรียม
สิ่งที่ต้องเตรียม
2 min
beginner
setup
checklist
1
สิ่งที่ต้องเตรียมก่อนเริ่ม Workshop

เตรียมของพร้อมก่อนเริ่ม จะได้ลื่นไหลไม่ต้องรอ!

Checklist
•

✅ Hostinger VPS — แนะนำ KVM2 ขึ้นไป (RAM 8GB)

•

✅ ChatGPT Plus Subscription ($20/เดือน) — ใช้ OAuth Login

•

✅ SSH Client — Terminal บน Mac หรือ Browser Terminal ของ Hostinger

•

✅ Telegram App — ติดตั้งบนมือถือ + คอมพิวเตอร์

•

✅ บัตรเครดิต/Debit — สำหรับสมัคร Hostinger VPS

⚠️

ไม่ต้องซื้อ Nexos AI Credits ตอน checkout — ข้ามไปได้เลย

⚠️

ไม่ต้องใส่ API Key ตอน checkout — ข้ามไปได้เลย

ทำไมต้อง ChatGPT Subscription?

OpenClaw ใช้ ChatGPT ผ่าน OAuth Login ซึ่งต้องมี subscription ถึงจะใช้ model ดีๆ ได้ ราคา $20/เดือน (~700 บาท) ใช้ได้ทั้งทีม!

ทางเลือกอื่น

ถ้าไม่อยากจ่าย subscription รายเดือน สามารถใช้ OpenAI API key แทนได้ (จ่ายตามใช้ ~$5-15/เดือน) หรือใช้ OpenRouter

NEXT IN LEARNING PATH

ซื้อ VPS + Deploy OpenClaw

Powered by Mew Social


---

# ซื้อ VPS + Deploy OpenClaw

Source: https://ask.mewsocial.com/browse/openclaw/oc-setup/setup-vps-deploy

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Setup
ซื้อ VPS + Deploy OpenClaw
ซื้อ VPS + Deploy OpenClaw
5 min
setup
vps
hostinger
deploy
1
Part 1 — ซื้อ VPS + Deploy OpenClaw

ขั้นตอนนี้ใช้เวลาประมาณ 5-10 นาที รวมรอ provision

Step 1: ซื้อ Hostinger VPS
1.

เปิดลิงก์ hostinger.com/vps/openclaw-hosting

1.

เลือกแพลน KVM2 ขึ้นไป (RAM 8GB แนะนำ)

1.

สร้างบัญชี / login

1.

ชำระเงิน

⚠️

⚠️ ไม่ต้องซื้อ Nexos AI Credits — ข้ามไปได้เลย

⚠️

⚠️ ไม่ต้องใส่ API Key ตอน checkout — ข้ามไปได้เลย

💡 เลือกแพลนยาวกว่าจะถูกกว่ารายเดือน

Step 2: จดข้อมูล Server

หลัง deploy เสร็จ เข้าที่ hPanel → VPS → Overview จดไว้:

•

Server IP (เช่น 187.127.98.204)

•

Root Password

•

Container Name (ดูจาก Docker Manager เช่น openclaw-j9zz-openclaw-1)

•

Gateway Token (ดูจาก Docker Manager → Manage → Environment → OPENCLAW_GATEWAY_TOKEN)

⚠️

Gateway Token = กุญแจเข้าระบบ — ห้ามทำหาย!

Step 3: ตั้ง VPS Password + Deploy
1.

ตั้ง VPS Password

1.

กด Deploy

1.

รอ Hostinger provision (~2-3 นาที)

1.

สถานะเปลี่ยนเป็น 'Running' = สำเร็จ!

NEXT IN LEARNING PATH

ตั้งค่า Auth ด้วย ChatGPT

Powered by Mew Social


---

# ตั้งค่า Auth ด้วย ChatGPT

Source: https://ask.mewsocial.com/browse/openclaw/oc-setup/setup-auth-chatgpt

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Setup
ตั้งค่า Auth ด้วย ChatGPT
ตั้งค่า Auth ด้วย ChatGPT
10 min
setup
auth
chatgpt
oauth
ssh
2
Part 2 — ตั้งค่า Auth ด้วย ChatGPT Subscription

ขั้นตอนนี้เชื่อม OpenClaw กับ ChatGPT account ของคุณผ่าน OAuth Login

Step 3: SSH เข้า VPS

เปิด Terminal (Mac) หรือ Browser Terminal ของ Hostinger:

TERMINAL
Copy
ssh root@YOUR_SERVER_IP

แทน YOUR_SERVER_IP ด้วย IP จริงของ VPS (เช่น 187.127.98.204)

💡

หรือใช้ Browser Terminal ของ Hostinger ได้เลย → hPanel → VPS → Browser terminal

Step 4: เข้าไปใน Container
TERMINAL
Copy
docker exec -it openclaw-j9zz-openclaw-1 sh
ℹ️

ชื่อ container อาจต่างกัน — ดูจาก docker ps ก่อนก็ได้

ถ้าไม่แน่ใจชื่อ container:

TERMINAL
Copy
docker ps

ดูคอลัมน์ NAMES จะเห็นชื่อเช่น openclaw-j9zz-openclaw-1

Step 5: รัน Configure + OAuth Login
TERMINAL
Copy
openclaw configure
1.

เลือก OpenAI เป็น provider

1.

เลือก Auth Login (OAuth)

1.

จะได้ URL แบบนี้:

TERMINAL
Copy
https://auth.openai.com/oauth/authorize?response_type=code&client_id=...
1.

Copy URL นี้ → เปิดใน browser บนคอมพิวเตอร์ของตัวเอง (ไม่ใช่บน VPS)

1.

Login ด้วย ChatGPT account ปกติ

1.

หลัง login จะ redirect ไปหน้า localhost:1455/auth/callback?code=...

⚠️

⚠️ หน้าจะ error — ไม่เป็นไร! Copy URL ทั้งหมดจาก address bar

ตัวอย่าง URL ที่ต้อง copy:

TERMINAL
Copy
http://localhost:1455/auth/callback?code=ac_xxxxx...xxxxx&scope=openid+profile+email+offline_access&state=xxxxx
1.

วาง URL ทั้งหมด ลงใน terminal ที่ขึ้น 'Paste the redirect URL'

1.

กด Enter → เลือก Models ที่ต้องการ → สำเร็จ!

Step 6: ออกจาก Container + Restart
TERMINAL
Copy
exit
TERMINAL
Copy
docker restart openclaw-j9zz-openclaw-1
💡

หลัง restart รอ 10-20 วินาทีก่อนใช้งาน

NEXT IN LEARNING PATH

เข้า Dashboard

Powered by Mew Social


---

# เข้า Dashboard

Source: https://ask.mewsocial.com/browse/openclaw/oc-setup/setup-dashboard

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Setup
เข้า Dashboard
เข้า Dashboard
3 min
setup
dashboard
ssh-tunnel
3
Part 3 — เข้า Dashboard ผ่าน SSH Tunnel

Dashboard คือหน้าควบคุม OpenClaw ทั้งหมด — ดู agents, ตั้งค่า, จัดการ models

Step 7: สร้าง SSH Tunnel

เปิด Terminal ใหม่ บนคอมของตัวเอง (ไม่ใช่ VPS):

TERMINAL
Copy
ssh -L 3000:localhost:GATEWAY_PORT root@YOUR_SERVER_IP

แทนค่า:

•

GATEWAY_PORT → port จาก Docker Manager (เช่น 54091)

•

YOUR_SERVER_IP → IP ของ VPS

ตัวอย่างจริง:

TERMINAL
Copy
ssh -L 3000:localhost:54091 root@187.127.98.204
Step 8: เปิด Dashboard

เปิด browser แล้วไปที่:

TERMINAL
Copy
http://localhost:3000
1.

ใส่ Gateway Token

1.

กด Connect

1.

เข้า Dashboard ได้แล้ว! 🎉

⚠️

⚠️ ต้องเข้าผ่าน localhost เท่านั้น — เปิดผ่าน http://IP:PORT ตรงไม่ได้ (จะขึ้น 'control ui requires device identity')

หา Gateway Token ไม่เจอ?

ไปที่ hPanel → Docker Manager → กด Manage ที่ project → ดู Environment → OPENCLAW_GATEWAY_TOKEN

NEXT IN LEARNING PATH

Troubleshooting & Useful Commands

Powered by Mew Social


---

# Troubleshooting & Useful Commands

Source: https://ask.mewsocial.com/browse/openclaw/oc-setup/troubleshooting

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Setup
Troubleshooting & Useful Commands
Troubleshooting & Useful Commands
5 min
3 steps
troubleshooting
commands
docker
อ่านแบบปกติ
ทำทีละ Step
สารบัญ
1
Troubleshooting & Useful Commands
2
ปัญหาที่เจอบ่อย
3
คำสั่งที่ใช้บ่อย
1
Troubleshooting & Useful Commands

รวมปัญหาที่เจอบ่อย + วิธีแก้ + คำสั่งที่ใช้บ่อย

2
ปัญหาที่เจอบ่อย
Permission Denied (อ่าน config ไม่ได้)
TERMINAL
Copy
docker exec -it openclaw-j9zz-openclaw-1 chown -R 1000:1000 /data/.openclaw
docker restart openclaw-j9zz-openclaw-1
'No API key found for provider'

แปลว่า OAuth ยังไม่สำเร็จ — ทำ Step 4-6 ในบทความ 'ตั้งค่า Auth ด้วย ChatGPT' ใหม่

'control ui requires device identity'

เข้า Dashboard ผ่าน http://IP:PORT ตรงไม่ได้ — ต้องใช้ SSH Tunnel (ดูบทความ 'เข้า Dashboard')

'docker: command not found'

คุณอยู่ข้างใน container อยู่ — พิมพ์ exit ออกมาก่อน แล้วค่อยรัน docker command

ลืม Gateway Token

hPanel → Docker Manager → กด Manage ที่ project → ดู OPENCLAW_GATEWAY_TOKEN ใน Environment

ไม่รู้ชื่อ Container
TERMINAL
Copy
docker ps

ดูคอลัมน์ NAMES จะเห็นชื่อเช่น openclaw-j9zz-openclaw-1

Token หมดอายุ

OAuth token อาจหมดอายุ ต้องทำ OAuth login ใหม่ (Step 4-6)

ทางเลือก: ใช้ OpenAI API key (pay-per-use ~$5-15/เดือน) หรือ OpenRouter

3
คำสั่งที่ใช้บ่อย
•

ดู container ที่รัน: docker ps

•

เข้าใน container: docker exec -it CONTAINER_NAME sh

•

ดู logs: docker logs CONTAINER_NAME -f

•

Restart: docker restart CONTAINER_NAME

•

ดู config: docker exec -it CONTAINER_NAME cat /data/.openclaw/openclaw.json

•

เปลี่ยน model: docker exec -it CONTAINER_NAME openclaw models set MODEL_NAME

•

ดู models ที่ใช้ได้: docker exec -it CONTAINER_NAME openclaw models list

NEXT IN LEARNING PATH

ตั้งค่า AI ให้เป็นแบรนด์ของคุณ

Powered by Mew Social


---

# ตั้งค่า AI ให้เป็นแบรนด์ของคุณ

Source: https://ask.mewsocial.com/browse/openclaw/oc-agent/brand-setup

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Agent
ตั้งค่า AI ให้เป็นแบรนด์ของคุณ
ตั้งค่า AI ให้เป็นแบรนด์ของคุณ
มี.ค. 2569
7 min
2 steps
agent
brand-brief
อ่านแบบปกติ
ทำทีละ Step
7
Step 7 — ตั้งชื่อ AI

ให้ AI มีตัวตน มีชื่อ — ทีมจะรู้สึกเหมือนมีเพื่อนร่วมงานคนใหม่

ตัวอย่างชื่อ: 🤖 "น้องเอ" — เลขาเก่ง 🦊 "น้องจิ้" — ผู้ช่วยคล่องแคล่ว 🐱 "มิ้นท์" — AI สายครีเอทีฟ ⚡ "สปาร์ค" — AI สาย tech

💡

💡 ชื่ออะไรก็ได้ที่ทีมจดจำ — AI จะเรียกตัวเองด้วยชื่อนี้!

8
Step 8 — Setup AI ด้วย Brand Brief

นี่คือขั้นตอนสำคัญที่สุด — ส่ง prompt นี้ให้ AI ใน Telegram เพื่อสร้าง "สมอง" ให้รู้จักแบรนด์คุณ

Copy prompt ด้านล่าง แก้ข้อมูลใน [ ] ตาม Brand Brief แล้ววางใน Telegram:

MARKDOWN
Copy
ตั้งค่าระบบให้ตามข้อมูลด้านล่างนี้

ชื่อ AI: [ชื่อที่ตั้งไว้]
Emoji: [เลือก emoji 1 ตัว]

สร้างไฟล์ 3 ไฟล์ให้ทั้ง:

📄 ไฟล์ที่ 1: SOUL.md — บุคลิกของ AI
- ใช้ชื่อกำหนด เรียกตัวเองด้วยชื่อนี้เสมอ
- เรียกผู้ใช้ว่า [ชื่อเล่น หรือ "หัวหน้า"]
- โทนเสียง: [professional / friendly / สนุกสนาน / อบอุ่น]
- ภาษาหลัก: [ไทย / อังกฤษ / ทั้งสอง]
- ตอบประเด็น ตรงประเด็น ไม่เวิ่นเว้อ
- กล้ามีความเห็น ไม่ตอบว่า "แล้วแต่" หรือ "ขึ้นอยู่กับ"
- กฎ:
 - ห้ามส่ง email/ข้อความออกภายนอกโดยไม่ถาม
 - ห้ามลงไฟล์โดยไม่ถาม
 - ห้ามเปิดเผยข้อมูลบริษัท / API key / password
- ทำได้: สรุปข้อมูล, เขียน content, ค้นหาข่าว, brainstorm, จัดการ task, ตั้ง reminder

📄 ไฟล์ที่ 2: USER.md — ข้อมูลเจ้าของ
- ชื่อ: [ชื่อ-นามสกุล]
- ตำแหน่ง: [ตำแหน่ง]
- บริษัท: [ชื่อบริษัท]
- อุตสาหกรรม: [ประเภทอุตสาหกรรม]
- สินค้า/บริการหลัก: [ระบุ]
- กลุ่มเป้าหมาย: [ระบุ]
- Timezone: Asia/Bangkok

📄 ไฟล์ที่ 3: MEMORY.md — ความจำเริ่มต้น
- ข้อมูลเพิ่มเติมจาก Brand Brief
- USP / จุดเด่น: [ระบุ]
- เว็บไซต์: [URL]
- Social Media: [FB / IG / LINE / etc.]
- ข้อมูลสำคัญอื่นๆ: [ระบุ]

--- Brand Brief ---
[วาง Brand Brief ตรงนี้]
ℹ️

ℹ️ AI จะสร้าง 3 ไฟล์ให้อัตโนมัติ — ทดสอบโดยส่ง "แนะนำตัวหน่อย" แล้ว AI จะตอบด้วยชื่อที่ตั้ง + รู้จักแบรนด์!

💡

💡 อยากเปลี่ยนบุคลิก AI ทีหลัง? ส่ง "แก้ SOUL.md ให้โทนเสียง [ใหม่]"

NEXT IN LEARNING PATH

สั่งทำ Content ครบชุด

Powered by Mew Social


---

# สั่งทำ Content ครบชุด

Source: https://ask.mewsocial.com/browse/openclaw/oc-usecase/content-creation

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Use Case
สั่งทำ Content ครบชุด
สั่งทำ Content ครบชุด
มี.ค. 2569
6 min
4 steps
use-case
content
อ่านแบบปกติ
ทำทีละ Step
⚠️

⚠️ ก่อนใช้งาน ต้องตั้งค่า API ก่อน → ดูวิธีที่หมวด ตั้งค่า API & Tools

สารบัญ
9
Step 9 — ติดตั้ง Content Toolkit
10
Step 10 — สั่งทำรูปโพสต์ + Caption ครบชุด
11
Step 11 — สั่งเขียน Caption อย่างเดียว
12
Step 12 — สั่งทำรูปอย่างเดียว
9
Step 9 — ติดตั้ง Content Toolkit

ให้ AI มีความสามารถทำ content ครบ: รูปโพสต์ + caption + hashtag

มี 2 วิธี เลือกวิธีไหนก็ได้ ผลเหมือนกัน:

วิธีที่ 1: ติดตั้งผ่าน ClawHub (แนะนำ)

ส่งข้อความนี้ให้ AI ใน Telegram:

TERMINAL
Copy
รันคำสั่ง 2 อันนี้ให้หน่อย:
1. clawhub install content-news-thai
2. bash skills/content-news-thai/scripts/setup.sh
⚠️

ถ้าติด rate limit → ใช้วิธีที่ 2 แทน

วิธีที่ 2: ติดตั้งเอง (ถ้า ClawHub ติด rate limit)

ส่งคำสั่งด้านล่างนี้เข้าไปที่ OpenClaw chat ได้เลย:

TERMINAL
Copy
# 1. Download
curl -L "https://drive.google.com/uc?export=download&id=1ujv420_i1oZerVKrMs3hf83iBp8Mwf2h" -o content-news-thai.zip

# 2. แตกไฟล์ไปที่ skills folder
unzip content-news-thai.zip -d ~/.openclaw/workspace/skills/

# 3. Install dependencies
cd ~/.openclaw/workspace/skills/content-news-thai/scripts
bash setup.sh
ติดตั้งเสร็จจะได้อะไร?
•

Template รูปข่าวสไตล์ Magazine

•

ฟอนต์ไทย (Kanit, Prompt, Sarabun)

•

ระบบ gen รูป + ซ้อนข้อความไทย

💡

รอ 2-3 นาที หลังติดตั้ง — พร้อมใช้!

10
Step 10 — สั่งทำรูปโพสต์ + Caption ครบชุด

Prompt หลัก — copy แล้วแก้ในวงเล็บ:

MARKDOWN
Copy
ทำ content ครบชุดเรื่อง "[หัวข้อข่าว]"

ต้องการ:
1. รูปโพสต์ 1080x1350 — มี headline ภาษาไทยบนรูป
2. Caption แบบ storytelling กระชับสั้น
3. Hashtag ที่เกี่ยวข้อง

กลุ่มเป้าหมาย: [ระบุ]

ตัวอย่าง:

MARKDOWN
Copy
ทำ content ครบชุดเรื่อง "AI กำลังเปลี่ยนวงการค้าปลีก ยอดขายพุ่ง 40%"
กลุ่มเป้าหมาย: เจ้าของธุรกิจค้าปลีก SME

AI จะทำให้: ✅ Gen background image ✅ ใส่ headline ภาษาไทย — ฟอนต์สวย ไม่เพี้ยน ไม่เบลอ ✅ เขียน caption storytelling ✅ ใส่ hashtag

11
Step 11 — สั่งเขียน Caption อย่างเดียว
MARKDOWN
Copy
เขียน caption สำหรับโพสต์ Facebook เรื่อง [หัวข้อ]

สไตล์:
- เล่าเรื่องแบบ storytelling กระชับสั้น
- เปิดด้วย hook ที่ทำให้หยุด scroll
- สรุปเนื้อหาตรงจุดไม่ยืดเยื้อ
- ปิดท้ายด้วยความเห็นสร้างสรรค์
- ชวนให้คนอยากส่งความคิดเห็น
- Hashtag 3-5 ตัว

กลุ่มเป้าหมาย: [ระบุ]
12
Step 12 — สั่งทำรูปอย่างเดียว
MARKDOWN
Copy
ทำรูปโพสต์ Facebook ให้หน่อย

หัวข้อ: [หัวข้อโพสต์]
Headline บนรูป: [ข้อความสั้นๆ]
Sub-headline: [ข้อความรอง]
ขนาด: 1080x1350
สไตล์: magazine cover
NEXT IN LEARNING PATH

งานเลขา AI

Powered by Mew Social


---

# งานเลขา AI

Source: https://ask.mewsocial.com/browse/openclaw/oc-usecase/ai-secretary

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Use Case
งานเลขา AI
งานเลขา AI
มี.ค. 2569
5 min
5 steps
use-case
productivity
อ่านแบบปกติ
ทำทีละ Step
⚠️

⚠️ ก่อนใช้งาน ต้องตั้งค่า API ก่อน → ดูวิธีที่หมวด ตั้งค่า API & Tools

สารบัญ
1
AI ช่วยได้มากกว่าแค่ Content!
2
ค้นหา / สรุปข้อมูล
3
Brainstorm / วางแผน
4
Reminder / จัดการ Task
5
จำข้อมูลสำคัญ
1
AI ช่วยได้มากกว่าแค่ Content!

นอกจากทำ content แล้ว AI ยังเป็นเลขาส่วนตัวที่ทำงานให้ 24/7 — ค้นหาข้อมูล, สรุปข่าว, brainstorm, จัดการ task, จำข้อมูลสำคัญ

2
ค้นหา / สรุปข้อมูล

หาข่าวล่าสุด:

MARKDOWN
Copy
หาข่าวล่าสุดเรื่อง [หัวข้อ] สรุปมา 3-5 ข่าว

สรุปบทความ:

MARKDOWN
Copy
สรุปบทความนี้: [วาง URL] เป็น bullet point สั้นๆ

สรุปข้อมูลยาว:

MARKDOWN
Copy
สรุปข้อมูลนี้เหลือ 5 ประเด็นหลัก: [วางข้อมูล]
3
Brainstorm / วางแผน
MARKDOWN
Copy
brainstorm ไอเดีย content 10 อัน สำหรับ [แบรนด์] กลุ่มเป้าหมาย [X]
MARKDOWN
Copy
วางแผน content 1 สัปดาห์ วันละ 2 โพสต์ แบ่ง 60% ให้คุณค่า / 20% เรื่องเล่า / 20% ขาย
4
Reminder / จัดการ Task
MARKDOWN
Copy
เตือนวันที่ [X] เวลา [X] เรื่อง [X]
MARKDOWN
Copy
จดไว้ — งานสัปดาห์นี้: 1. [X] 2. [X] 3. [X]
MARKDOWN
Copy
สรุปงานวันนี้ให้หน่อย
5
จำข้อมูลสำคัญ

AI จำข้อมูลได้! สั่ง "จำไว้ว่า [ข้อมูล]" แล้ว AI จะเก็บไว้ใน MEMORY.md

MARKDOWN
Copy
จำไว้ว่า ราคาสินค้า A = 1,500 บาท
MARKDOWN
Copy
จำไว้ว่า ผู้ติดต่อหลักคือ บริษัท X Y Z
MARKDOWN
Copy
จำไว้ว่า โปรโมชั่นถึงเดือนนี้ลด 20%
💡

💡 AI ทำงาน 24 ชั่วโมง — สั่งงานตี 3 ก็ได้!

NEXT IN LEARNING PATH

Prompt Cheat Sheet

Powered by Mew Social


---

# Prompt Cheat Sheet

Source: https://ask.mewsocial.com/browse/openclaw/oc-skill/prompt-cheat-sheet

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
Skill
Prompt Cheat Sheet
Prompt Cheat Sheet
มี.ค. 2569
3 min
skill
prompt
1
Prompt สำเร็จรูป — Copy แล้ววางได้เลย!

รวม prompt ที่ใช้บ่อยทั้งหมด แก้ข้อมูลในวงเล็บ [ ] แล้วส่งให้ AI ใน Telegram

🎨 ทำ Content ครบชุด
MARKDOWN
Copy
ทำ content ครบชุดเรื่อง "[X]" กลุ่มเป้าหมาย [Y]
✍️ เขียน Caption
MARKDOWN
Copy
เขียน caption FB เรื่อง [X] แบบ storytelling
🖼️ ทำรูปโพสต์
MARKDOWN
Copy
ทำรูปโพสต์ 1080x1350 หัวข้อ [X] สไตล์ magazine
🔍 หาข่าว
MARKDOWN
Copy
หาข่าวล่าสุดเรื่อง [X] สรุปมา 5 ข่าว
📝 สรุปบทความ
MARKDOWN
Copy
สรุปบทความนี้: [URL]
💡 Brainstorm
MARKDOWN
Copy
brainstorm ไอเดีย content 10 อัน สำหรับ [แบรนด์]
📅 วางแผน Content
MARKDOWN
Copy
วางแผน content 1 สัปดาห์ วันละ 2 โพสต์
⏰ ตั้ง Reminder
MARKDOWN
Copy
เตือนวันที่ [X] เวลา [X] เรื่อง [Y]
✅ จด Task
MARKDOWN
Copy
จดไว้ — งานสัปดาห์นี้: 1. [X] 2. [X] 3. [X]
💾 จำข้อมูล
MARKDOWN
Copy
จำไว้ว่า [ข้อมูลสำคัญ]
🔄 เปลี่ยนบุคลิก AI
MARKDOWN
Copy
แก้ SOUL.md ให้โทนเสียง [ใหม่]
ℹ️

ℹ️ Prompt เหล่านี้ใช้ได้ใน Telegram กับ bot ที่ตั้งค่าแล้วเท่านั้น

🔒

AI Money Machine

เปลี่ยน content เป็นเงินล้าน? สอนทุกขั้นตอน

ดูเพิ่มเติมที่คลังแสง AI →
Powered by Mew Social


---

# ตั้งค่า Kie.ai (สร้างรูป AI)

Source: https://ask.mewsocial.com/browse/openclaw/oc-api/setup-kie-ai

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
ตั้งค่า API & Tools
ตั้งค่า Kie.ai (สร้างรูป AI)
ตั้งค่า Kie.ai (สร้างรูป AI)
มี.ค. 2569
3 min
2 steps
api
image
setup
อ่านแบบปกติ
ทำทีละ Step
1
Kie.ai คืออะไร?

Kie.ai เป็นบริการสร้างรูปด้วย AI ที่ OpenClaw ใช้สำหรับ gen รูปโพสต์ รูปข่าว และ background ต่างๆ ราคาถูกกว่าใช้ API ตรง 30-50% เพราะเป็นระบบ credit-based จ่ายตามใช้

2
ขั้นตอนตั้งค่า
1. สมัครบัญชี

เปิด https://kie.ai → กด Sign up → สร้างบัญชี

2. สร้าง API Key

ไปที่ https://kie.ai/api-key → กด Create API Key → Copy เก็บไว้

TERMINAL
Copy
API Key ตัวอย่าง: kie_sk_xxxxxxxxxxxxxxxxxxxx
3. ใส่ใน OpenClaw

เข้า OpenClaw Dashboard → Settings → Config → หาช่อง Kie API Key → วาง key → กด Save

4. ทดสอบ

ส่งข้อความนี้ให้ AI ใน Telegram:

MARKDOWN
Copy
ทำรูปโพสต์ 1080x1350 หัวข้อ AI เปลี่ยนโลกธุรกิจ

ถ้าได้รูปกลับมา = สำเร็จ! 🎉

💡

💡 Kie.ai เป็น credit-based — เติมเงินตามใช้ ไม่มีค่ารายเดือน ประหยัดกว่า DALL-E API ตรง 30-50%

⚠️

⚠️ ถ้า gen รูปไม่ได้ ให้เช็ค: (1) API key ถูกมั้ย (2) มี credit เหลือมั้ย (3) ลอง restart bot

NEXT IN LEARNING PATH

ตั้งค่า Brave Search (ค้นหาข่าว)

Powered by Mew Social


---

# ตั้งค่า Brave Search (ค้นหาข่าว)

Source: https://ask.mewsocial.com/browse/openclaw/oc-api/setup-brave-search

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
ตั้งค่า API & Tools
ตั้งค่า Brave Search (ค้นหาข่าว)
ตั้งค่า Brave Search (ค้นหาข่าว)
มี.ค. 2569
3 min
2 steps
api
search
setup
อ่านแบบปกติ
ทำทีละ Step
1
Brave Search API คืออะไร?

Brave Search API ให้ AI ค้นหาข้อมูลบนอินเทอร์เน็ตได้แบบ real-time — หาข่าวล่าสุด ค้นหาข้อมูลคู่แข่ง เช็คเทรนด์ ฯลฯ มี free tier ให้ใช้ฟรี

2
ขั้นตอนตั้งค่า
1. สมัครบัญชี

เปิด https://brave.com/search/api/ → กด Get Started → สร้างบัญชี

2. เลือก Plan

เลือก "Data for Search" — มี free tier ให้ 2,000 queries/เดือน เพียงพอสำหรับเริ่มต้น

3. สร้าง API Key

ใน API Dashboard → กด Create API Key → Copy เก็บไว้

TERMINAL
Copy
API Key ตัวอย่าง: BSA_xxxxxxxxxxxxxxxxxxxx
4. ใส่ใน OpenClaw (เลือกวิธีใดวิธีหนึ่ง)

วิธี A — ผ่าน Dashboard: OpenClaw Dashboard → Settings → Config → ใส่ BRAVE_API_KEY → Save

วิธี B — ผ่าน Gateway Environment: hPanel → Docker Manager → Manage → Environment → เพิ่ม:

TERMINAL
Copy
BRAVE_API_KEY=BSA_xxxxxxxxxxxxxxxxxxxx
5. ทดสอบ

ส่งข้อความนี้ให้ AI:

MARKDOWN
Copy
หาข่าวล่าสุดเรื่อง AI สรุปมา 5 ข่าว

ถ้า AI หาข่าวจากอินเทอร์เน็ตได้ = สำเร็จ!

💡

💡 Free tier 2,000 queries/เดือน — เพียงพอสำหรับทีม 5 คนที่ใช้วันละ 10-15 ครั้ง

ℹ️

ℹ️ อ้างอิง: https://docs.openclaw.ai/brave-search

NEXT IN LEARNING PATH

ตั้งค่า Meta API (โพส Facebook/IG)

Powered by Mew Social


---

# ตั้งค่า Meta API (โพส Facebook/IG)

Source: https://ask.mewsocial.com/browse/openclaw/oc-api/setup-meta-api

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
ตั้งค่า API & Tools
ตั้งค่า Meta API (โพส Facebook/IG)
ตั้งค่า Meta API (โพส Facebook/IG)
มี.ค. 2569
8 min
2 steps
api
facebook
instagram
อ่านแบบปกติ
ทำทีละ Step
1
Meta API ทำอะไรได้?

เชื่อม Meta API แล้ว AI จะสามารถ: • โพส content ลง Facebook Page อัตโนมัติ • โพสลง Instagram Business • ตั้งเวลาโพสล่วงหน้า • ดึงข้อมูล insights

⚠️

⚠️ ขั้นตอนซับซ้อนกว่า API อื่น — แนะนำทำเป็น homework หลัง workshop หรือให้ทีม dev ช่วย

2
ขั้นตอนตั้งค่า
1. สร้าง Facebook App

1. เปิด https://developers.facebook.com 2. กด My Apps → Create App 3. เลือก Business → ตั้งชื่อ app 4. สร้างเสร็จจะเห็น App Dashboard

2. เพิ่ม Products

ใน App Dashboard: 1. กด Add Product 2. เพิ่ม "Facebook Login" → Set up 3. เพิ่ม "Pages API" (อาจต้อง request access)

3. สร้าง Page Access Token

1. ไป Graph API Explorer (developers.facebook.com/tools/explorer) 2. เลือก App ที่สร้าง 3. เลือก Page → Get Token 4. กด Generate Access Token 5. Copy token เก็บไว้

⚠️

⚠️ Token มีอายุ! ต้องสร้าง Long-lived token: 1. ใน App Dashboard → Settings → Basic → ดู App Secret 2. ใช้ Graph API แลก short-lived → long-lived token

4. ตั้งค่าใน OpenClaw

เข้า OpenClaw Dashboard → Settings → Config → ใส่: • Facebook App ID • Facebook App Secret • Page Access Token

5. ทดสอบ
MARKDOWN
Copy
โพสข้อความนี้ลง Facebook: "ทดสอบโพสจาก AI 🤖"
💡

💡 เชื่อม Meta API สำเร็จแล้ว สั่ง AI ตั้งเวลาโพสได้: "ตั้งเวลาโพสวันพรุ่งนี้ 10:00 เรื่อง [X]"

NEXT IN LEARNING PATH

ตั้งค่า YouTube API

Powered by Mew Social


---

# ตั้งค่า YouTube API

Source: https://ask.mewsocial.com/browse/openclaw/oc-api/setup-youtube-api

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
ตั้งค่า API & Tools
ตั้งค่า YouTube API
ตั้งค่า YouTube API
มี.ค. 2569
5 min
2 steps
api
youtube
google
อ่านแบบปกติ
ทำทีละ Step
1
YouTube API ทำอะไรได้?

เชื่อม YouTube API แล้ว AI จะสามารถ: • ค้นหาวิดีโอ YouTube • ดึงข้อมูล channel / video analytics • สร้าง script สำหรับ YouTube content

⚠️

⚠️ ต้องมี Google Cloud account ก่อน — ถ้ายังไม่มีสมัครฟรีที่ cloud.google.com

2
ขั้นตอนตั้งค่า
1. สร้าง Google Cloud Project

1. เปิด https://console.cloud.google.com 2. กด Select Project → New Project 3. ตั้งชื่อ → Create

2. เปิด YouTube Data API v3

1. ไปที่ APIs & Services → Library 2. ค้นหา "YouTube Data API v3" 3. กด Enable

3. สร้าง API Key

1. ไปที่ APIs & Services → Credentials 2. กด Create Credentials → API Key 3. Copy key เก็บไว้

TERMINAL
Copy
API Key ตัวอย่าง: AIzaSyXXXXXXXXXXXXXXXXXXX
⚠️

⚠️ แนะนำ: Restrict API key ให้ใช้ได้เฉพาะ YouTube Data API เท่านั้น — กันคนอื่นเอาไปใช้

4. ใส่ใน OpenClaw

OpenClaw Dashboard → Settings → Config → ใส่ YouTube API Key → Save

5. ทดสอบ
MARKDOWN
Copy
หาวิดีโอ YouTube เรื่อง AI Marketing สรุปมา 5 อัน
💡

💡 YouTube API มี free quota 10,000 units/วัน — เพียงพอสำหรับการใช้งานปกติ

NEXT IN LEARNING PATH

TikTok — หมายเหตุ

Powered by Mew Social


---

# TikTok — หมายเหตุ

Source: https://ask.mewsocial.com/browse/openclaw/oc-api/tiktok-note

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
ตั้งค่า API & Tools
TikTok — หมายเหตุ
TikTok — หมายเหตุ
มี.ค. 2569
1 min
2 steps
tiktok
note
อ่านแบบปกติ
ทำทีละ Step
1
TikTok API — ยังไม่รองรับ
ℹ️

ℹ️ OpenClaw ยังไม่รองรับ TikTok API โดยตรง ณ ตอนนี้ — อาจรองรับในอนาคต

2
วิธีใช้งาน TikTok กับ AI ตอนนี้

ให้ AI สร้าง content แล้ว copy ไปโพสเอง:

สร้าง Caption TikTok
MARKDOWN
Copy
เขียน caption TikTok เรื่อง [หัวข้อ] พร้อม hashtag ยอดนิยม
สร้าง Script วิดีโอ
MARKDOWN
Copy
เขียน script วิดีโอ TikTok 30 วินาที เรื่อง [หัวข้อ]
สไตล์: hook 3 วิแรก + เนื้อหา + CTA
วางแผน Content TikTok
MARKDOWN
Copy
วางแผน content TikTok 1 สัปดาห์ วันละ 1 คลิป
แนว: [ประเภท] กลุ่มเป้าหมาย: [X]
💡

💡 AI ช่วยคิด content ได้ — แค่ต้อง copy ไปโพสเองบน TikTok

🔒

AI Money Machine

เปลี่ยน content เป็นเงินล้าน? สอนทุกขั้นตอน

ดูเพิ่มเติมที่คลังแสง AI →
Powered by Mew Social


---

# 📣 Marketing — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-marketing

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
📣 Marketing — คำสั่งสำเร็จรูป
📣 Marketing — คำสั่งสำเร็จรูป
8 min
marketing
prompt
สำเร็จรูป
1
📣 Marketing — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

วางแผน Content Calendar

วางแผน content 1 เดือน แบ่งตามวัน + หัวข้อ

PROMPT
Copy
วางแผน content calendar สำหรับ [ชื่อแบรนด์]
ธุรกิจ: [ประเภทธุรกิจ]
กลุ่มเป้าหมาย: [กลุ่มเป้าหมาย]
ช่องทาง: [Facebook/IG/TikTok]
ระยะเวลา: 1 เดือน
โพสต์วันละ [1-2] โพสต์

แบ่งเป็น:
- 60% ให้ความรู้/คุณค่า
- 20% เล่าเรื่อง/behind the scene
- 20% ขาย/โปรโมชั่น
วิเคราะห์คู่แข่ง

เปรียบเทียบจุดแข็ง-จุดอ่อน กับคู่แข่ง 3 ราย

PROMPT
Copy
วิเคราะห์คู่แข่งให้หน่อย

แบรนด์เรา: [ชื่อแบรนด์] — [สินค้า/บริการ]
คู่แข่ง 3 ราย:
1. [ชื่อคู่แข่ง 1]
2. [ชื่อคู่แข่ง 2]
3. [ชื่อคู่แข่ง 3]

วิเคราะห์:
- จุดแข็ง vs จุดอ่อน
- กลยุทธ์ content ที่ใช้
- ราคาและ positioning
- โอกาสที่เราจะชนะ
เขียน Campaign Brief

สรุป brief แคมเปญให้ทีมเข้าใจตรงกัน

PROMPT
Copy
เขียน campaign brief

แคมเปญ: [ชื่อแคมเปญ]
วัตถุประสงค์: [เพิ่มยอดขาย/สร้าง awareness/lead gen]
สินค้า: [ชื่อสินค้า]
กลุ่มเป้าหมาย: [อายุ เพศ ความสนใจ]
งบประมาณ: [จำนวนเงิน]
ระยะเวลา: [วันเริ่ม - วันจบ]
ข้อความหลัก (Key Message): [1 ประโยค]
ช่องทาง: [FB/IG/TikTok/LINE]
สร้าง Buyer Persona

สร้างโปรไฟล์ลูกค้าในฝัน ละเอียดถึง pain point

PROMPT
Copy
สร้าง buyer persona สำหรับ [ชื่อแบรนด์]

สินค้า/บริการ: [อธิบายสั้นๆ]
ราคา: [ช่วงราคา]

สร้างให้ 2 personas:
แต่ละคนต้องมี:
- ชื่อสมมุติ + อายุ + อาชีพ
- รายได้/เดือน
- Pain points 3 ข้อ
- สิ่งที่มองหา (desires)
- ช่องทางที่ใช้ (social media)
- สิ่งที่ทำให้ตัดสินใจซื้อ
- ข้อกังวลก่อนซื้อ
Content Pillar Strategy

กำหนดเสาหลัก content 4-5 แกน

PROMPT
Copy
สร้าง content pillar strategy

แบรนด์: [ชื่อแบรนด์]
ธุรกิจ: [ประเภท]
กลุ่มเป้าหมาย: [ใคร]
เป้าหมาย: [สร้าง awareness / เพิ่มยอดขาย / สร้าง community]

สร้าง 4-5 content pillars:
แต่ละ pillar ต้องมี:
- ชื่อ pillar
- คำอธิบาย 1 บรรทัด
- ตัวอย่างหัวข้อ 3 อัน
- format ที่เหมาะ (โพสต์ / วิดีโอ / carousel / story)
เขียน Brand Message

สร้างข้อความแบรนด์ที่สื่อสารตรงจุด

PROMPT
Copy
เขียน brand message สำหรับ [ชื่อแบรนด์]

สินค้า/บริการ: [อะไร]
จุดเด่น: [USP 2-3 ข้อ]
กลุ่มเป้าหมาย: [ใคร]
คู่แข่ง: [ใคร]

เขียนให้:
1. Tagline (สั้นกระชับ 5-7 คำ)
2. Elevator Pitch (30 วินาที)
3. Brand Story (3 ย่อหน้า)
4. Value Proposition (3 ข้อ)
5. Tone of Voice (อธิบาย + ตัวอย่างประโยค)
วิเคราะห์ SWOT

วิเคราะห์จุดแข็ง จุดอ่อน โอกาส อุปสรรค

PROMPT
Copy
วิเคราะห์ SWOT ให้หน่อย

ธุรกิจ: [ชื่อธุรกิจ]
สินค้า/บริการ: [อะไร]
ตลาด: [B2C/B2B — อุตสาหกรรม]
คู่แข่งหลัก: [ใคร]

วิเคราะห์:
- Strengths (จุดแข็ง 3-5 ข้อ)
- Weaknesses (จุดอ่อน 3-5 ข้อ)
- Opportunities (โอกาส 3-5 ข้อ)
- Threats (อุปสรรค 3-5 ข้อ)

สรุป action plan 3 ข้อจาก SWOT
Social Media Audit

ตรวจสอบและประเมิน social media ทุกช่องทาง

PROMPT
Copy
ช่วย audit social media ให้หน่อย

แบรนด์: [ชื่อแบรนด์]
ช่องทางที่ใช้:
- Facebook: [URL หรือชื่อเพจ]
- Instagram: [URL]
- TikTok: [URL]
- LINE: [มี/ไม่มี]

วิเคราะห์:
1. ความถี่ในการโพสต์
2. ประเภท content ที่โพสต์
3. engagement rate
4. จุดที่ทำดี
5. จุดที่ควรปรับปรุง
6. แนะนำ 5 action items
NEXT IN LEARNING PATH

💰 Sales — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 💰 Sales — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-sales

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
💰 Sales — คำสั่งสำเร็จรูป
💰 Sales — คำสั่งสำเร็จรูป
8 min
sales
prompt
สำเร็จรูป
1
💰 Sales — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียน Sales Pitch

สร้าง pitch ที่โน้มน้าวใจใน 2 นาที

PROMPT
Copy
เขียน sales pitch สำหรับ [ชื่อสินค้า/บริการ]

ขายให้: [กลุ่มเป้าหมาย]
ราคา: [ราคา]
จุดเด่น: [USP 3 ข้อ]
ปัญหาที่แก้: [pain point ของลูกค้า]

เขียน pitch 3 แบบ:
1. แบบสั้น 30 วินาที (elevator pitch)
2. แบบกลาง 2 นาที (presentation)
3. แบบ chat (ส่งทาง LINE/DM)
สร้าง Proposal

เขียน proposal ส่งลูกค้าแบบมืออาชีพ

PROMPT
Copy
เขียน proposal สำหรับ [ชื่อโปรเจค]

ลูกค้า: [ชื่อบริษัท/คน]
บริการ: [อะไร]
ขอบเขตงาน: [รายละเอียด]
ระยะเวลา: [กี่วัน/สัปดาห์/เดือน]
งบประมาณ: [ช่วงราคา]

ต้องมี:
1. Executive Summary
2. ปัญหาที่จะแก้
3. แนวทางการทำงาน
4. Timeline
5. ราคาและเงื่อนไข
6. ทำไมต้องเลือกเรา
Follow-up Email

ส่ง follow-up หลังเสนอราคา หรือหลังประชุม

PROMPT
Copy
เขียน follow-up email

บริบท: [ประชุมเมื่อวาน / ส่ง proposal ไปแล้ว 3 วัน / พบกันที่งาน X]
ชื่อลูกค้า: [ชื่อ]
สินค้า/บริการ: [อะไร]
เป้าหมาย: [นัดประชุม / ปิดการขาย / ถามความคืบหน้า]

เขียนให้:
- subject line ที่น่าเปิด
- เนื้อหาสั้นกระชับ
- CTA ชัดเจน
- tone: professional แต่เป็นกันเอง
Objection Handling Script

เตรียมคำตอบสำหรับข้อโต้แย้งที่พบบ่อย

PROMPT
Copy
สร้าง objection handling script

สินค้า/บริการ: [อะไร]
ราคา: [ราคา]
กลุ่มเป้าหมาย: [ใคร]

เตรียมคำตอบสำหรับ:
1. "แพงไป"
2. "ขอคิดก่อน"
3. "ไม่แน่ใจว่าจะได้ผล"
4. "ใช้ของที่อื่นอยู่แล้ว"
5. "ยังไม่ใช่เวลาที่เหมาะ"
6. "ส่งข้อมูลมาให้ดูก่อน"
7. "ต้องปรึกษาคนอื่นก่อน"

แต่ละข้อตอบ 2-3 ประโยค tone เป็นกันเอง ไม่กดดัน
Cold Outreach Message

เขียนข้อความ DM หาลูกค้าใหม่

PROMPT
Copy
เขียน cold outreach message

ส่งทาง: [LINE / DM IG / Email / FB Messenger]
ลูกค้าเป้าหมาย: [ใคร — อาชีพ/ธุรกิจ]
สินค้า/บริการ: [อะไร]
จุดเด่น: [ทำไมเขาควรสนใจ]

เขียน 3 แบบ:
1. แบบตรงประเด็น (3 บรรทัด)
2. แบบให้คุณค่าก่อน (share ความรู้ → ชวนคุย)
3. แบบอ้างอิงผลงาน (case study สั้นๆ)

ห้ามเหมือน spam ต้องรู้สึกเหมือนคนจริงส่งมา
เขียน Quotation

สร้างใบเสนอราคาแบบมีรายละเอียดครบ

PROMPT
Copy
สร้างใบเสนอราคา

จาก: [ชื่อบริษัท/ชื่อเรา]
ถึง: [ชื่อลูกค้า]
โปรเจค: [ชื่อโปรเจค]

รายการ:
1. [รายการที่ 1] — [รายละเอียด]
2. [รายการที่ 2] — [รายละเอียด]
3. [รายการที่ 3] — [รายละเอียด]

เงื่อนไข: [ระยะเวลา / จำนวนแก้ไข / ส่งมอบยังไง]
การชำระเงิน: [มัดจำ % / งวดไหนบ้าง]
สรุป Pipeline

สรุปสถานะการขายทั้งหมดแบบเห็นภาพ

PROMPT
Copy
สรุป sales pipeline ให้หน่อย

ข้อมูล deals ปัจจุบัน:
1. [ชื่อลูกค้า] — [มูลค่า] — [สถานะ: ติดต่อแล้ว/เสนอราคา/รอตอบ/ปิดได้]
2. [ชื่อลูกค้า] — [มูลค่า] — [สถานะ]
3. [ชื่อลูกค้า] — [มูลค่า] — [สถานะ]
(เพิ่มได้ตามจริง)

สรุปให้:
- จำนวน deals ในแต่ละ stage
- มูลค่ารวม
- deals ที่ควร follow-up ด่วน
- คาดการณ์ยอดเดือนนี้
Win-back Campaign

ชวนลูกค้าเก่ากลับมาซื้ออีกครั้ง

PROMPT
Copy
สร้าง win-back campaign

ธุรกิจ: [ชื่อธุรกิจ]
สินค้า/บริการ: [อะไร]
ลูกค้าเก่า: [ซื้อครั้งสุดท้ายนานแค่ไหน]
จำนวนลูกค้าเก่า: [ประมาณกี่คน]

เขียนให้:
1. ข้อความ re-engage แรก (ทักทาย + ถามสารทุกข์)
2. ข้อความ offer พิเศษ (ส่วนลด/ของแถม)
3. ข้อความ last chance (urgency)
4. flow ส่งแต่ละข้อความห่างกันกี่วัน

ส่งทาง: [LINE / Email / SMS]
NEXT IN LEARNING PATH

📝 Admin — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 📝 Admin — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-admin

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
📝 Admin — คำสั่งสำเร็จรูป
📝 Admin — คำสั่งสำเร็จรูป
8 min
admin
prompt
สำเร็จรูป
1
📝 Admin — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

สรุปประชุม

สรุป meeting notes จาก transcript หรือจดเอง

PROMPT
Copy
สรุปประชุมให้หน่อย

ประชุมเรื่อง: [หัวข้อ]
ผู้เข้าร่วม: [รายชื่อ]
วันที่: [วันที่]

เนื้อหาที่คุยกัน:
[วางเนื้อหาที่จดไว้ หรือ transcript ตรงนี้]

สรุปให้:
1. ประเด็นสำคัญ (bullet points)
2. Action Items — ใครทำอะไร เมื่อไหร่
3. ข้อตกลงที่ได้
4. นัดถัดไป
เขียน Email ทางการ

เขียน email ภาษาสุภาพ เป็นทางการ

PROMPT
Copy
เขียน email ทางการ

ส่งถึง: [ชื่อ — ตำแหน่ง]
เรื่อง: [หัวข้อ email]
วัตถุประสงค์: [แจ้งเรื่อง / ขอข้อมูล / ส่งเอกสาร / เชิญประชุม]
รายละเอียด: [ข้อมูลที่ต้องใส่]

Tone: [ทางการมาก / ทางการปานกลาง / semi-formal]
ภาษา: [ไทย / อังกฤษ]
ลงท้าย: [ชื่อ — ตำแหน่ง — บริษัท]
จัดตาราง

สร้างตารางงาน/ตารางเวร/timeline

PROMPT
Copy
จัดตารางให้หน่อย

ประเภท: [ตารางงานรายสัปดาห์ / ตารางเวร / timeline โปรเจค]
จำนวนคน: [กี่คน — ชื่อ]
ระยะเวลา: [1 สัปดาห์ / 1 เดือน]
เงื่อนไข:
- [เช่น คนละไม่เกิน 5 วัน/สัปดาห์]
- [วันหยุด: เสาร์-อาทิตย์]
- [ต้องมีคนอย่างน้อย 2 คน/วัน]

Format: ตาราง
สร้าง SOP

เขียน Standard Operating Procedure ขั้นตอนชัดเจน

PROMPT
Copy
สร้าง SOP สำหรับ [ชื่อกระบวนการ]

แผนก: [แผนกอะไร]
ผู้รับผิดชอบ: [ตำแหน่ง]
ความถี่: [ทุกวัน / ทุกสัปดาห์ / ตามเคส]

รายละเอียดกระบวนการ:
[อธิบายคร่าวๆ ว่าทำอะไรบ้าง]

เขียน SOP ที่มี:
1. วัตถุประสงค์
2. ขอบเขต
3. ขั้นตอน (step-by-step พร้อมรายละเอียด)
4. checklist สิ่งที่ต้องตรวจ
5. ข้อควรระวัง
เขียนรายงาน

สรุปรายงานสรุปผลงาน ประจำสัปดาห์/เดือน

PROMPT
Copy
เขียนรายงานสรุป

ประเภท: [รายงานประจำสัปดาห์ / เดือน / โปรเจค]
ช่วงเวลา: [วันที่ — ถึงวันที่]
แผนก: [แผนก]

ผลงาน:
- [ผลงานที่ 1]
- [ผลงานที่ 2]
- [ผลงานที่ 3]

ปัญหา/อุปสรรค:
- [ปัญหาที่ 1]

เขียนรายงานที่มี:
1. สรุปภาพรวม
2. ผลงานสำคัญ
3. ตัวเลข/KPI
4. ปัญหาและวิธีแก้
5. แผนสัปดาห์/เดือนหน้า
นัดหมาย

เขียนข้อความนัดประชุม/นัดพบ

PROMPT
Copy
เขียนข้อความนัดหมาย

นัดกับ: [ชื่อ/ทีม]
เรื่อง: [หัวข้อ]
วันเวลาที่เสนอ:
- ตัวเลือก 1: [วัน เวลา]
- ตัวเลือก 2: [วัน เวลา]
- ตัวเลือก 3: [วัน เวลา]
สถานที่: [ออฟฟิศ / Zoom / Google Meet]
ระยะเวลา: [30 นาที / 1 ชั่วโมง]

ส่งทาง: [Email / LINE / Teams]
Tone: [ทางการ / เป็นกันเอง]
Memo ภายใน

เขียน memo แจ้งเรื่องภายในบริษัท

PROMPT
Copy
เขียน memo ภายใน

จาก: [ชื่อ — ตำแหน่ง]
ถึง: [ทีม/แผนก/ทุกคน]
เรื่อง: [หัวข้อ]
วันที่: [วันที่]

เนื้อหา:
[อธิบายสิ่งที่ต้องแจ้ง]

สิ่งที่ต้องทำ:
- [action item 1]
- [action item 2]

Deadline: [วันที่]
Tone: [ทางการ / กึ่งทางการ]
Checklist งาน

สร้าง checklist สำหรับงานหรือ event

PROMPT
Copy
สร้าง checklist สำหรับ [ชื่องาน/event/โปรเจค]

รายละเอียด: [อธิบายคร่าวๆ]
วันที่: [วันที่จัดงาน/deadline]
ทีม: [กี่คน — ใครบ้าง]

สร้าง checklist แบ่งเป็น:
1. ก่อนงาน (เตรียมอะไรบ้าง)
2. วันงาน (ทำอะไรบ้าง ตามลำดับ)
3. หลังงาน (สรุป/follow-up)

แต่ละ item ระบุ: ผู้รับผิดชอบ + deadline
NEXT IN LEARNING PATH

🎨 Content Creator — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 🎨 Content Creator — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-creator

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
🎨 Content Creator — คำสั่งสำเร็จรูป
🎨 Content Creator — คำสั่งสำเร็จรูป
8 min
content-creator
prompt
สำเร็จรูป
1
🎨 Content Creator — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียน Script วิดีโอ

เขียน script สำหรับ Reels/TikTok/YouTube

PROMPT
Copy
เขียน script วิดีโอ

แพลตฟอร์ม: [Reels / TikTok / YouTube]
ความยาว: [15 วินาที / 60 วินาที / 5 นาที]
หัวข้อ: [เรื่องอะไร]
กลุ่มเป้าหมาย: [ใคร]
สไตล์: [สอน / เล่าเรื่อง / ตลก / dramatic]

ต้องมี:
1. Hook แรก (3 วินาทีแรก) — ต้องหยุด scroll
2. เนื้อหา — จัดเป็น scene
3. CTA — ปิดท้ายให้คนทำอะไร
4. คำแนะนำ B-roll / transition
Caption Storytelling

เขียน caption แบบเล่าเรื่องชวนอ่านจนจบ

PROMPT
Copy
เขียน caption แบบ storytelling

แพลตฟอร์ม: [Facebook / IG / TikTok]
หัวข้อ: [เรื่องอะไร]
แบรนด์: [ชื่อแบรนด์]
กลุ่มเป้าหมาย: [ใคร]

สไตล์:
- เปิดด้วย hook ที่ทำให้หยุด scroll
- เล่าเรื่องประสบการณ์จริง
- สรุปเชื่อมกลับสินค้า/บริการ
- ปิดด้วย CTA + emoji
- Hashtag 3-5 ตัว
Brainstorm ไอเดีย 10 อัน

ระดมไอเดีย content 10 หัวข้อ ทำได้เลย

PROMPT
Copy
brainstorm ไอเดีย content 10 อัน

แบรนด์: [ชื่อแบรนด์]
ธุรกิจ: [ประเภท]
กลุ่มเป้าหมาย: [ใคร]
ช่องทาง: [Facebook / IG / TikTok]

แต่ละไอเดียต้องมี:
- หัวข้อ
- format (โพสต์ / Reels / carousel / story)
- hook 1 บรรทัด
- ทำไมเรื่องนี้คนจะสนใจ

เน้น: 60% ให้ความรู้ / 20% เล่าเรื่อง / 20% ขาย
เขียน Blog Post

เขียนบทความ SEO-friendly จาก outline

PROMPT
Copy
เขียน blog post

หัวข้อ: [ชื่อบทความ]
Keyword หลัก: [keyword ที่ต้องการ rank]
ความยาว: [800 / 1500 / 2000 คำ]
กลุ่มเป้าหมาย: [ใคร]
Tone: [ให้ความรู้ / สนุกสนาน / มืออาชีพ]

โครงสร้าง:
1. Title (มี keyword + น่าคลิก)
2. Intro (hook + สรุปสิ่งที่จะได้)
3. เนื้อหา (แบ่งหัวข้อย่อย H2/H3)
4. สรุป
5. CTA
6. Meta description
Carousel Content

สร้าง carousel 7-10 slides สวยๆ

PROMPT
Copy
สร้าง carousel content

แพลตฟอร์ม: [IG / Facebook / LinkedIn]
หัวข้อ: [เรื่องอะไร]
จำนวน slides: [7-10 slides]
กลุ่มเป้าหมาย: [ใคร]

แต่ละ slide ต้องมี:
- Headline (สั้นกระชับ)
- เนื้อหา (2-3 บรรทัด)
- คำแนะนำภาพ/graphic

Slide แรก: Hook ที่ทำให้ swipe
Slide สุดท้าย: CTA + ชวน save/share
Podcast Outline

วางโครงสร้าง episode พร้อมคำถาม

PROMPT
Copy
สร้าง podcast outline

ชื่อรายการ: [ชื่อ podcast]
หัวข้อ episode: [เรื่องอะไร]
แขกรับเชิญ: [ชื่อ — ตำแหน่ง] (ถ้ามี)
ความยาว: [30 นาที / 1 ชั่วโมง]

สร้าง outline:
1. Intro (แนะนำตัว + หัวข้อ)
2. Main questions (5-7 คำถาม)
3. Deep dive topics
4. Quick fire round (คำถามสั้นๆ สนุกๆ)
5. Outro (สรุป + CTA)

Tone: [casual / professional]
Newsletter

เขียน newsletter อ่านจบใน 3 นาที

PROMPT
Copy
เขียน newsletter

ชื่อ newsletter: [ชื่อ]
หัวข้อสัปดาห์นี้: [เรื่องอะไร]
กลุ่มผู้อ่าน: [ใคร]

โครงสร้าง:
1. Subject line (น่าเปิด — เขียน 3 ตัวเลือก)
2. Preview text
3. เนื้อหาหลัก (อ่านจบใน 3 นาที)
4. ลิงก์/แหล่งอ้างอิง 2-3 อัน
5. CTA
6. PS line (เกร็ดเล็กน้อย)
Content Repurpose

แปลง content เดิมเป็นหลาย format

PROMPT
Copy
repurpose content นี้ให้หน่อย

Content เดิม:
[วาง content เดิมตรงนี้ — บทความ / script / post]

แปลงเป็น:
1. Twitter/X thread (5-7 tweets)
2. LinkedIn post
3. IG carousel outline (7 slides)
4. TikTok script (60 วินาที)
5. Email newsletter excerpt
6. Facebook post

รักษา key message เดิม แต่ปรับ tone ให้เหมาะแต่ละแพลตฟอร์ม
NEXT IN LEARNING PATH

🛒 Affiliate — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 🛒 Affiliate — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-affiliate

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
🛒 Affiliate — คำสั่งสำเร็จรูป
🛒 Affiliate — คำสั่งสำเร็จรูป
8 min
affiliate
prompt
สำเร็จรูป
1
🛒 Affiliate — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียนรีวิวสินค้า

รีวิวสินค้าแบบน่าเชื่อถือ ชวนซื้อ

PROMPT
Copy
เขียนรีวิวสินค้า

ชื่อสินค้า: [ชื่อ]
แบรนด์: [แบรนด์]
ราคา: [ราคา]
หมวดหมู่: [เช่น gadget / beauty / health]

ข้อมูลสินค้า:
- จุดเด่น: [3-5 ข้อ]
- ข้อด้อย: [1-2 ข้อ — ซื่อสัตย์]
- เหมาะกับใคร: [กลุ่มเป้าหมาย]

เขียนรีวิว:
1. Hook (ทำไมต้องอ่าน)
2. ประสบการณ์ใช้จริง
3. ข้อดี-ข้อเสีย
4. เทียบกับคู่แข่ง
5. สรุป + ให้คะแนน /10
6. CTA (link ซื้อ)
เปรียบเทียบ 3 สินค้า

ตารางเปรียบเทียบ side-by-side

PROMPT
Copy
เปรียบเทียบ 3 สินค้า

หมวดหมู่: [เช่น หูฟัง / ครีมกันแดด / คอร์สออนไลน์]

สินค้า:
1. [ชื่อ] — ราคา [X] บาท
2. [ชื่อ] — ราคา [X] บาท
3. [ชื่อ] — ราคา [X] บาท

เปรียบเทียบ:
- คุณสมบัติ
- ราคา
- ข้อดี-ข้อเสีย
- เหมาะกับใคร
- Rating /10

สรุป: ตัวไหนดีที่สุดสำหรับคนไหน
Format: ตาราง + สรุปแต่ละตัว
Landing Page Copy

เขียน copy สำหรับหน้า landing page

PROMPT
Copy
เขียน landing page copy

สินค้า: [ชื่อสินค้า]
ราคา: [ราคา]
กลุ่มเป้าหมาย: [ใคร]
ปัญหาที่แก้: [pain point]

เขียนให้:
1. Headline (จับใจ — 1 บรรทัด)
2. Sub-headline
3. Pain points (3 ข้อ)
4. Solution (สินค้าแก้ยังไง)
5. Features & Benefits (5 ข้อ)
6. Social proof (testimonial format)
7. FAQ (3-5 คำถาม)
8. CTA (ปุ่มกดซื้อ + urgency)
Email Sequence

ชุด email 5 ฉบับสำหรับ nurture → ขาย

PROMPT
Copy
สร้าง email sequence 5 ฉบับ

สินค้า: [ชื่อ]
ราคา: [ราคา]
กลุ่มเป้าหมาย: [ใคร]

Sequence:
1. Welcome (แนะนำตัว + ให้คุณค่า)
2. Pain point (ชี้ปัญหา)
3. Solution (แนะนำสินค้า)
4. Social proof (รีวิว/case study)
5. Last chance (urgency + CTA)

แต่ละฉบับ:
- Subject line
- เนื้อหา 150-200 คำ
- CTA
- ส่งห่างกัน [2-3 วัน]
สรุปจุดเด่นสินค้า

สรุป selling points สั้นกระชับ ใช้ได้ทุกที่

PROMPT
Copy
สรุปจุดเด่นสินค้า

ชื่อสินค้า: [ชื่อ]
ราคา: [ราคา]
ข้อมูลสินค้า:
[วางข้อมูลสินค้าตรงนี้ — spec / features / description]

สรุปเป็น:
1. USP 1 บรรทัด
2. Bullet points 5 ข้อ (features → benefits)
3. เหมาะกับใคร (2-3 กลุ่ม)
4. ทำไมต้องตัวนี้ (เปรียบเทียบ)
5. Caption สั้นๆ ใช้โพสต์ได้เลย
เขียน CTA ที่ได้ผล

สร้าง call-to-action หลายแบบสำหรับ A/B test

PROMPT
Copy
สร้าง CTA (Call-to-Action) 10 แบบ

สินค้า: [ชื่อ]
ราคา: [ราคา]
ข้อเสนอ: [ส่วนลด / ของแถม / ทดลองฟรี]
ช่องทาง: [เว็บ / FB / IG / LINE]

สร้าง CTA:
- 3 แบบสร้าง urgency
- 3 แบบให้คุณค่า
- 2 แบบ social proof
- 2 แบบตลก/สนุก

แต่ละอัน: ข้อความ CTA + ปุ่ม text
Commission Calculator

คำนวณรายได้ affiliate ตามสถานการณ์ต่างๆ

PROMPT
Copy
คำนวณรายได้ affiliate

สินค้า: [ชื่อ]
ราคาสินค้า: [ราคา] บาท
ค่า commission: [X]%

คำนวณให้:
1. ขายได้ 10 ชิ้น/เดือน = ?
2. ขายได้ 50 ชิ้น/เดือน = ?
3. ขายได้ 100 ชิ้น/เดือน = ?

วิเคราะห์:
- ต้องมี traffic เท่าไหร่ (สมมุติ conversion rate 2-3%)
- ช่องทางไหนน่าจะได้ traffic มากสุด
- เทียบกับเวลาที่ใช้ คุ้มมั้ย
Product Roundup

เขียนบทความ 'X สินค้าที่ดีที่สุด' สำหรับ SEO

PROMPT
Copy
เขียน product roundup

หัวข้อ: "[จำนวน] [หมวดหมู่] ที่ดีที่สุดใน [ปี]"
ตัวอย่าง: "7 หูฟังไร้สายที่ดีที่สุดในปี 2026"

สินค้า:
1. [ชื่อ] — ราคา [X]
2. [ชื่อ] — ราคา [X]
3. [ชื่อ] — ราคา [X]
(เพิ่มได้)

แต่ละตัวต้องมี:
- ภาพรวม 2-3 ประโยค
- ข้อดี 3 ข้อ / ข้อเสีย 1-2 ข้อ
- เหมาะกับใคร
- Rating /10

สรุป: ตัวไหนดีสำหรับงบไหน
NEXT IN LEARNING PATH

🎵 TikToker — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 🎵 TikToker — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-tiktoker

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
🎵 TikToker — คำสั่งสำเร็จรูป
🎵 TikToker — คำสั่งสำเร็จรูป
7 min
tiktok
prompt
สำเร็จรูป
1
🎵 TikToker — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

Hook 3 วินาที

สร้าง opening hook ที่หยุด scroll ได้

PROMPT
Copy
สร้าง hook สำหรับ TikTok 10 แบบ

หัวข้อ: [เรื่องอะไร]
กลุ่มเป้าหมาย: [ใคร]

แต่ละ hook:
- ความยาวไม่เกิน 3 วินาที
- ต้องทำให้คนหยุด scroll
- มี element of surprise / curiosity / controversy

แบบ:
- 3 แบบ "คุณทำผิดมาตลอด..."
- 3 แบบ "ไม่มีใครบอกคุณเรื่องนี้..."
- 2 แบบตั้งคำถาม
- 2 แบบ shocking fact
Viral Script Format

script TikTok ที่มีโอกาส viral สูง

PROMPT
Copy
เขียน TikTok script แบบ viral

หัวข้อ: [เรื่องอะไร]
ความยาว: [15 / 30 / 60 วินาที]
สไตล์: [สอน / เล่าเรื่อง / ตลก / shocking]

Format:
[0-3s] HOOK: (หยุด scroll)
[3-10s] CONTEXT: (ทำไมต้องดู)
[10-25s] CONTENT: (เนื้อหาหลัก)
[25-30s] CTA: (ทำให้คนมีส่วนร่วม)

เพิ่ม:
- คำแนะนำ text overlay
- เพลงที่เหมาะ (trending)
- transition ที่แนะนำ
Trend Adaptation

เอา trend มาดัดแปลงให้เข้ากับแบรนด์

PROMPT
Copy
ดัดแปลง TikTok trend ให้เข้ากับแบรนด์

Trend: [อธิบาย trend — เช่น "get ready with me" / "POV" / เพลงที่กำลังฮิต]
แบรนด์: [ชื่อแบรนด์]
สินค้า/บริการ: [อะไร]
กลุ่มเป้าหมาย: [ใคร]

สร้าง script 3 แบบ:
1. แบบตรงๆ (ตาม trend เป๊ะ + ใส่แบรนด์)
2. แบบ twist (ดัดแปลงให้แปลก)
3. แบบ series (ต่อยอดเป็น 3 ตอน)
Duet/Stitch Ideas

ไอเดีย duet หรือ stitch กับ video ดังๆ

PROMPT
Copy
ให้ไอเดีย duet/stitch 5 แบบ

หัวข้อ/niche: [niche ของช่อง]
แบรนด์: [ชื่อแบรนด์] (ถ้ามี)
สไตล์ช่อง: [สอน / ตลก / lifestyle]

แต่ละไอเดีย:
- ประเภท: duet หรือ stitch
- stitch กับ video แบบไหน (อธิบายประเภท)
- script ที่จะพูด
- ทำไมคนจะดู
- estimated length
Caption สั้น

caption TikTok ที่สั้นกระชับ ชวนมีส่วนร่วม

PROMPT
Copy
เขียน TikTok caption 10 แบบ

หัวข้อวิดีโอ: [เรื่องอะไร]

เขียน:
- 3 แบบตั้งคำถาม (ชวน comment)
- 3 แบบ controversial (ชวน debate)
- 2 แบบตลก
- 2 แบบ CTA (ชวน follow/save/share)

ทุกอัน:
- ไม่เกิน 2 บรรทัด
- มี emoji 1-2 ตัว
- ไม่ใส่ hashtag (ใส่แยก)
Hashtag Strategy

วาง hashtag strategy สำหรับ reach สูงสุด

PROMPT
Copy
วาง hashtag strategy สำหรับ TikTok

Niche: [niche ของช่อง]
หัวข้อวิดีโอ: [เรื่องอะไร]
กลุ่มเป้าหมาย: [ใคร]
ภาษา: [ไทย / ไทย+อังกฤษ]

สร้าง hashtag set:
1. Trending hashtags (3-5 อัน)
2. Niche hashtags (3-5 อัน)
3. Long-tail hashtags (3-5 อัน)
4. Branded hashtag (1 อัน — สร้างใหม่)

อธิบาย: ทำไมเลือก hashtag เหล่านี้
Content Series

วาง content series 5-7 ตอน ให้คนติดตาม

PROMPT
Copy
สร้าง TikTok content series

หัวข้อ series: [เรื่องอะไร]
จำนวนตอน: [5-7 ตอน]
ความยาวต่อตอน: [30-60 วินาที]

แต่ละตอน:
- ชื่อตอน
- hook
- เนื้อหาหลัก
- cliffhanger/teaser ตอนถัดไป

ตอนแรก: intro + ทำให้อยากดูต่อ
ตอนสุดท้าย: สรุป + CTA follow
Behind-the-Scene Script

script เบื้องหลังการทำงาน ให้คนรู้สึกใกล้ชิด

PROMPT
Copy
เขียน behind-the-scene script

เบื้องหลังอะไร: [ทำงาน / ผลิตสินค้า / เตรียมงาน / ชีวิตประจำวัน]
ธุรกิจ: [ชื่อธุรกิจ]
ความยาว: [30-60 วินาที]

Format:
- เปิดด้วย "พาดูเบื้องหลัง..."
- แสดง process step-by-step
- ใส่ personality + ความรู้สึก
- ปิดด้วยผลลัพธ์ที่น่าพอใจ

Tone: genuine, ไม่ทำ ไม่เว่อร์
NEXT IN LEARNING PATH

💼 Freelancer — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 💼 Freelancer — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-freelancer

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
💼 Freelancer — คำสั่งสำเร็จรูป
💼 Freelancer — คำสั่งสำเร็จรูป
8 min
freelancer
prompt
สำเร็จรูป
1
💼 Freelancer — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียน Proposal ส่งลูกค้า

proposal ที่ดูมืออาชีพ ปิดงานได้

PROMPT
Copy
เขียน proposal สำหรับ freelance

งาน: [ประเภทงาน — design / เขียน content / dev / marketing]
ลูกค้า: [ชื่อ/บริษัท]
โจทย์: [ลูกค้าต้องการอะไร]
ราคา: [ราคาที่จะเสนอ]
ระยะเวลา: [กี่วัน]

ต้องมี:
1. เข้าใจโจทย์ (paraphrase สิ่งที่ลูกค้าต้องการ)
2. แนวทางการทำงาน
3. ผลงานที่เกี่ยวข้อง (อ้างอิง)
4. Timeline
5. ราคาและเงื่อนไข
6. ทำไมต้องเลือกเรา
Portfolio Description

เขียนอธิบายผลงานให้น่าสนใจ

PROMPT
Copy
เขียน portfolio description

ผลงาน: [ชื่อโปรเจค]
ลูกค้า: [ชื่อ]
ประเภทงาน: [design / content / dev / marketing]
สิ่งที่ทำ: [อธิบายสั้นๆ]
ผลลัพธ์: [ตัวเลข — เช่น engagement เพิ่ม X% / ยอดขายเพิ่ม]

เขียนให้:
- 1 ย่อหน้าสรุป
- Challenge: ลูกค้ามีปัญหาอะไร
- Solution: แก้ยังไง
- Result: ผลลัพธ์ที่ได้
- Testimonial (ถ้ามี)
ตั้งราคา

คำนวณราคาที่เหมาะสมกับงาน

PROMPT
Copy
ช่วยตั้งราคา freelance

ประเภทงาน: [อะไร]
รายละเอียดงาน: [scope งาน]
เวลาที่ใช้: [ประมาณกี่ชั่วโมง/วัน]
ระดับประสบการณ์: [มือใหม่ / กลาง / เชี่ยวชาญ]
ตลาดเป้าหมาย: [ลูกค้าไทย / ต่างประเทศ]

ช่วย:
1. คำนวณราคาที่เหมาะสม (ต่อชิ้น + ต่อชั่วโมง)
2. เปรียบเทียบกับราคาตลาด
3. เสนอ pricing packages (Basic / Standard / Premium)
4. สิ่งที่ควรรวม/ไม่รวมในราคา
Contract Draft

ร่างสัญญาจ้างงาน freelance

PROMPT
Copy
ร่างสัญญาจ้างงาน freelance

ผู้ว่าจ้าง: [ชื่อลูกค้า/บริษัท]
ผู้รับจ้าง: [ชื่อเรา]
งาน: [รายละเอียดงาน]
ราคา: [จำนวนเงิน]
ระยะเวลา: [วันเริ่ม — วันจบ]

เงื่อนไข:
- จำนวนครั้งแก้ไข: [กี่ครั้ง]
- การชำระเงิน: [มัดจำ X% ก่อนเริ่ม / ที่เหลือหลังส่งมอบ]
- ลิขสิทธิ์: [โอนให้ลูกค้า / เก็บไว้ + ให้ license]
- การยกเลิก: [เงื่อนไข]

ร่างเป็นภาษาไทย กึ่งทางการ
Client Onboarding Checklist

checklist สำหรับเริ่มงานกับลูกค้าใหม่

PROMPT
Copy
สร้าง client onboarding checklist

ประเภทงาน: [อะไร]
ลูกค้าใหม่: [ชื่อ]

สร้าง checklist:
1. ก่อนเริ่มงาน (ข้อมูลที่ต้องขอจากลูกค้า)
2. kick-off (สิ่งที่ต้องคุยกัน)
3. ระหว่างทำงาน (checkpoint + update)
4. ส่งมอบ (format + ช่องทาง)
5. หลังส่งมอบ (feedback + invoice)

รวม: template ข้อความทักลูกค้าครั้งแรก
Testimonial Request

ขอ testimonial จากลูกค้าแบบไม่อึดอัด

PROMPT
Copy
เขียนข้อความขอ testimonial จากลูกค้า

ลูกค้า: [ชื่อ]
งานที่ทำให้: [อะไร]
ส่งทาง: [LINE / Email]

เขียน 2 แบบ:
1. แบบง่ายๆ (ขอแค่ 2-3 ประโยค)
2. แบบมี guideline (ส่งคำถาม 3-5 ข้อให้ตอบ)

คำถามที่แนะนำ:
- ก่อนจ้างมีปัญหาอะไร?
- ผลลัพธ์ที่ได้?
- จะแนะนำให้คนอื่นมั้ย?

Tone: ขอบคุณจริงๆ ไม่กดดัน
Upsell Pitch

เสนอบริการเพิ่มเติมให้ลูกค้าเก่า

PROMPT
Copy
เขียน upsell pitch

ลูกค้า: [ชื่อ]
งานที่ทำให้แล้ว: [อะไร]
บริการเพิ่มที่อยากเสนอ: [อะไร]
ราคาเพิ่ม: [ราคา]

เขียนข้อความ:
1. ขอบคุณ + อ้างอิงงานที่ทำแล้ว
2. สิ่งที่สังเกตเห็น (โอกาสที่ลูกค้ายังไม่ได้ทำ)
3. เสนอบริการเพิ่ม + ราคาพิเศษสำหรับลูกค้าเก่า
4. CTA (นัดคุย / ส่ง proposal)

Tone: ให้คุณค่า ไม่ใช่ขายของ
Invoice Template

สร้าง invoice ส่งลูกค้าแบบครบถ้วน

PROMPT
Copy
สร้าง invoice

จาก: [ชื่อเรา — ที่อยู่ — เลขที่ผู้เสียภาษี]
ถึง: [ชื่อลูกค้า — ที่อยู่]
เลขที่ invoice: [INV-XXXX]
วันที่: [วันที่]

รายการ:
1. [รายการ] — [จำนวน] x [ราคาต่อหน่วย] = [รวม]
2. [รายการ] — [จำนวน] x [ราคาต่อหน่วย] = [รวม]

ยอดรวม: [จำนวน]
VAT 7%: [คำนวณ / ไม่มี]
รวมทั้งสิ้น: [จำนวน]

ชำระเงิน: [โอนเข้าบัญชี — ชื่อ — เลขที่]
กำหนดชำระ: [ภายใน X วัน]
NEXT IN LEARNING PATH

📢 Ads Optimizer — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 📢 Ads Optimizer — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-ads

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
📢 Ads Optimizer — คำสั่งสำเร็จรูป
📢 Ads Optimizer — คำสั่งสำเร็จรูป
8 min
ads
prompt
สำเร็จรูป
1
📢 Ads Optimizer — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียน Ad Copy FB/IG

เขียน ad copy 5 ตัว สำหรับ A/B test

PROMPT
Copy
เขียน ad copy สำหรับ Facebook/IG Ads

สินค้า: [ชื่อ]
ราคา: [ราคา]
ข้อเสนอ: [ส่วนลด / ทดลองฟรี / ของแถม]
กลุ่มเป้าหมาย: [ใคร — อายุ ความสนใจ]
เป้าหมายแคมเปญ: [ยอดขาย / lead gen / traffic]

เขียน 5 ตัว:
1. แบบ pain point (ชี้ปัญหา → solution)
2. แบบ benefit-first (ผลลัพธ์ที่ได้)
3. แบบ social proof (คนอื่นใช้แล้ว)
4. แบบ urgency (เวลาจำกัด)
5. แบบ storytelling (เล่าเรื่อง)

แต่ละตัว: headline + primary text + CTA
A/B Test Variations

สร้าง variations 5 แบบสำหรับ test

PROMPT
Copy
สร้าง A/B test variations 5 แบบ

Ad เดิม:
Headline: [headline เดิม]
Primary text: [เนื้อหาเดิม]
CTA: [CTA เดิม]

สร้าง variations:
1. เปลี่ยน headline (3 แบบ)
2. เปลี่ยน primary text (3 แบบ)
3. เปลี่ยน CTA (3 แบบ)
4. เปลี่ยน angle ทั้งหมด (2 แบบ)

อธิบาย: ทำไมแต่ละ variation น่าจะ perform ดี
Audience Targeting Strategy

วาง targeting ให้ตรงกลุ่มที่สุด

PROMPT
Copy
วาง audience targeting strategy

สินค้า: [อะไร]
ราคา: [ราคา]
ลูกค้าปัจจุบัน: [อธิบายคร่าวๆ]
งบ/เดือน: [งบ]
แพลตฟอร์ม: [FB/IG / Google / TikTok]

สร้าง 3 audiences:
1. Core audience (interest-based)
2. Lookalike audience
3. Retargeting audience

แต่ละ audience:
- Demographics
- Interests / behaviors
- ขนาดกลุ่มที่เหมาะ
- งบที่แนะนำ
สรุป Ad Report

สรุปผลแคมเปญโฆษณาให้เข้าใจง่าย

PROMPT
Copy
สรุป ad report ให้หน่อย

ข้อมูล:
- แคมเปญ: [ชื่อ]
- ระยะเวลา: [วันที่ — ถึงวันที่]
- งบที่ใช้: [จำนวน]
- Reach: [ตัวเลข]
- Impressions: [ตัวเลข]
- Clicks: [ตัวเลข]
- CTR: [%]
- Conversions: [ตัวเลข]
- CPA: [ราคา]
- ROAS: [ตัวเลข]

สรุป:
1. ภาพรวมผลลัพธ์ (ดีหรือไม่ดี)
2. สิ่งที่ทำดี
3. สิ่งที่ควรปรับ
4. Action items สำหรับ sprint ถัดไป
Retargeting Message

เขียนข้อความสำหรับ retarget คนที่เคยสนใจ

PROMPT
Copy
เขียน retargeting ad

สินค้า: [ชื่อ]
กลุ่มที่จะ retarget:
- คนที่เข้าเว็บแต่ไม่ซื้อ
- คนที่ add to cart แล้วไม่จ่าย
- คนที่ดู ad แต่ไม่คลิก

เขียน ad copy แต่ละกลุ่ม:
1. Reminder (เตือนว่ายังสนใจอยู่มั้ย)
2. Incentive (ให้ส่วนลดเพิ่ม)
3. Social proof (คนอื่นซื้อแล้ว)
4. Urgency (ใกล้หมด/ราคาจะขึ้น)
Ad Creative Brief

brief สำหรับทีม creative ทำรูป/วิดีโอ

PROMPT
Copy
เขียน ad creative brief

สินค้า: [ชื่อ]
แคมเปญ: [ชื่อ]
แพลตฟอร์ม: [FB/IG/TikTok]
Format: [รูป / วิดีโอ / carousel]
ขนาด: [1080x1080 / 1080x1350 / 9:16]

Brief:
1. Key message (1 ประโยค)
2. Headline บนรูป
3. Visual direction (อธิบายรูปที่ต้องการ)
4. สี/mood
5. CTA บนรูป
6. โลโก้/branding ที่ต้องใส่
7. Reference (ตัวอย่างที่ชอบ)
Budget Allocation Plan

วางแผนแบ่งงบโฆษณาให้คุ้มที่สุด

PROMPT
Copy
วางแผน budget allocation

งบรวม/เดือน: [จำนวน] บาท
ธุรกิจ: [ประเภท]
เป้าหมาย: [ยอดขาย / lead / awareness]
ช่องทางที่ใช้: [FB/IG / Google / TikTok / LINE]

ช่วย:
1. แบ่งงบแต่ละช่องทาง (% + จำนวนเงิน)
2. แบ่งงบตาม funnel (awareness / consideration / conversion)
3. งบสำหรับ testing vs scaling
4. KPI ที่ควร track
5. เมื่อไหร่ควรปรับงบ
ROAS Analysis

วิเคราะห์ ROAS และหาทางเพิ่ม

PROMPT
Copy
วิเคราะห์ ROAS

ข้อมูล:
- ยอดขายจากโฆษณา: [จำนวน] บาท
- งบโฆษณา: [จำนวน] บาท
- ROAS ปัจจุบัน: [ตัวเลข]x
- ROAS เป้าหมาย: [ตัวเลข]x
- ต้นทุนสินค้า: [%]
- margin: [%]

วิเคราะห์:
1. ROAS ปัจจุบันดีหรือไม่ (เทียบกับ benchmark)
2. Break-even ROAS คือเท่าไหร่
3. วิธีเพิ่ม ROAS 5 ข้อ
4. สิ่งที่ควร cut
5. scaling strategy
NEXT IN LEARNING PATH

⚡ AI Automation — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# ⚡ AI Automation — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-automation

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
⚡ AI Automation — คำสั่งสำเร็จรูป
⚡ AI Automation — คำสั่งสำเร็จรูป
7 min
automation
ai
prompt
สำเร็จรูป
1
⚡ AI Automation — คำสั่งสำเร็จรูป

รวม 7 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

ออกแบบ Workflow Automation

ออกแบบระบบ automation สำหรับงานซ้ำๆ

PROMPT
Copy
ออกแบบ workflow automation

งานที่ทำซ้ำ: [อธิบายงาน]
ความถี่: [ทุกวัน / ทุกสัปดาห์ / เมื่อมี trigger]
เครื่องมือที่ใช้อยู่: [Notion / Google Sheets / LINE / etc.]

ออกแบบ:
1. Trigger: อะไรเริ่มต้น flow
2. Steps: แต่ละขั้นตอนทำอะไร
3. Tools: ใช้เครื่องมืออะไรเชื่อม
4. Output: ผลลัพธ์สุดท้ายคืออะไร
5. Error handling: ถ้าผิดพลาดทำยังไง
Chatbot Flow

ออกแบบ flow สำหรับ chatbot ตอบลูกค้า

PROMPT
Copy
ออกแบบ chatbot flow

ธุรกิจ: [ชื่อ]
ช่องทาง: [LINE / FB Messenger / เว็บ]
เป้าหมาย: [ตอบคำถาม / จอง / ขาย / support]

FAQ ที่พบบ่อย:
1. [คำถาม 1]
2. [คำถาม 2]
3. [คำถาม 3]

ออกแบบ flow:
1. Welcome message
2. Menu หลัก (3-5 ตัวเลือก)
3. แต่ละ path → คำตอบ + next step
4. จุดที่ต้องส่งต่อคน
5. Closing message
Email Automation Sequence

ออกแบบ automated email ตาม trigger

PROMPT
Copy
ออกแบบ email automation

Trigger: [สมัครสมาชิก / ซื้อสินค้า / หยุดใช้งาน]
ธุรกิจ: [ชื่อ]
เป้าหมาย: [nurture / onboard / re-engage]

Sequence [5-7 ฉบับ]:
แต่ละฉบับ:
- Delay: ส่งหลัง trigger กี่วัน
- Subject line
- เนื้อหาหลัก (2-3 ย่อหน้า)
- CTA
- Condition: ส่งต่อหรือหยุด (if opened/clicked)
Report Automation

ออกแบบระบบสร้างรายงานอัตโนมัติ

PROMPT
Copy
ออกแบบระบบ report automation

รายงานอะไร: [sales report / marketing report / inventory]
ข้อมูลมาจาก: [Google Sheets / CRM / Facebook Ads / etc.]
ส่งให้ใคร: [หัวหน้า / ทีม / ลูกค้า]
ความถี่: [ทุกวัน / ทุกสัปดาห์ / ทุกเดือน]

ออกแบบ:
1. ข้อมูลที่ต้องดึง
2. การคำนวณ/วิเคราะห์
3. Format รายงาน
4. ช่องทางส่ง (Email / LINE / Sheets)
5. Template ข้อความ
Task Delegation System

ระบบแจกงานอัตโนมัติตาม workflow

PROMPT
Copy
ออกแบบระบบ task delegation

ทีม: [กี่คน — ตำแหน่ง]
งานที่ต้องแจก: [ประเภทงาน]
เครื่องมือ: [Notion / Trello / Asana / Google Sheets]

ออกแบบ:
1. เมื่อมีงานใหม่เข้ามา → แจกใคร (กฎ)
2. Notification ให้คนที่ได้งาน
3. Deadline tracking
4. Status updates
5. Escalation (ถ้างานไม่เสร็จตามเวลา)
6. Weekly summary
Notification Bot

สร้าง bot แจ้งเตือนอัตโนมัติ

PROMPT
Copy
ออกแบบ notification bot

แจ้งเตือนอะไร: [ออเดอร์ใหม่ / งานที่ต้องทำ / KPI / etc.]
ส่งทาง: [LINE / Telegram / Slack / Email]
Trigger: [เมื่อมี event / ตามเวลา]

ออกแบบ:
1. เงื่อนไขที่ trigger
2. ข้อความที่ส่ง (template)
3. ข้อมูลที่ต้องแสดง
4. ปุ่ม/action ที่กดได้
5. ความถี่ + ช่วงเวลาที่ส่ง (ไม่รบกวนตอนดึก)
Scheduling Automation

ระบบจัดการนัดหมาย/ตารางอัตโนมัติ

PROMPT
Copy
ออกแบบระบบ scheduling automation

ประเภท: [นัดลูกค้า / จัดเวร / ตาราง content / ตาราง meeting]
จำนวนคน: [กี่คน]
เครื่องมือ: [Google Calendar / Notion / Calendly]

ออกแบบ:
1. วิธีจองนัด (link / form / bot)
2. ตรวจสอบ availability อัตโนมัติ
3. Confirmation message
4. Reminder (ก่อนนัด 1 วัน + 1 ชั่วโมง)
5. Follow-up หลังนัด
6. Reschedule/cancel flow
NEXT IN LEARNING PATH

💻 Web/App Builder — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 💻 Web/App Builder — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-web

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
💻 Web/App Builder — คำสั่งสำเร็จรูป
💻 Web/App Builder — คำสั่งสำเร็จรูป
7 min
web
app
prompt
สำเร็จรูป
1
💻 Web/App Builder — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียน Wireframe Spec

อธิบาย wireframe ให้ designer/dev เข้าใจ

PROMPT
Copy
เขียน wireframe spec

โปรเจค: [ชื่อ]
ประเภท: [เว็บ / app / landing page]
หน้าที่ต้องการ: [หน้าอะไรบ้าง]

แต่ละหน้า:
1. ชื่อหน้า
2. Layout (อธิบายว่ามีอะไร ตรงไหน)
3. Elements (ปุ่ม / form / รูป / text)
4. User flow (กดอะไร → ไปไหน)
5. หมายเหตุสำหรับ designer
Feature List

สร้าง feature list แบ่ง MVP vs Nice-to-have

PROMPT
Copy
สร้าง feature list

โปรเจค: [ชื่อ]
ประเภท: [เว็บ / app / SaaS]
กลุ่มเป้าหมาย: [ใคร]
ปัญหาที่แก้: [pain point]

สร้าง:
1. MVP features (ต้องมี — launch ได้เลย)
2. Phase 2 (ทำหลัง launch)
3. Nice-to-have (ทำเมื่อมีเวลา)

แต่ละ feature:
- ชื่อ feature
- อธิบาย 1 บรรทัด
- Priority (High/Medium/Low)
- ระดับความยาก (Easy/Medium/Hard)
User Story

เขียน user stories สำหรับ dev team

PROMPT
Copy
เขียน user stories

โปรเจค: [ชื่อ]
Feature: [ชื่อ feature]
User type: [ผู้ใช้ทั่วไป / admin / ลูกค้า]

เขียน 5-8 user stories:
Format: "ในฐานะ [user type] ฉันต้องการ [action] เพื่อ [benefit]"

แต่ละ story:
- Acceptance criteria (3-5 ข้อ)
- Priority
- Story points (1/2/3/5/8)
Landing Page Copy

เขียน copy สำหรับ landing page ทั้งหน้า

PROMPT
Copy
เขียน landing page copy

ชื่อ product: [ชื่อ]
ประเภท: [SaaS / app / service]
ราคา: [ราคา/แพลน]
กลุ่มเป้าหมาย: [ใคร]
จุดเด่น: [USP 3 ข้อ]

เขียนทุก section:
1. Hero (headline + sub + CTA)
2. Problem (pain points 3 ข้อ)
3. Solution (product แก้ยังไง)
4. Features (5-6 features + icon คำอธิบาย)
5. How it works (3 steps)
6. Testimonials (3 quotes)
7. Pricing
8. FAQ (5 ข้อ)
9. Final CTA
Tech Stack Recommendation

แนะนำ tech stack ที่เหมาะกับโปรเจค

PROMPT
Copy
แนะนำ tech stack

โปรเจค: [อธิบายสั้นๆ]
ประเภท: [เว็บ / app / SaaS / e-commerce]
ขนาดทีม: [กี่คน — skill level]
งบ: [ต่ำ / กลาง / สูง]
เวลา: [กี่เดือน]
Scale: [ผู้ใช้กี่คน]

แนะนำ:
1. Frontend
2. Backend
3. Database
4. Hosting
5. Auth
6. Payment (ถ้ามี)
7. Analytics

อธิบาย: ทำไมเลือก + ทางเลือกอื่น + ค่าใช้จ่าย
API Design

ออกแบบ API endpoints

PROMPT
Copy
ออกแบบ API

โปรเจค: [ชื่อ]
Resource หลัก: [เช่น users, products, orders]

ออกแบบ endpoints:
แต่ละ resource:
- GET (list + single)
- POST (create)
- PUT/PATCH (update)
- DELETE

แต่ละ endpoint:
- Method + URL
- Request body (JSON)
- Response body (JSON)
- Status codes
- Auth required?
Database Schema

ออกแบบ database schema

PROMPT
Copy
ออกแบบ database schema

โปรเจค: [อธิบายสั้นๆ]
ข้อมูลที่ต้องเก็บ: [อะไรบ้าง]
Database: [PostgreSQL / MySQL / MongoDB]

ออกแบบ:
1. Tables/Collections
2. Fields + types
3. Relations (1:1, 1:N, N:N)
4. Indexes ที่ควรมี
5. Sample data

Format: SQL CREATE TABLE หรือ Prisma schema
Deployment Checklist

checklist ก่อน deploy ขึ้น production

PROMPT
Copy
สร้าง deployment checklist

โปรเจค: [ชื่อ]
Stack: [เช่น Next.js + Vercel + Neon]
Domain: [domain]

Checklist:
1. Code review
2. Environment variables
3. Database migration
4. Build test
5. Security check
6. Performance check
7. Backup
8. DNS/SSL
9. Monitoring setup
10. Rollback plan

แต่ละข้อ: อธิบายสั้นๆ ว่าเช็คอะไร
NEXT IN LEARNING PATH

📚 E-book / Digital Product — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 📚 E-book / Digital Product — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-ebook

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
📚 E-book / Digital Product — คำสั่งสำเร็จรูป
📚 E-book / Digital Product — คำสั่งสำเร็จรูป
7 min
ebook
digital-product
prompt
สำเร็จรูป
1
📚 E-book / Digital Product — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

เขียน Outline หนังสือ

สร้าง outline หนังสือ/e-book ครบทุกบท

PROMPT
Copy
สร้าง outline สำหรับ e-book

ชื่อ: [ชื่อหนังสือ]
หัวข้อ: [เกี่ยวกับอะไร]
กลุ่มเป้าหมาย: [ใคร]
จำนวนหน้า: [50 / 100 / 200]
Level: [เริ่มต้น / กลาง / สูง]

สร้าง:
1. ชื่อบท (8-12 บท)
2. แต่ละบท: หัวข้อย่อย 3-5 ข้อ
3. Key takeaway ของแต่ละบท
4. Exercise/worksheet (ถ้าเหมาะ)
5. จำนวนหน้าต่อบท
Draft บทที่ 1

เขียน draft บทแรก จากข้อมูลที่มี

PROMPT
Copy
เขียน draft บทที่ 1

ชื่อหนังสือ: [ชื่อ]
ชื่อบท: [ชื่อบทที่ 1]
หัวข้อย่อย:
1. [หัวข้อ 1]
2. [หัวข้อ 2]
3. [หัวข้อ 3]

Key message: [สิ่งที่ผู้อ่านต้องได้จากบทนี้]
Tone: [สอน / เล่าเรื่อง / practical]
ความยาว: [2000-3000 คำ]

รวม:
- Opening hook
- เนื้อหาตามหัวข้อ
- ตัวอย่างจริง
- สรุปท้ายบท
Sales Page Copy

เขียน copy หน้าขาย digital product

PROMPT
Copy
เขียน sales page copy

Product: [ชื่อ e-book/course]
ราคา: [ราคา]
ราคาเดิม: [ราคาก่อนลด] (ถ้ามี)
กลุ่มเป้าหมาย: [ใคร]

เขียน:
1. Headline (จับใจ)
2. Pain points (3-5 ข้อ ที่ผู้อ่านเจอ)
3. "จะดีแค่ไหนถ้า..." (paint the picture)
4. สิ่งที่ได้ (bullet points 7-10 ข้อ)
5. สารบัญ/เนื้อหาที่ได้
6. เกี่ยวกับผู้เขียน
7. Testimonials (format)
8. Guarantee
9. FAQ
10. CTA + pricing
Pricing Strategy

กำหนดราคาและ tier ที่เหมาะสม

PROMPT
Copy
ช่วยตั้งราคา digital product

Product: [ชื่อ]
ประเภท: [e-book / course / template / membership]
เนื้อหา: [อธิบายคร่าวๆ]
กลุ่มเป้าหมาย: [ใคร — กำลังซื้อ]
คู่แข่ง: [ราคาของคู่แข่ง]

ช่วย:
1. ราคาที่เหมาะสม + เหตุผล
2. Pricing tiers (3 แพลน)
3. Early bird / launch price
4. Bundle options
5. Upsell strategy
Launch Plan

วางแผน launch digital product

PROMPT
Copy
วางแผน launch

Product: [ชื่อ]
วัน launch: [วันที่]
กลุ่มเป้าหมาย: [ใคร]
ช่องทาง: [FB/IG/LINE/Email]
งบ marketing: [จำนวน]

วางแผน:
1. Pre-launch (2-4 สัปดาห์ก่อน)
2. Launch week
3. Post-launch (1-2 สัปดาห์หลัง)

แต่ละ phase:
- Content ที่ต้องทำ
- Email ที่ต้องส่ง
- Ads ที่ต้องยิง
- Milestone + KPI
Email Sequence สำหรับ Launch

ชุด email 7 ฉบับสำหรับ launch product

PROMPT
Copy
สร้าง launch email sequence 7 ฉบับ

Product: [ชื่อ]
ราคา: [ราคา]
วัน launch: [วันที่]

Sequence:
1. [D-7] Teaser (กำลังจะมีอะไร)
2. [D-3] Story (ทำไมถึงสร้างสิ่งนี้)
3. [D-1] Early bird (สิทธิพิเศษ)
4. [D-Day] Launch! (เปิดขาย)
5. [D+1] Social proof (คนซื้อแล้วพูดอะไร)
6. [D+3] FAQ (ตอบข้อสงสัย)
7. [D+5] Last chance (ปิดราคาพิเศษ)

แต่ละฉบับ: subject + preview + body + CTA
Bonus Content Ideas

ไอเดีย bonus สำหรับเพิ่มมูลค่า

PROMPT
Copy
brainstorm bonus content ideas

Product หลัก: [ชื่อ — อธิบายสั้นๆ]
ราคา: [ราคา]
กลุ่มเป้าหมาย: [ใคร]

ให้ 8-10 ไอเดีย bonus:
แต่ละอัน:
- ชื่อ bonus
- format (PDF / video / template / checklist)
- อธิบาย 1 บรรทัด
- มูลค่าสมมุติ
- ใช้เวลาสร้างนานแค่ไหน

เน้น: ของที่ทำง่าย แต่ perceived value สูง
Upsell Strategy

วาง strategy ขายเพิ่มหลังซื้อ

PROMPT
Copy
วาง upsell strategy

Product หลัก: [ชื่อ — ราคา]
ลูกค้าที่ซื้อแล้ว: [กี่คน]

สร้าง upsell path:
1. Order bump (ซื้อพร้อมกัน — ราคาพิเศษ)
2. One-time offer (หลังซื้อทันที)
3. Follow-up upsell (หลัง 7 วัน)
4. Cross-sell (สินค้าอื่นที่เกี่ยวข้อง)

แต่ละ step:
- Product อะไร
- ราคา
- ข้อความ/copy
- Conversion rate ที่คาดหวัง
NEXT IN LEARNING PATH

🤖 AI Tools Builder — คำสั่งสำเร็จรูป

Powered by Mew Social


---

# 🤖 AI Tools Builder — คำสั่งสำเร็จรูป

Source: https://ask.mewsocial.com/browse/openclaw/oc-prompts/prompt-aitools

ask.mewsocial
Steanpong Suksakorm
MY ROOMS
C
Claude Cowork
O
Openclaw
M
Machine Series
Openclaw
คำสั่งสำเร็จรูป
🤖 AI Tools Builder — คำสั่งสำเร็จรูป
🤖 AI Tools Builder — คำสั่งสำเร็จรูป
7 min
ai-tools
builder
prompt
สำเร็จรูป
1
🤖 AI Tools Builder — คำสั่งสำเร็จรูป

รวม 8 คำสั่งสำเร็จรูป copy แล้วส่งให้ AI ใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ตามธุรกิจของคุณ

💡

กดที่ code block แล้ว copy ไปวางใน Telegram ได้เลย — แก้ข้อมูลในวงเล็บ [ ] ให้ตรงกับธุรกิจของคุณ

ออกแบบ AI Tool Concept

conceptualize AI tool ตั้งแต่ idea ถึง spec

PROMPT
Copy
ออกแบบ AI tool concept

ไอเดีย: [AI ทำอะไร — อธิบายคร่าวๆ]
กลุ่มเป้าหมาย: [ใคร]
ปัญหาที่แก้: [pain point]

ช่วย:
1. ชื่อ tool (3 ตัวเลือก)
2. Tagline
3. Feature หลัก 5 อัน
4. User flow (step-by-step)
5. Input อะไร → Output อะไร
6. ทำด้วย stack อะไรได้บ้าง
7. MVP scope (ทำอะไรก่อน)
8. Monetization (ขายยังไง)
เขียน System Prompt

เขียน system prompt สำหรับ AI agent/chatbot

PROMPT
Copy
เขียน system prompt

AI ชื่อ: [ชื่อ]
หน้าที่: [ทำอะไร]
กลุ่มผู้ใช้: [ใคร]
Tone: [professional / friendly / casual]
ภาษา: [ไทย / อังกฤษ / ทั้งคู่]

ต้องมี:
1. บทบาทของ AI (เป็นใคร)
2. สิ่งที่ทำได้ (capabilities)
3. สิ่งที่ห้ามทำ (boundaries)
4. format การตอบ
5. ตัวอย่างการตอบที่ดี 3 แบบ
6. ตัวอย่างการตอบที่ไม่ดี 2 แบบ
7. edge cases
Prompt Chain Design

ออกแบบ chain of prompts ที่ทำงานต่อกัน

PROMPT
Copy
ออกแบบ prompt chain

เป้าหมาย: [ผลลัพธ์สุดท้ายที่ต้องการ]
Input: [ข้อมูลตั้งต้น]

ออกแบบ chain:
Step 1: [Prompt อะไร → Output อะไร]
Step 2: [เอา output step 1 → Prompt อะไร → Output อะไร]
Step 3: [ต่อเนื่อง...]
...
Final: [ผลลัพธ์สุดท้าย]

แต่ละ step:
- Prompt template
- Expected output format
- Validation (เช็คว่า output ถูกต้อง)
- Fallback (ถ้าไม่ได้ผลลัพธ์ที่ต้องการ)
Evaluation Criteria

สร้างเกณฑ์ประเมิน output ของ AI

PROMPT
Copy
สร้างเกณฑ์ประเมิน AI output

AI ทำอะไร: [task ที่ AI ทำ]
Output: [ผลลัพธ์ที่ได้]

สร้าง evaluation rubric:
1. Accuracy (ความถูกต้อง) — เกณฑ์
2. Relevance (ตรงประเด็น) — เกณฑ์
3. Completeness (ครบถ้วน) — เกณฑ์
4. Tone/Style (เหมาะสม) — เกณฑ์
5. Actionability (นำไปใช้ได้) — เกณฑ์

Scoring: 1-5 แต่ละข้อ
Pass threshold: [คะแนนต่ำสุดที่ยอมรับ]
ตัวอย่าง output ที่ดี vs ไม่ดี
Use Case Documentation

เขียน use case doc สำหรับ AI tool

PROMPT
Copy
เขียน use case documentation

Tool: [ชื่อ AI tool]

เขียน 5 use cases:
แต่ละ use case:
1. ชื่อ use case
2. Persona (ใครใช้)
3. สถานการณ์ (context)
4. ขั้นตอนการใช้ (step-by-step)
5. Input ตัวอย่าง
6. Output ตัวอย่าง
7. ผลลัพธ์ที่ได้ (before/after)
8. เวลาที่ประหยัดได้
Onboarding Guide

เขียน guide สอนใช้ AI tool

PROMPT
Copy
เขียน onboarding guide

Tool: [ชื่อ]
กลุ่มผู้ใช้: [ใคร — tech level]

สร้าง guide:
1. Welcome (tool ทำอะไรได้)
2. Quick Start (3 steps ใช้ครั้งแรก)
3. Basic features (5 features + วิธีใช้)
4. Tips & tricks (5 ข้อ)
5. FAQ (5 คำถาม)
6. Troubleshooting (3 ปัญหาที่เจอบ่อย)

Tone: ง่ายๆ ทำตามได้เลย
Format: step-by-step + screenshots description
Pricing Model

ออกแบบ pricing model สำหรับ AI product

PROMPT
Copy
ออกแบบ pricing model

Product: [ชื่อ AI tool]
ต้นทุน API/เดือน: [ประมาณ]
กลุ่มเป้าหมาย: [ใคร — กำลังซื้อ]
คู่แข่ง: [ชื่อ — ราคา]

ออกแบบ:
1. Free tier (มีอะไรบ้าง + limit)
2. Pro tier (ราคา + features)
3. Enterprise (ราคา + features)

เพิ่มเติม:
- Usage-based vs flat rate
- Annual discount
- Trial period
- Revenue projection (100/500/1000 users)
Competitive Analysis

วิเคราะห์คู่แข่งในตลาด AI tools

PROMPT
Copy
วิเคราะห์คู่แข่ง AI tools

Tool ของเรา: [ชื่อ — ทำอะไร]
คู่แข่ง:
1. [ชื่อ tool 1]
2. [ชื่อ tool 2]
3. [ชื่อ tool 3]

วิเคราะห์:
- Feature comparison (ตาราง)
- Pricing comparison
- Target audience
- จุดแข็ง-จุดอ่อนแต่ละตัว
- Gap ที่เราเข้าได้
- Positioning strategy
- Differentiation (ทำไมต้องเลือกเรา)
🔒

AI Money Machine

เปลี่ยน content เป็นเงินล้าน? สอนทุกขั้นตอน

ดูเพิ่มเติมที่คลังแสง AI →
Powered by Mew Social
