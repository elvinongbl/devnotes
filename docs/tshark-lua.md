Table of Contents

- [Introduction](#introduction)

# Introduction

Writing Wireshark dissectors in Lua is good for fast prototyping. However,
if users would like high performance dissectors, the logics implemented in
Lua should be ported into C language.

The global configuration of Wireshark Lua engine is located at /etc/wireshark/init.lua.
There are two variables worth mentioning here:-
 - disable_lua = false (use to disable Lua engine if true)
 - run_user_scripts_when_superuser = false (use to control if user scripts can be
   executed by superuser)

Next, ~/.config/wireshark/init.lua script is executed before eventually running
the script passed with -X lua_script:xyz.lua. This can be seen from following
example:-

<img src="images/wireshark/tshark-lua-initlua.png" width="760" height="225" />
