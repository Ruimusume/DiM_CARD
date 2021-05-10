# DiM_CARD
デジモンバイタルブレス／DIGIMON VITAL BRACELET DiM CARD Flash

[DIGIMON VITAL BRACELET]CH341A编程器 Dump&刷写&初始化 DiM Card 数据（含数码兽数据bin）
https://ruisan.blog.jp/archives/9756028.html

<div  align="center">
<img  src="https://livedoor.blogimg.jp/ruimusume/imgs/d/d/dd5f25cc.jpg" width="1000" border="0" alt="DIGIMON VITAL BRACELET" hspace="5" class="pict">
</div>
<blockquote> <b>CH341A编程器接线示意图方案</b><br />
  点击图片可以查看大图<br />
  microDS读卡器是可以用工具从插入卡的地方放撬开的，外壳都是有卡扣扣住的可以在合回去不会松<br />
  由于DiM Card厚度比microDS厚可能需要用胶纸缠稳<br />
  接线方案①可以用买杜邦线进行对接，方案②一般买CH341A都会送板和针，同样也需要杜邦线对接<br />
  使用SOP烧录夹可以免用microDS读卡器，接线麻烦的情况下建议买SOP16能用杜邦线的那种就比较傻瓜化<br />
  <div  align="center"><a  href="https://livedoor.blogimg.jp/ruimusume/imgs/7/0/70d47266.jpg" target="_blank"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/7/0/70d47266.jpg" width="900" alt="CH341A" hspace="5" class="pict"></a></div>
</blockquote>
<blockquote> <b>软件工具</b><br />
<a  target="_blank" href="http://www.wch.cn/downloads/CH341SER_EXE.html">CH341SER.exe驱动</a><br />
  <a  href="https://github.com/Ruimusume/DiM_CARD/releases/tag/2.1.0.13" class="name" target="_blank">AsProgrammer 2.1.0.13 DiM CARD ver.zip</a></blockquote>

<blockquote> <b>驱动安装</b><br />
不用CH341A连接电脑直接安装CH341SER.exe（如果怕装了别的版本的驱动可以先点卸载）<br />
<div  align="center"><img  class="pict" hspace="5" alt="CH341SER" border="0" height="282" width="430" src="https://livedoor.blogimg.jp/ruimusume/imgs/f/8/f8c9d15b.png"></div>
</blockquote>

<blockquote><b>CH341A连接电脑注意事项</b><br />
CH341A如果没有跳线连接电脑的话，可以在设备管理器的端口处确认驱动是否安装好或CH341A是否连接电脑成功<br />
<div  align="center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/a/9/a9282fb7.png" width="239" height="82" border="0" alt="USB-SERIAL CH341A" hspace="5" class="pict"></div>
如果设备出现在端口显示USB-SERIAL CH341A的话证明无法对DiM Card进行编程刷写Dump等，软件会读取不到芯片型号<br />
<br />
可以查看CH341A背面会有标记「1-2 编程」代表旁边的1和2需要跳线触碰才能编程的意思<br />
如果你购买的CH341A没有带跳线帽的话可以用铜线夹紧也有效<br />
<div  align="center"><img  class="pict" hspace="5" alt="CH341A跳线" border="0" height="614" width="800" src="https://livedoor.blogimg.jp/ruimusume/imgs/0/1/01b45042.jpg"></div>
<br />
正常CH341A连接电脑，软件可以读取芯片型号会在设备管理器的外部接口显示USB-EPP I2C... CH341A<br />
<div  align="center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/2/b/2b539a03.png" width="200" height="42" border="0" alt="USB-EPP I2C... CH341A" hspace="5" class="pict"></div>
</blockquote>

<blockquote> <b>读取DiM卡&amp;备份</b><br />
点击检查芯片型号，然后选择DiM_CARD（GPR25L3203F）<br />
<div  align="center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/f/b/fbf92165.png" width="766" height="488" border="0" alt="AsProgrammer" hspace="5" class="pict"></div>
<br />
然后点击读取IC，等待进度条完成出现进制代码，然后就可以点保存bin文件到电脑里了<br />
<div  align="center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/b/6/b620cf98.png" width="766" height="488" border="0" alt="读取" hspace="5" class="pict"></div>
</blockquote>
<blockquote> <b>DiM卡刷写其他bin数据</b><br />
点击检查芯片型号，然后选择DiM_CARD（GPR25L3203F）<br />
然后打开bin文件，再点写入/编程 IC，等待进度条完成即可<br />
  <div  align="center"><img  class="pict" hspace="5" alt="刷写" border="0" height="488" width="766" src="https://livedoor.blogimg.jp/ruimusume/imgs/6/6/666cce1a.png"></div>
