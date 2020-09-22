<div align="center">

## Beginners Intro To IRC Connections


</div>

### Description

Shows Begineers how to sucessfully program applications to connect to IRC servers.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Benjamin Owen](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/benjamin-owen.md)
**Level**          |Beginner
**User Rating**    |3.0 (12 globes from 4 users)
**Compatibility**  |VB 5\.0, VB 6\.0
**Category**       |[Internet/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-html__1-34.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/benjamin-owen-beginners-intro-to-irc-connections__1-42700/archive/master.zip)





### Source Code

```
' This code shows the basic way too make
' a basic connection to an irc server and
' keep it alive
'Requires: 1 textbox with multiline enabled
'     1 Winsock Control
Private Sub Form_Load()
' Connect the winsock to the irc server
  Winsock1.Close
  Winsock1.Connect "irc.qeast.net", 6667
  '(6667 is the default irc port)
End Sub
Private Sub Winsock1_Connect()
'When a user connects to an irc server, such programs
'like mirc, automaticly send over your Nick and User
'So when the winsock is connected we will do the same
With Winsock1
.SendData "NICK psc-user" & vbCrLf
.SendData "USER pscode pscode pscode pscode" & vbCrLf
End With
End Sub
Private Sub Winsock1_DataArrival(ByVal bytesTotal As Long)
'First we declare a variable for the data to go in
Dim data As String
Dim reply As String
'Now get the data and put it in the variable Data
Winsock1.GetData data
'Put the data in text1
Text1.Text = Text1.Text & data
'if the data is a ping from the server we must reply
'with a PONG then the rest of the ping
'eg. PING :12345 would be replied with PONG :12345
If Left(UCase(data), 4) = "PING" Then
'extract what we have to pong back and send it
reply = Right(data, Len(data) - 6)
Winsock1.SendData "PONG :" & reply
End If
End Sub
'End of code
```

