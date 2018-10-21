#First Discord Bot by Pomf


import discord
import asyncio
import random
import youtube_dl
from discord.ext import commands
from discord.ext.commands import bot
from itertools import cycle
import time
from discord import Game

__all__ = ['random', 'youtube_dl', 'time', 'Game']

bot = commands.Bot(command_prefix=".")
bot.remove_command('help')
status = ["Type '.help' for help!", "with Pomf"]
players = {}
queues = {}
hentai_haven = [
    "http://hentaihaven.org/kanojo-x-kanojo-x-kanojo-episodes-1-3-uncensored-marathon/",
    "http://hentaihaven.org/mankitsu-happening-episode-2/",
    "http://hentaihaven.org/mankitsu-happening-episode-1/",
    "http://hentaihaven.org/baku-ane-otouto-shibocchau-zo-episode-1/",
    "http://hentaihaven.org/nozoki-ana-episode-1/",
    "http://hentaihaven.org/harem-time-episode-1/",
    "http://hentaihaven.org/mankitsu-happening-episode-3-hd/",
    "http://hentaihaven.org/bangable-girl-episode-1/",
    "http://hentaihaven.org/itadaki-seieki-episode-1-unc/",
    "http://hentaihaven.org/mankitsu-happening-episode-4-hd/",
    "http://hentaihaven.org/boy-meets-harem-episode-1/",
    "http://hentaihaven.org/dropout-episode-1/",
    "http://hentaihaven.org/stringendo-episode-5/",
    "http://hentaihaven.org/fuzzy-lips-episode-1-unc/",
    "http://hentaihaven.org/tamashii-insert-episode-1/",
    "http://hentaihaven.org/boku-to-misaki-sensei-episode-1/",
    "http://hentaihaven.org/futabu-mix-futanari-world-episode-1/",
    "http://hentaihaven.org/oppai-heart-episode-2/",
    "http://hentaihaven.org/toshi-densetsu-series-episode-1-hd/",
    "http://hentaihaven.org/stringendo-episode-4/",
    "http://hentaihaven.org/baku-ane-2-otouto-ippai-shibocchau-zo-episode-1/",
    "http://hentaihaven.org/jk-bitch-ni-shiboraretai-episode-1/",
    "http://hentaihaven.org/3ping-lovers-ippu-nisai-no-sekai-e-youkoso-episode-1/",
    "http://hentaihaven.org/dirty-laundry-episode-1/",
    "http://hentaihaven.org/koakuma-kanojo-the-animation-episode-1/",
    "http://hentaihaven.org/toshi-densetsu-series-episode-2/",
    "http://hentaihaven.org/stringendo-episode-6/",
    "http://hentaihaven.org/imouto-paradise-3-episode-2/",
    "http://hentaihaven.org/aku-no-onna-kanbu-episode-2/",
    "http://hentaihaven.org/euphoria-episode-6-hd/",
    "http://hentaihaven.org/euphoria-episode-4/",
    "http://hentaihaven.org/imouto-paradise-3-the-animation-episode-1/",
    "http://hentaihaven.org/oni-chichi-episode-1-hd/",
    "http://hentaihaven.org/tayu-tayu-episode-3/",
    "http://hentaihaven.org/stringendo-episode-8/",
    "http://hentaihaven.org/baku-ane-otouto-shibocchau-zo-directors-cut-episode-1/",
    "http://hentaihaven.org/rance-01-the-quest-for-hikari-episode-3/",
    "http://hentaihaven.org/baka-na-imouto-o-rikou-ni-suru-no-wa-ore-no-xx-dake-na-ken-ni-tsuite-episode-3-hd/",
    "http://hentaihaven.org/namaiki-kissuisou-e-youkoso-episode-1/",
    "http://hentaihaven.org/oni-chichi-refresh-episode-1-hd/",
    "http://hentaihaven.org/toshi-densetsu-series-episode-3/",
    "http://hentaihaven.org/monster-girl-quest-episode-1/",
    "http://hentaihaven.org/futabu-episode-1/",
    "http://hentaihaven.org/jk-bitch-ni-shiboraretai-episode-2/",
    "http://hentaihaven.org/honoo-no-haramase-oppai-ero-appli-gakuen-the-animation-episode-1/",
    "http://hentaihaven.org/pretty-x-cation-the-animation-episode-1/",
    "http://hentaihaven.org/rance-01-the-quest-for-hikari-episode-4/",
    "http://hentaihaven.org/fuzzy-lips-episode-2-uncensored/",
    "http://hentaihaven.org/yarimoku-beach-ni-shuugakuryokou-episode-1/",
    "http://hentaihaven.org/daisuki-na-mama-episode-1/",
    "https://hanime.tv/hentai-videos/shoujo-ramune-1",
    "https://hanime.tv/hentai-videos/shoujo-ramune-2",
    "https://hanime.tv/hentai-videos/shoujo-ramune-3",
    "https://hanime.tv/hentai-videos/shoujo-ramune-4"
]

