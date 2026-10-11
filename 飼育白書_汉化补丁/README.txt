飼育白書～鎖に繋がれた同級生～  DL版  deepseek汉化补丁
=====================================================

原理（借鉴同厂游戏《麗佳牝犬調教》开源汉化工程 misc_game-chs）：
  · 游戏文本存放在脚本文件 SIKN.SD 中，为 Delta 引擎格式（Shift-JIS 明文 + \x00 分隔 + 固定偏移）。
  · 本补丁“不改 exe”，做法：
      1) 抽取 SIKN.SD 中所有日文文本段并定位其绝对偏移；
      2) 用机器翻译（MyMemory / Google）把日文翻成中文；
      3) 把中文以“等长”方式写回 SIKN.SD（中文比原文长则删标点/截断，短则补空格），
         不能塞进 Shift-JIS 码位的汉字，先用“替身字”代替；
      4) 运行时由 winmm.dll（Universal Injector Framework）注入中文字体 FZNewKai-Z03，
         并把“替身字”换回真正的汉字，从而正常显示中文。

使用方法：
  1) 关闭游戏。
  2) 把本目录下的 4 个文件（SIKN.SD / winmm.dll / FZNewKai-Z03.ttf / uif_config.json）
     全部复制到游戏安装目录，覆盖原 SIKN.SD（建议先备份原 SIKN.SD）。
  3) 本补丁的 winmm.dll 已内置 locale_emulator，会自动以日文 codepage(932) 运行游戏，通常无需额外转区；
     若你的系统/启动方式导致仍乱码，可配合 Locale Emulator 或游戏自带转区工具以日文区域启动。
  4) 游戏内设置中，建议把“抗锯齿”“文字阴影”设为 OFF，阅读体验更好。
     想换字体：编辑 uif_config.json 的 font_manager.spoof_creation.override_face。

汉化补丁作者  世界公交车-中国牛排（github@WorldBus-ChineseBeef）