<div  align="center"><img  class="pict" hspace="5" alt="黑加布兽" border="0" height="456" width="766" src="https://livedoor.blogimg.jp/ruimusume/imgs/6/0/609d3d3b.jpg"><br />
VS卡刷写黑加布兽接收成功</div>
</blockquote>
<blockquote><b>重置&解绑DiM卡</b><br />
<blockquote> <b>重置DiM卡脚本（自行保存为.pas格式放入scripts文件夹）</b><br />
 {$ Re_Dim_card}<br />
  begin<br />
  LogPrint ('Start Restore DiM card ID.');<br />
  ReadToEditor ( 8, $10000, $FF, $FF, $FF, $FF, $FF, $FF, $FF, $FF);<br />
  LogPrint ('Please click Programm IC to upload the HEX file.');<br />
  end </blockquote>
首先读取IC，菜单栏里选择脚本—区段=，选择你保存的脚本<br />
然后点运行，最后点写入/编程 IC，等待进度条完成即可 </blockquote>

<blockquote><div  align="center">数据购买支付方式<br />
支付后请联系邮箱ruisan618@126.com附上支付截图和所需的文件通过邮件发送获取数据文件<br />
    <img  src="https://livedoor.blogimg.jp/ruimusume/imgs/5/8/585cc192.jpg" hspace="5" class="pict">
  <br />
PALPAY支付方式<br />
支付后请邮箱联系附上截图<br />
<form  action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
<input  type="hidden" name="cmd" value="_s-xclick">
<table>
<tbody><tr><td><input  type="hidden" name="on0" value="选择DIM数据价格">选择DIM数据价格</td></tr><tr><td><select  name="os0">
	<option  value="10元">10元 $ 10.00 USD</option>
	<option  value="30元">30元 $ 30.00 USD</option>
	<option  value="50元">50元 $ 50.00 USD</option>
	<option  value="100元">100元 $ 100.00 USD</option>
</select> </td></tr>
</tbody></table>
<input  type="hidden" name="encrypted" value="-----BEGIN PKCS7-----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-----END PKCS7-----">
<input  type="image" src="https://www.paypalobjects.com/zh_XC/C2/i/btn/btn_buynowCC_LG.gif" border="0" name="submit" alt="PayPal——最安全便捷的在线支付方式！">
<img  border="0" src="https://www.paypalobjects.com/zh_XC/i/scr/pixel.gif" width="1" height="1">
</form>
</div>
  </blockquote>
<blockquote>
      <table  align="center">
<tr>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/d/a/da32a79e.png" width="150" title="VS MEMORY" alt="VS MEMORY"><br />（免费提供）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/c/f/cf539c58.png" width="150" title="IMPULSE CITY" alt="IMPULSE CITY"><br />（10元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/a/4/a4564c9e.png" width="150" title="ANCIENT WARRIORS" alt="ANCIENT WARRIORS"><br />（50元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/9/7/973b32d8.png" width="150" title="BLACK ROAR" alt="BLACK ROAR"><br />（50元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/7/8/785d70fb.png" width="150" title="SHADOW HOWL" alt="SHADOW HOWL"><br />（100元）</td>
      </tr>
      <tr>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/8/f/8f6ac507.png" width="150" alt="AGUMON" title="AGUMON"><br />（30元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/b/0/b0199679.png" width="150" alt="GABOMON" title="GABOMON"><br />（30元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/0/1/01d0609d.png" width="150" alt="VOLCANIC BEAT" title="VOLCANIC BEAT"><br />（30元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/e/1/e1d41189.png" width="150" alt="BLIZZARD FANG" title="BLIZZARD FANG"><br />（30元）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/f/2/f2f41560.png" width="150" alt="INFINITE TIDE" title="INFINITE TIDE"><br />（未出）</td>
      </tr>
      <tr>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/3/1/31b22e08.png" width="150" alt="TITAN OF DUST" title="TITAN OF DUST"><br />（未出）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/3/d/3d6bef73.png" width="150" alt="MAD BALCK ROAR" title="MAD BALCK ROAR"><br />（未出）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/e/a/eac24082.png" width="150" alt="TRUE SHADOW HOWL" title="TRUE SHADOW HOWL"><br />（未出）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/d/1/d16f3201.png" width="150" alt="GUILMON" title="GUILMON"><br />（未出）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/6/0/60ffe97f.png" width="150" alt="IMPMON" title="IMPMON"><br />（未出）</td>
      </tr>
      <tr>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/e/4/e4777d8a.png" width="150" alt="RENAMON" title="RENAMON"><br />（未出）</td>
        <td  style="text-align: center"><img  src="https://livedoor.blogimg.jp/ruimusume/imgs/4/c/4ca49ba6.png" width="150" alt="MONODRAMON" title="MONODRAMON"><br />（未出）</td>        
        <td  style="text-align: center"><img  title="MEDAROT × DIGITALMONSTER" alt="MEDAROT × DIGITALMONSTER" border="0" width="150" src="https://livedoor.blogimg.jp/ruimusume/imgs/8/6/869c8f89.png"><br />（未出）</td>
        <td  style="text-align: center">null</td>
        <td  style="text-align: center">null</td>
      </tr>
    