def check_queue(id):
    if queues[id] != []:
        player = queues[id].pop(0)
        players[id] = player
        player.start

async def change_status():
    await bot.wait_until_ready()
    msgs = cycle(status)

    while not bot.is_closed:
        current_status = next(msgs)
        await bot.change_presence(game=discord.Game(name=current_status))
        await asyncio.sleep(8)

print("[TomatoBot by Pomf]")

@bot.event
async def on_ready():
    print("Bot Successfully Connected!")

#@bot.event
#async def raisin():
#    embed = discord.Embed(title="Rum Raisin?", color=0xff0000)
#    embed.set_image(url='')

@bot.command(pass_context=True)
async def help():
    embed = discord.Embed(title="TomatoBot Help Menu", color=0xff0000)
    embed.add_field(name="Basic Commands",
                    value= ".help: ```Displays this menu```.info: ```@ a user after this command, and it will"
                    " provide their discord info```.serverinfo: ```Pretty self-explanitory; it will provide information"
                    " about the server it is in```.say: ```This command will repeat any text that is entered after it"
                    "```.hentai: ```Don't know what to watch? AND you're a degerate? Luckily, this command is for you."
                    " It will randomly link 1 of 50 stored videos from Hentai Haven. And for those of you that are REAL"
                    " degenerates, I have also linked all episodes of Shoujo Ramune. Enjoy, you fucking losers```"
                    ".pomf: ```What Would Pomf Say? (chooses a random quote by yours truly)```.zomb: ```Epic or"
                    " Not Epic? This command will decide that for you.```.ayame: ```Random quotes from ayame```")
    embed.set_thumbnail(url="https://i.pinimg.com/originals/f9/0e/15/f90e154d9ac8bba3c3810b499616cfff.jpg")
    embed.add_field(name="Music Commands",
                    value=
                    #".join: ```Only works if you're in a voice channel. The bot will join the voice channel you"
                    #" are currently in```"
                    "(***like anyone would even use these***)\n.play: ```Insert a YouTube link after this command and"
                    " it will play the audio of said"
                    " video. (Must be in voice channel) (Only works with links."
                    ") (.queue function disabled, but isn't really needed anyway)```"
                    #".queue: ```Use this function to play a song after the song"
                    #" that is currently playing. (Again,"
                    #" link it) (Command is sort of buggy as of now so don't bother; just use .play)```"
                    ".pause: ```Pauses the current"
                    " song that is being played```.stop: ```Stops playing the song that is currently streaming```"
                    ".resume: ```Resumes the song that was paused```.leave: ```The bot will stop playing music and"
                    " leave the voice channel```")
    await bot.say(embed=embed)

#@bot.command(pass_context=True)
#async def join(ctx):
#    channel = ctx.message.author.voice.voice_channel
#    await bot.join_voice_channel(channel)

@bot.command(pass_context=True)
async def leave(ctx):
    server = ctx.message.server
    voice_client = bot.voice_client_in(server)
    await voice_client.disconnect()

@bot.command(pass_context=True)
async def play(ctx, url):
    channel = ctx.message.author.voice.voice_channel
    await bot.join_voice_channel(channel)
    server = ctx.message.server
    voice_client = bot.voice_client_in(server)
    player = await voice_client.create_ytdl_player(url, after=lambda: check_queue(server.id))
    players[server.id] = player
    player.start()

@bot.command(pass_context=True)
async def pause(ctx):
    id = ctx.message.server.id
    players[id].pause()

@bot.command(pass_context=True)
async def stop(ctx):
    id = ctx.message.server.id
    players[id].stop()

@bot.command(pass_context=True)
async def resume(ctx):
    id = ctx.message.server.id
    players[id].resume()

#@bot.command(pass_context=True)
#async def queue(ctx, url):
#    server = ctx.message.server
#    voice_client = bot.voice_client_in(server)
#    player = await voice_client.create_ytdl_player(url, after=lambda: check_queue(server.id))
#
#    if server.id in queues:
#        queues[server.id].append(player)
#    else:
#        queues[server.id] = [player]
#    await bot.say("Video queued.")

