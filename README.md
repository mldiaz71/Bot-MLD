# Bot-MLD
Código del Bot creado en Discord MLD-MIT
import discord
from discord.ext import commands

# Crea una instancia del bot con un prefijo (por ejemplo, "!")
intents = discord.Intents.default()
intents.message_content = True  # Necesario para leer mensajes

bot = commands.Bot(command_prefix="!", intents=intents)

@bot.event
async def on_ready():
    print(f"Bot conectado como {bot.user}")

@bot.event
async def on_message(message):
    # Evita que el bot responda a sus propios mensajes
    if message.author == bot.user:
        return

    # Si el usuario escribe "hola"
    if message.content.lower() == "hola":
        await message.channel.send("hola")

    # Permite que otros comandos funcionen
    await bot.process_commands(message)

#token del portal de desarrolladores de Discord
bot.run("MTQ5MTgxMDcwMDk0NTkyMDA1MA.Ghqwb0.-odUlqnhBPFNZAnlT7iXDmosDRohKSpFZ3p2aA")
