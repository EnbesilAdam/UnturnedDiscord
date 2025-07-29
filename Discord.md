using Rocket.Core.Plugins;
using Rocket.Core.Logging;
using Rocket.API;
using Rocket.Unturned.Player;
using Rocket.Unturned.Chat;
using System.Collections.Generic;
using UnityEngine;
using System;

namespace DiscordPlugin
{
    public class Main : RocketPlugin
    {
        protected override void Load()
        {
            Console.WriteLine("[Discord] Loaded", Console.ForegroundColor = ConsoleColor.Magenta);
        }
    }
    public class DiscordCommand : IRocketCommand
    {
        public AllowedCaller AllowedCaller => AllowedCaller.Player;
        //
        public string Name => "discord";
        //    
        public string Help => "Shows Discord URL";
        //     
        public string Syntax => "/discord";
        //
        public List<string> Aliases => new List<string>();
        //
        public List<string> Permissions => new List<string>();
        //
        public void Execute(IRocketPlayer caller, string[] command)
        {
            if (caller is UnturnedPlayer player)
                UnturnedChat.Say(player, " Our Discord Server: https://discord.gg/Plugin", Color.cyan);
        }
    }
}