@bot.command(pass_context=True)
async def info(ctx, user: discord.Member):
    embed = discord.Embed(title="{}'s info".format(user.name), description="Here's what I could find:", color=0xff0000)
    embed.add_field(name="Name", value=user.name, inline=True)
    embed.add_field(name="ID", value=user.id, inline=True)
    embed.add_field(name="Status", value=user.status, inline=True)
    embed.add_field(name="Highest Role", value=user.top_role)
    embed.add_field(name="Joined", value=user.joined_at)
    embed.set_thumbnail(url=user.avatar_url)
    await  bot.say(embed = embed)

@bot.command(pass_context=True)
async def serverinfo(ctx):
    embed = discord.Embed(title="{}'s info".format(ctx.message.server.name), description="Here's what I could find:",
                          color=0xff0000)
    embed.add_field(name="Name", value=ctx.message.server.name, inline=True)
    embed.add_field(name="ID", value=ctx.message.server.id, inline=True)
    embed.add_field(name="Roles", value=len(ctx.message.server.roles), inline=True)
    embed.add_field(name="Members", value=len(ctx.message.server.members))
    embed.set_thumbnail(url=ctx.message.server.icon_url)
    await  bot.say(embed=embed)

@bot.command()
async def say(*args):
    output = ''
    for word in args:
        output += word
        output += " "
    await bot.say(output)

@bot.command()
async def zomb():
    yayornay = [
        "epic",
        "not epic",
        "a little epic",
        "not really epic",
        "very epic",
        "not even close to epic"
    ]
    await bot.say(random.choice(yayornay))

@bot.command()
async def ayame():
    nword = [
        "nigger",
        ";;w;",
        "ggggggggg",
        "m ok"
    ]
    await bot.say(random.choice(nword))

@bot.command()
async def hentai():
    await bot.say(random.choice(hentai_haven))

@bot.command()
async def pomf():
    variable = [
        "ok.",
        "wow dont care",
        "mhm yea ok uh huh yup",
        "you mad bro? *le trol face*",
        "yep, i'm a pedophile. problem?",
        "watch Monogatari",
        "guys go like my memes",
        "guys hel pme",
        "haha lol xd lmao",
        "Ritsu (being the tomboy she is) is all for it. Mio refuses and is very careful to show her panties (we all"
        " know why), Yui (the adorable carefree girl she is) gladly goes alon with it. Azusa reluctantly follows along"
        " with some modesty, and Mugi almost seems to want it.",
        "not cool dude.",
        "are you RETARDED?",
        "dude, LOL!",
        "omgg kawaii desu~~~ :33",
        "Shut the fuck up",
        "that's pretty crin\n*crinbe\n*cringw, duud...",
        "noochan\nsnoooop\nnchan\nsoop"]
    await bot.say(random.choice(variable))

