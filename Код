from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, filters, ContextTypes

# English idioms to Russian translations
IDIOMS = {
    "break the ice": "растопить лед (разрядить обстановку)",
    "hit the nail on the head": "попасть в точку",
    "under the weather": "нездоровится",
    "once in a blue moon": "очень редко",
    "spill the beans": "раскрыть секрет",
    "bite the bullet": "сжать зубы",
    "let the cat out of the bag": "выдать тайну",
    "costs an arm and a leg": "стоить целое состояние",
    "the ball is in your court": "мяч на твоей стороне",
    "burn the midnight oil": "работать допоздна",
    "piece of cake": "пара пустяков",
    "the best of both worlds": "лучшее из обоих миров",
    "when pigs fly": "когда рак на горе свистнет",
    "barking up the wrong tree": "ошибаться адресом",
    "the early bird catches the worm": "кто рано встает, тому Бог подает",
    "hit the sack": "пойти спать",
    "pull someone's leg": "подшучивать над кем-то",
    "jump on the bandwagon": "присоединиться к моде",
    "throw in the towel": "сдаться",
    "call it a day": "закончить на сегодня",
    "back to the drawing board": "начать с нуля",
    "bite off more than you can chew": "взяться за слишком много",
    "burning the candle at both ends": "работать на износ",
    "by the skin of your teeth": "едва-едва",
    "don't count your chickens before they hatch": "не говори гоп, пока не перепрыгнешь",
    "every cloud has a silver lining": "нет худа без добра",
    "get a taste of your own medicine": "попробовать на себе собственные методы",
    "hit the ground running": "войти в дело с энтузиазмом",
    "let sleeping dogs lie": "не буди лихо, пока оно тихо",
    "make a long story short": "короче говоря",
    "once bitten, twice shy": "обжегшись на молоке, будешь дуть на воду"
}

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    """
    Обрабатывает команду /start и отправляет приветственное сообщение пользователю.

    Args:
        update (Update): Объект обновления, содержащий информацию о сообщении.
        context (ContextTypes.DEFAULT_TYPE): Контекст, содержащий информацию о состоянии бота.
    """
    await update.message.reply_text(
        "Привет! Я помогу тебе выучить английские идиомы.\n"
        "Просто отправь мне идиому, и я переведу её на русский."
    )

async def translate_idiom(update: Update, context: ContextTypes.DEFAULT_TYPE):
    """
    Обрабатывает текстовые сообщения и переводит идиомы с английского на русский.

    Args:
        update (Update): Объект обновления, содержащий информацию о сообщении.
        context (ContextTypes.DEFAULT_TYPE): Контекст, содержащий информацию о состоянии бота.
    """
    text = update.message.text.strip().lower()
    translation = IDIOMS.get(text)
    if translation:
        await update.message.reply_text(f"Перевод: {translation}")
    else:
        await update.message.reply_text("Извините, я не знаю эту идиому. Попробуйте другой.")

def main():
    """
    Основная функция для запуска бота.
    Создает экземпляр приложения и добавляет обработчики команд и сообщений.
    """
    TOKEN = "YOUR_BOT_TOKEN_HERE"  # Замените на ваш токен

    app = ApplicationBuilder().token(TOKEN).build()

    app.add_handler(CommandHandler("start", start))
    app.add_handler(MessageHandler(filters.TEXT & (~filters.COMMAND), translate_idiom))

    print("Bot started ... Ctrl+C to stop.")
    app.run_polling()

if __name__ == "__main__":
    main()
