# food-telegram-bot
my-food-bot/
├── bot.py       # основной код бота
├── requirements.txt
├── Procfile
└── food_db.csv  # база продуктов
python-telegram-bot==13.7
pandas==1.3.5
python-dotenv==0.19.2
worker: python bot.py
import os
from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

TOKEN = os.getenv('TELEGRAM_TOKEN')  # Токен из переменных окружения

def start(update: Update, context: CallbackContext):
    update.message.reply_text("👋 Привет! Я помогу тебе следить за питанием!")

if __name__ == '__main__':
    updater = Updater(TOKEN)
    dp = updater.dispatcher
    dp.add_handler(CommandHandler("start", start))
    updater.start_polling()
    updater.idle()
    
