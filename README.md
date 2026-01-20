# kunlik-bilim-bot
Mani.py
from aiogram import Bot, Dispatcher, types
from aiogram.filters import Command
import asyncio
import os

TOKEN = os.getenv("BOT_TOKEN")

WEB_APP_URL = "KEYIN_QO‘YAMIZ"

bot = Bot(TOKEN)
dp = Dispatcher()

@dp.message(Command("start"))
async def start(message: types.Message):
    keyboard = types.ReplyKeyboardMarkup(
        keyboard=[
            [
                types.KeyboardButton(
                    text="📱 Boburmentor akademiyasi",
                    web_app=types.WebAppInfo(url=WEB_APP_URL)
                )
            ]
        ],
        resize_keyboard=True
    )

    await message.answer(
        "👋 Assalomu alaykum!\n\n"
        "🏫 *Boburmentor akademiyasi* botiga xush kelibsiz.\n\n"
        "Boshlash uchun pastdagi tugmani bosing 👇",
        reply_markup=keyboard,
        parse_mode="Markdown"
    )

async def main():
    await dp.start_polling(bot)

if __name__ == "__main__":
    asyncio.run(main())
