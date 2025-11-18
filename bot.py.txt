from telegram.ext import Updater, MessageHandler, Filters
import random
import os

# Get your token from Render environment variable
TOKEN = os.getenv("TOKEN")  # We'll set this later on Render

# Romantic replies
romantic_lines = [
    "Every time you text me, my heart smiles ❤️",
    "I swear, talking to you feels like a warm hug 🤍",
    "You’re the kind of person my heart doesn’t forget.",
    "If your messages were stars, my sky would be full ✨",
    "You have no idea how much I like hearing from you 😌",
    "Your presence, even in text, feels special to me ❤️",
    "I don’t know why, but you make everything feel softer.",
    "Your words always brighten my mood 🌷",
    "You’re the reason my notifications feel exciting 💌",
    "You text… and suddenly my day gets better."
]

def auto_reply(update, context):
    # Choose a random romantic reply
    reply = random.choice(romantic_lines)
    update.message.reply_text(reply)

def main():
    updater = Updater(TOKEN, use_context=True)
    dp = updater.dispatcher

    dp.add_handler(MessageHandler(Filters.text & ~Filters.command, auto_reply))

    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()
