---
title: "How to: Show Available Serial Ports in Visual Basic | Microsoft Docs"
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
  - "serial ports, availability"
  - "My.Computer.Ports.SerialPortNames property"
  - "My.Computer.Ports object"
  - "ports, serial port availability"
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Show Available Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、`My.Computer.Ports` を使用して、コンピューターで利用可能なシリアル ポートを [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で表示する方法について説明します。  
  
 使用するポートをユーザーが選択できるようにするために、シリアル ポートの名前を <xref:System.Windows.Forms.ListBox> コントロールに格納します。  
  
## 使用例  
 この例では、`My.Computer.Ports.SerialPortNames` プロパティが返すすべての文字列に対してループします。  これらの文字列は、コンピューターで利用可能なシリアル ポートの名前です。  
  
 通常は、利用可能なシリアル ポートの一覧から、アプリケーションで使用するシリアル ポートをユーザーが選択します。  この例では、シリアル ポートの名前を <xref:System.Windows.Forms.ListBox> コントロールに格納しています。  詳細については、「[ListBox コントロール](../Topic/ListBox%20Control%20\(Windows%20Forms\).md)」を参照してください。  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[接続とネットワーク\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Windows.Forms.dll に対するプロジェクト参照が必要です。  
  
-   <xref:System.Windows.Forms> 名前空間のメンバーに対するアクセス。  コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。  詳細については、「[Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
-   フォーム上に `ListBox1` という名前の <xref:System.Windows.Forms.ListBox> コントロールが必要です。  
  
## 信頼性の高いプログラミング  
 利用可能なシリアル ポートの名前は、必ずしも <xref:System.Windows.Forms.ListBox> コントロールに表示しなくてもかまいません。  <xref:System.Windows.Forms.ComboBox> コントロールやその他のコントロールを使用することもできます。  ユーザーからの応答が必要ないアプリケーションの場合は、<xref:System.Windows.Forms.TextBox> コントロールを使用して情報を表示できます。  
  
> [!NOTE]
>  `My.Computer.Ports.SerialPortNames` が返すポート名は、Windows 98 での実行時には正しくない場合があります。  アプリケーション エラーを防ぐには、ポート名を使用してポートを開くときに、`Try...Catch...Finally` ステートメントや `Using` ステートメントなどの例外処理を使用します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)