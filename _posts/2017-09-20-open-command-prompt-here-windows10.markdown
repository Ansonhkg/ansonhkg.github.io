---
layout: post
title:  Open Command Prompt Here Windows 10
date:   2017-09-20 21:04:00 +0100
categories: Workflow
author: Anson Cheung
---

<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- Pages -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-3447513048440895"
     data-ad-slot="9229199209"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

# Quick Breif
- For decades, we were able to right click on a folder (or the background of a folder) to get the "Open Command Prompt" here option. However, you can no longer do that after the Windows 10 Creators Update. 

# Add CMD to Context Menu
1. Create a file with `.reg` extension and paste the following code:
{% highlight linenos %}
Windows Registry Editor Version 5.00

; Command Prompt

[HKEY_CLASSES_ROOT\Directory\shell\01MenuCmd]
"MUIVerb"="Command Prompts"
"Icon"="cmd.exe"
"ExtendedSubCommandsKey"="Directory\\ContextMenus\\MenuCmd"

[HKEY_CLASSES_ROOT\Directory\background\shell\01MenuCmd]
"MUIVerb"="Command Prompts"
"Icon"="cmd.exe"
"ExtendedSubCommandsKey"="Directory\\ContextMenus\\MenuCmd"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuCmd\shell\open]
"MUIVerb"="Command Prompt"
"Icon"="cmd.exe"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuCmd\shell\open\command]
@="cmd.exe /s /k pushd \"%V\""

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuCmd\shell\runas]
"MUIVerb"="Command Prompt Elevated"
"Icon"="cmd.exe"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuCmd\shell\runas\command]
@="cmd.exe /s /k pushd \"%V\""
{% endhighlight %}

# Add PowerShell to Context Menu
{% highlight linenos %}
Windows Registry Editor Version 5.00
; PowerShell

[HKEY_CLASSES_ROOT\Directory\shell\02MenuPowerShell]
"MUIVerb"="PowerShell Prompts"
"Icon"="powershell.exe"
"ExtendedSubCommandsKey"="Directory\\ContextMenus\\MenuPowerShell"

[HKEY_CLASSES_ROOT\Directory\background\shell\02MenuPowerShell]
"MUIVerb"="PowerShell Prompts"
"Icon"="powershell.exe"
"ExtendedSubCommandsKey"="Directory\\ContextMenus\\MenuPowerShell"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuPowerShell\shell\open]
"MUIVerb"="PowerShell"
"Icon"="powershell.exe"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuPowerShell\shell\open\command]
@="powershell.exe -noexit -command Set-Location '%V'"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuPowerShell\shell\runas]
"MUIVerb"="PowerShell Elevated"
"Icon"="powershell.exe"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuPowerShell\shell\runas\command]
@="powershell.exe -noexit -command Set-Location '%V'"


; Ensure OS Entries are on the Extended Menu (Shift-Right Click)

[HKEY_CLASSES_ROOT\Directory\shell\cmd]
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\background\shell\cmd]
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\shell\Powershell]
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\background\shell\Powershell]
"Extended"=""
{% endhighlight %}

# Enable GIT
{% highlight linenos %}
Windows Registry Editor Version 5.00

; Add GIT to Context Menu

[HKEY_CLASSES_ROOT\Directory\shell\03MenuGit]
"MUIVerb"="GIT Prompts"
"Icon"="C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico"
"ExtendedSubCommandsKey"="Directory\\ContextMenus\\MenuGit"

[HKEY_CLASSES_ROOT\Directory\background\shell\03MenuGit]
"MUIVerb"="GIT Prompts"
"Icon"="C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico"
"ExtendedSubCommandsKey"="Directory\\ContextMenus\\MenuGit"


[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuGit\shell\git_gui]
"MUIVerb"="GIT GUI"
"Icon"="C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuGit\shell\git_gui\command]
@="\"C:\\Program Files\\Git\\cmd\\git-gui.exe\" \"--working-dir\" \"%v.\""


[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuGit\shell\git_shell]
"MUIVerb"="GIT BASH"
"Icon"="C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico"

[HKEY_CLASSES_ROOT\Directory\ContextMenus\MenuGit\shell\git_shell\command]
@="\"C:\\Program Files\\Git\\git-bash.exe\" \"--cd=%v.\""


; Move Official GIT Entries to the Extended Menu (Shift-Right Click)

[HKEY_CLASSES_ROOT\Directory\shell\git_gui]
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\background\shell\git_gui]
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\shell\git_shell]
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\background\shell\git_shell]
"Extended"=""
{% endhighlight %}

> Reference: [Windows Explorer Command Prompt Here](https://stackoverflow.com/questions/378319/windows-explorer-command-prompt-here/379804) 

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'open-command-prompt-here-windows10.html'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://ansonc.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>