@bot.event
async def on_message(message):
    if "tomato" in message.content or "Tomato" in message.content or "TOMATO"in message.content:
        embed = discord.Embed(title="TOMATO!!!", color=0xff0000)
        embed.set_image(url="https://i.kym-cdn.com/photos/images/original/000/818/968/0c1.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "baka" in message.content or "Baka" in message.content or "BAKA" in message.content:
        embed = discord.Embed(color=0xff0000)
        embed.set_image(url="https://i.ytimg.com/vi/715NU3ehq5E/maxresdefault.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
#    elif "ayame" in message.content or "Ayame" in message.content:
#        embed = discord.Embed(color=0xff69b4)
#        embed.set_author(name="you already have a fucking command")
#        await bot.process_commands(message)
#        await bot.send_message(destination=message.channel, embed=embed)
    elif "woah" in message.content or "Woah" in message.content or "WOAH" in message.content or \
     "woag" in message.content or "Woag" in message.content or "woa" in message.content:
        embed = discord.Embed(color=0xff0000)
        embed.set_image(url="https://i.gifer.com/8toI.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "<3" in message.content or "ily" in message.content or "i love you" in message.content or \
     "I love you" in message.content or "Ily" in message.content or ":heart:" in message.content:
        embed = discord.Embed(color=0xff0000)
        embed.set_image(url="https://media.giphy.com/media/G7vN34HuAtkT6/giphy.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "Dance" in message.content or "dance" in message.content or "DANCE" in message.content or \
     "guitar" in message.content:
        embed = discord.Embed(color=0xff0000)
        embed.set_image(url="https://i.neoseeker.com/mgv/59301/301/112/yy_dance_display.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif ">///<" in message.content:
        embed = discord.Embed(color=0xff0000)
        embed.set_image(url="http://pbs.twimg.com/media/ClADgn3UUAAEVuk.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "nom" in message.content or "Nom" in message.content or "NOM" in message.content or \
     "eat" in message.content or "EAT" in message.content or "Eat" in message.content:
        embed = discord.Embed(color=0xff0000)
        embed.set_image(url="https://68.media.tumblr.com/879bf34f5498099e064c33dfaadf300a/tumblr_n5p3nvz4Om1shlg3vo1"
            "_500.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "Christmas" in message.content or "christmas" in message.content or "CHRISTMAS" in message.content or \
            "xmas" in message.content or "Xmas" in message.content or "XMAS" in message.content or "x-mas" in \
        message.content or "X-mas " in message.content or "X-MAS " in message.content:
        embed = discord.Embed(title="'Christmas?'", color=0xff0000)
        embed.set_image(url="http://i.imgur.com/3bgMs2i.png")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "sleep" in message.content or "Sleep" in message.content or "gn" in message.content or "Gn" \
            in message.content or "goodnight" in message.content or "Goodnight" in message.content:
        embed = discord.Embed(title="Goodnight!", color=0xff0000)
        embed.set_image(url="https://i.pinimg.com/736x/4e/d4/81/4ed48195f9674d2855a97eb9cca9259e--yuru-yuri-blog.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "good morning" in message.content or "Good Morning" in message.content or "Good morning" in message.content\
            or "Gm" in message.content or "gm" in message.content:
        embed = discord.Embed(title="Good Morning!", color=0xff0000)
        embed.set_image(url="https://78.media.tumblr.com/40e1f6e1395bef949c19a38589254002/tumblr_o7cwyacnTt1udcoqno1"
            "_500.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "shut up" in message.content or"Shut up" in message.content or "SHUT UP" in message.content:
        embed = discord.Embed(title="Okay.", color=0xff0000)
        embed.set_image(url="https://thumbs.gfycat.com/ScarceMindlessEmu-size_restricted.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif ":thinking:" in message.content or "hm" in message.content or "Hm" in message.content:
        embed = discord.Embed(title="Hmm", color=0xff0000)
        embed.set_image(url="https://pm1.narvii.com/6833/e1f1ffff0b45e1b579331445762e2ebc8f211088v2_hq.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
#    elif 'say "I can' in message.content:
#        embed = discord.Embed(title="ok :333", color=0xff0000)
#        embed.set_image(url="https://i.pinimg.com/236x/bc/ac/7b/bcac7b18f43490b6b6f269aa3748bdb1--yuru-yuri-kawaii-anime.jpg")
#        await bot.process_commands(message)
#        await bot.send_message(destination=message.channel, embed=embed)
#    elif "im ugly" in message.content or "i'm ugly" in message.content or "Im ugly" in message.content or "I'm ugly" \
#        in message.content:
#        embed = discord.Embed(title="WRONG", color=0xff0000)
#        embed.set_image(url="http://theakiba.com/images/2011/08/1024_cosplay-200x200.jpg")
#        await bot.process_commands(message)
#        await bot.send_message(destination=message.channel, embed=embed)
    elif "Halloween" in message.content or "halloween" in message.content:
        embed = discord.Embed(title="'Halloween?'", color=0xff0000)
        embed.set_image(url="https://i.kym-cdn.com/photos/images/original/000/859/134/07b.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "vore" in message.content or "Vore" in message.content or "VORE" in message.content:
        embed = discord.Embed(title="VORE", color=0xff0000)
        embed.set_image(url="https://i.redd.it/c9nvwpctibby.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "new year" in message.content or "New year" in message.content or "New Year" in message.content:
        embed = discord.Embed(title="Happy New Year!", color=0xff0000)
        embed.set_image(url="https://i.imgur.com/iW7UHbc.gif")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    elif "April fools" in message.content or "April Fools" in message.content or "april fools" in message.content \
            or "APRIL FOOLS" in message.content:
        embed = discord.Embed(title="April Fools!", color=0xff0000)
        embed.set_image(url="https://i.stack.imgur.com/Y1mNM.jpg")
        await bot.process_commands(message)
        await bot.send_message(destination=message.channel, embed=embed)
    else:
        await bot.process_commands(message)

bot.loop.create_task(change_status())
bot.run("NTAyNjY5OTA3ODM4NzYzMDIz.DqrZZQ.rKsy4Rafqgpr449ztP3kogIeDxc")
