---
title: "How to: Receive Strings From Serial Ports in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "serial ports, retrieving strings"
  - "strings [Visual Basic], retrieving from serial ports"
  - "My.Resources object"
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Receive Strings From Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックでは、`My.Computer.Ports` を使用して、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でコンピューターのシリアル ポートから文字列を受信する方法について説明します。  
  
### シリアル ポートから文字列を受信するには  
  
1.  返す文字列を初期化します。  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#38)]  
  
2.  どのシリアル ポートから文字列を取得するかを決定します。  この例では、`COM1` であるものと想定しています。  
  
3.  `My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。  詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。  
  
     `Try...Catch...Finally` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。  シリアル ポートを操作するコードは、このブロックに記述する必要があります。  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#39)]  
  
4.  `Do` ループを作成します。行がなくなるまでテキストの読み取りを繰り返すためのループです。  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#40)]  
  
5.  <xref:System.IO.Ports.SerialPort.ReadLine%2A> メソッドを使用して、シリアル ポートから次の行のテキストを読み取ります。  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#41)]  
  
6.  `If` ステートメントを使用して、<xref:System.IO.Ports.SerialPort.ReadLine%2A> メソッドが `Nothing` を返したかどうか \(つまり、テキストがもうないかどうか\) を判断します。  `Nothing` を返した場合は、`Do` ループを終了します。  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#42)]  
  
7.  文字列をきちんと読み取ることができた場合の処理を実行するための `Else` ブロックを `If` ステートメントに追加します。  ブロックでは、シリアル ポートから取得した文字列を、返す文字列の末尾に追加します。  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#43)]  
  
8.  文字列を返します。  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#44)]  
  
## 使用例  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#37)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[接続とネットワーク\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## コードのコンパイル  
 この例では、コンピューターが `COM1` を使用しているものと想定しています。  
  
## 信頼性の高いプログラミング  
 この例では、コンピューターが `COM1` を使用しているものと想定しています。  実際に作成するコードでは、柔軟性を高めるために、利用可能なシリアル ポートの一覧から、目的のポートをユーザーが選択できるようにすることをお勧めします。  詳細については、「[How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」を参照してください。  
  
 この例では、アプリケーションが確実にポートを閉じるようにするため、およびタイムアウト例外をすべてキャッチできるようにするために、`Try...Catch...Finally` ブロックを使用しています。  詳細については、「[Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)