</table>
</blockquote>
<blockquote>
<b>bin文件数据校验值</b><br />
<div  align="center"><img  class="pict" hspace="5" alt="dim img" border="0" width="950" src="https://livedoor.blogimg.jp/ruimusume/imgs/1/1/112f9473.png"></div>
<br />
文件: VOLCANIC BEAT.bin<br />
大小: 4194304 字节<br />
MD5: 9C84708473BC869B21CF141490E828E4<br />
SHA1: 0A8B097421C797382A1D4E047BC6E2191B7BDBA5<br />
CRC32: A6A763C0<br />
<br />
文件: VS MEMORY.bin<br />
大小: 4194304 字节<br />
MD5: C06B785697542470ADE5EA60507D386A<br />
SHA1: 76BB3839AC3F72F3890BECB40D42BD579FFAF91E<br />
CRC32: 1DBEC49C<br />
<br />
文件: AGUMON.bin<br />
大小: 4194304 字节<br />
MD5: D045A246DC5AEEBDF8857FDA2A767ED7<br />
SHA1: BE25CBA3185E3801ABBFBC90595F590E67384E5E<br />
CRC32: BE86D5FD<br />
<br />
文件: ANCIENT WARRIORS.bin<br />
大小: 4194304 字节<br />
MD5: C6014EEC3DA378C928DEB740E84BD641<br />
SHA1: A6775E064AF67FD74B1E0730191EAF964105AF91<br />
CRC32: 5676CB2E<br />
<br />
文件: BLACK ROAR.bin<br />
大小: 4194304 字节<br />
MD5: EC47C64CF1D6A814840ACBC9A4E9FE6C<br />
SHA1: 5A7FDAF0C21EC6BEC22AF9C638E123D27E162927<br />
CRC32: C73D964E<br />
<br />
文件: BLIZZARD FANG.bin<br />
大小: 4194304 字节<br />
MD5: BF530CBCB26460E18FB6DB247719EF1B<br />
SHA1: 83C06B28F197301DBDB2A34127062A8BBABC629A<br />
CRC32: 711F3854<br />
<br />
文件: GABOMON.bin<br />
大小: 4194304 字节<br />
MD5: 73A18AE4450B2C1F4E4FF3F6369321DB<br />
SHA1: 10BA0B04998F66FA62F2DCF2DA33D83CCBC94352<br />
CRC32: F16342B3<br />
<br />
文件: IMPULSE CITY.bin<br />
大小: 4194304 字节<br />
MD5: 061082CBEDE5C35BDE24554FD287A3A1<br />
SHA1: BD19053D535B234B20753CCFC2E4CCE74EC98E55<br />
CRC32: 74D2B203<br />
<br />
文件: SHADOW HOWL.bin<br />
大小: 4194304 字节<br />
MD5: 6F9DCBA75CE23D7FD42295C3C512F3DC<br />
SHA1: 4FD807485624B42D1708070B43FB46A237E8DABD<br />
CRC32: CA5E552D<br />
</blockquote>
