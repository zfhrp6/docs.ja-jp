---
title: "How to: Send Strings to Serial Ports in Visual Basic | Microsoft Docs"
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
  - "ports, sending strings to"
  - "strings [Visual Basic], sending to serial ports"
  - "My.Computer.Ports object"
  - "serial ports, sending strings to"
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Send Strings to Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックでは、`My.Computer.Ports` を使用して、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でコンピューターのシリアル ポートに文字列を送信する方法について説明します。  
  
## 使用例  
 この例では、COM1 シリアル ポートに文字列を送信します。  コンピューターによっては、他のシリアル ポートを使用することが必要な場合があります。  
  
 `My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。  詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。  
  
 `Using` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。  シリアル ポートを操作するコードは、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> メソッドはシリアル ポートにデータを送信します。  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#33)]  
  
## コードのコンパイル  
  
-   この例では、コンピューターが `COM1` を使用しているものと想定しています。  
  
## 信頼性の高いプログラミング  
 この例では、コンピューターが `COM1` を使用しているものと想定しています。実際に作成するコードでは、柔軟性を高めるために、利用可能なシリアル ポートの一覧から、目的のポートをユーザーが選択できるようにすることをお勧めします。  詳細については、「[How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」を参照してください。  
  
 この例では、アプリケーションが例外をスローした場合でもポートが閉じられるよう、`Using` ブロックを使用しています。  詳細については、「[Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)