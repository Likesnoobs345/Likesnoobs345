import discord, sys, requests, os, time
from discord.ext import commands
import asyncio
from packaging import version
from random import randint, choice, randrange, random, choices
from threading import Thread
from inputimeout import inputimeout, TimeoutOccurred
from queue import Queue
from io import BytesIO
from pathlib import Path
from math import ceil
from copy import deepcopy
import json

# style
from colorama import init, Fore


init(autoreset=True)

# 
__TITLE__ = "C-REAL"
__VERSION__ = "2.4.1"
__AUTHOR__ = "TKperson"
__LICENSE__ = "MIT"

# Global vars
per_page = 15
commands_per_page = 5
number_of_bomb_default = 250
selected_server = None
sorted_commands = []
webhook_targets = []
saved_ctx = None
nuke_on_join = False
auto_nick = False
auto_status = False
selfbot_has_perm = False
timeout = 6
fetching_members = False
bad_filename_map = dict((ord(char), None) for char in '<>:"\\/|?*')
grant_all_permissions = False
# normal functions==============
def exit():
    try:
        input('Press enter to exit...')
    except (EOFError, KeyboardInterrupt):
        pass
    sys.exit(1)

def banner():
    """Handler for non-unicode consoles"""
    sys.stdout.buffer.write(f'''\
