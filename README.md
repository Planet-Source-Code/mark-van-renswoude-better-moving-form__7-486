<div align="center">

## Better moving form


</div>

### Description

While looking at somebody else's code, I noticed he was doing all sorts of stuff with the MouseDown and MouseMove events. Here's a better way, it captures the WM_NCHITTEST message which Windows sends to make Windows think the user is clicking on the titlebar, thus moving the form...
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mark van Renswoude](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mark-van-renswoude.md)
**Level**          |Beginner
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |Delphi 5, Delphi 4, Pre Delphi 4
**Category**       |[Custom Controls/ Forms/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/custom-controls-forms-menus__7-4.md)
**World**          |[Delphi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/delphi.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mark-van-renswoude-better-moving-form__7-486/archive/master.zip)





### Source Code

<font face="courier new" size="-1">
<b>unit</b> Unit1;<br /><br />
<b>interface</b><br /><br />
<b>uses</b><br />
&nbsp;&nbsp;Windows,<br />
&nbsp;&nbsp;Messages,<br />
&nbsp;&nbsp;Forms;<br /><br />
<b>type</b><br />
&nbsp;&nbsp;TForm1 = <b>class</b>(TForm)<br />
&nbsp;&nbsp;<b>protected</b><br />
&nbsp;&nbsp;&nbsp;&nbsp;<b>procedure</b> WMNCHitTest(<b>var</b> Msg: TWMNCHitTest); <b>message</b> WM_NCHITTEST;<br />
&nbsp;&nbsp;<b>end</b>;<br /><br />
<b>var</b><br />
&nbsp;&nbsp;Form1: TForm1;<br /><br />
<b>implementation</b><br /><br />
<font color="#000080">{$R *.DFM}</font><br /><br />
<b>procedure</b> TForm1.WMNCHitTest(<b>var</b> Msg: TWMNCHitTest);<br />
<b>begin</b><br />
&nbsp;&nbsp;<font color="#000080">// Call default procedure</font><br />
&nbsp;&nbsp;<b>inherited</b>;<br /><br />
&nbsp;&nbsp;<font color="#000080">// Modify result to make windows think we're<br />
&nbsp;&nbsp;// clicking on the titlebar when we're actually<br />
&nbsp;&nbsp;// clicking on the client area...</font><br />
&nbsp;&nbsp;<b>if</b> Msg.Result = HTCLIENT <b>then</b><br />
&nbsp;&nbsp;&nbsp;&nbsp;Msg.Result := HTCAPTION;<br />
<b>end</b>;<br /><br />
<b>end</b>.<br />
</font>

