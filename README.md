# -PyJWT-
from telegram import InlineKeyboardButton, InlineKeyboardMarkup, and ReplyKeyboardMarkup
from telegram.ext import Updater, CommandHandler

def start(update, context):
    # เมนูปุ่ม
    keyboard = [
        [InlineKeyboardButton("สมัครสมาชิก", url="https://example.com/signup"),
         InlineKeyboardButton("เข้ากลุ่ม", url="https://t.me/examplegroup")],
        [InlineKeyboardButton("LINE ฝาก ถอน", url="https://line.me/example"),
         InlineKeyboardButton("ทางเข้าเว็บ 1", url="https://example.com/1"),
         InlineKeyboardButton("ทางเข้าเว็บ 2", url="https://example.com/2")],
        [InlineKeyboardButton("สอบถาม แอดมิน", url="https://t.me/admin"),
         InlineKeyboardButton("ช่วงเวลาแตกดี", callback_data="bonus_time"),
         InlineKeyboardButton("แนวทางบอล", callback_data="football_tips")],
        [InlineKeyboardButton("OnlyFans (18+)", url="https://example.com/onlyfans"),
         InlineKeyboardButton("ปลดปล่อย (18+)", url="https://example.com/free"),
         InlineKeyboardButton("ห้องแดง (18+)", url="https://example.com/redroom")]
    ]

    # ปุ่ม Web App ที่มุมล่างซ้าย
    web_app_button = InlineKeyboardButton("🔗 เปิด Web App", web_app={"url": "https://example.com/webapp"})

    reply_markup = InlineKeyboardMarkup(keyboard + [[web_app_button]])

    update.message.reply_text("เลือกเมนูด้านล่าง:", reply_markup=reply_markup)

# ตั้งค่า Token บอทของพี่
TOKEN = "7849416891:AAGn2nuY_TbkVsoa-3GHdip34jEVVFtRInQ"

updater = Updater(TOKEN, use_context=True)
dp = updater.dispatcher

dp.add_handler(CommandHandler("start", start))

updater.start_polling()
updater.idle()
