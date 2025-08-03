from telegram import Update, Bot
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, ContextTypes, filters

# Здесь вставь свой токен
TOKEN = "ТВОЙ_ТОКЕН_ЗДЕСЬ"

# Пример команды /start
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Здравствуйте! Это FitMenu Bot.\n\nОтправьте скриншот оплаты, чтобы получить меню.")

# Обработка фото
async def handle_photo(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Спасибо! Ваш скриншот принят. Меню будет отправлено после проверки.")

app = ApplicationBuilder().token(TOKEN).build()
app.add_handler(CommandHandler("start", start))
app.add_handler(MessageHandler(filters.PHOTO, handle_photo))

app.run_polling()
