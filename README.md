# 概要
alfred4でTerminalを開いてコマンドを叩く時に常に新規ウィンドウが開いてしまうのが微妙だったので参考サイトを参考にすでに表示されているターミナルがあるんであれば、それ以上ターミナルを新規に開かないようにする設定を行いました。

# 設定方法
AlfredのFeatures > TerminalのApplicationでCustomを選択し、下記のscriptを登録する

```
on alfred_script(q)
    tell application "Terminal"
        activate
        set wCount to count (every window whose visible is true)

        if wCount = 0 then
          do script q
        else
          do script q in front window
        end if
    end tell
end alfred_script

```

## 参考
http://piyocast.com/as/archives/3984
