---
title: "How to: Dial Modems Attached to Serial Ports in Visual Basic | Microsoft Docs"
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
  - "modems, dialing"
  - "serial ports, dialing"
  - "My.Computer.Ports object"
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Dial Modems Attached to Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で `My.Computer.Ports` を使用してモデムをダイヤルする方法について説明します。  
  
 通常、モデムはコンピューターのいずれかのシリアル ポートに接続されています。  アプリケーションがモデムとやり取りするためには、適切なシリアル ポートにコマンドを送信する必要があります。  
  
### モデムをダイヤルするには  
  
1.  モデムが接続されているシリアル ポートを確認します。  この例では、モデムが COM1 に接続されていることを前提としています。  
  
2.  `My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。  詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。  
  
     `Using` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。  シリアル ポートを操作するコードは、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#28)]  
  
3.  `DtrEnable` プロパティを設定し、コンピューターがモデムからの伝送を受け取る準備ができたことを通知します。  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#29)]  
  
4.  <xref:System.IO.Ports.SerialPort.Write%2A> メソッドを使用して、ダイヤル コマンドと電話番号をシリアル ポート経由でモデムに送信します。  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#30)]  
  
## 使用例  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#27)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[接続とネットワーク\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## コードのコンパイル  
 この例では、<xref:System?displayProperty=fullName> 名前空間への参照が必要です。  
  
## 信頼性の高いプログラミング  
 この例では、モデムが COM1 に接続されていることを前提としています。  作成するコードでは、利用可能なシリアル ポートの一覧から、目的のポートをユーザーが選択できるようにすることをお勧めします。  詳細については、「[How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」を参照してください。  
  
 この例では、アプリケーションが例外をスローした場合でもポートが閉じられるよう、`Using` ブロックを使用しています。  詳細については、「[Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
 この例では、アプリケーションは、モデムをダイヤルした後でシリアル ポートを切断しています。  実際には、モデムとの間でデータの転送が必要となります。  詳細については、「[How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)