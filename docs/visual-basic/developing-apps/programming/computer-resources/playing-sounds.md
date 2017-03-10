---
title: "Playing Sounds (Visual Basic) | Microsoft Docs"
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
  - "system sounds, playing"
  - "system sounds"
  - "playing sounds, Visual Basic"
  - "sound loops"
  - "My.Computer.Audio object, tasks"
  - "sounds, playing"
  - "sounds, background"
  - "playing sounds"
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Playing Sounds (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.Audio` オブジェクトには、サウンドを再生するためのメソッドが用意されています。  
  
## サウンドを再生できます。  
 バックグラウンド再生を利用すると、サウンドの再生中にアプリケーションで他のコードを実行できます。  `My.Computer.Audio.Play` メソッドでは、一度に 1 つのバックグラウンド サウンドのみを再生できます。新しいバックグラウンド サウンドを再生するときには、前のバックグラウンド サウンドの再生は停止されます。  また、サウンドを再生し、その完了を待機することもできます。  
  
 次の例では、 `My.Computer.Audio.Play` のメソッドは、サウンドを再生します。  `AudioPlayMode.WaitToComplete` を指定した場合、`My.Computer.Audio.Play` はサウンドの再生が完了するまで待機した後、呼び出し元のコードに戻ります。  この例を使用する場合は、ファイル名がコンピューターにある .wav サウンド ファイルを参照するようにする必要があります。  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class1.vb#15)]  
  
 次の例では、 `My.Computer.Audio.Play` のメソッドは、サウンドを再生します。  この例を使用する場合、アプリケーション リソースが Waterfall という名前の .wav サウンド ファイルが含まれていることを確認する必要があります。  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class1.vb#16)]  
  
## ループ サウンドを再生できます。  
 次の例では、 `My.Computer.Audio.Play` のメソッドは `PlayMode.BackgroundLoop` を指定すると、指定のサウンドをバックグラウンドで説明します。  この例を使用する場合は、ファイル名がコンピューターにある .wav サウンド ファイルを参照するようにする必要があります。  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class1.vb#11)]  
  
 次の例では、 `My.Computer.Audio.Play` のメソッドは `PlayMode.BackgroundLoop` を指定すると、指定のサウンドをバックグラウンドで説明します。  この例を使用する場合、アプリケーション リソースが Waterfall という名前の .wav サウンド ファイルが含まれていることを確認する必要があります。  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class1.vb#12)]  
  
 前のコード例では、 IntelliSense コード スニペットとしても使用できます。  コード スニペット ピッカーでは、これは **\[Windows Forms Applications\] の \[Sound\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
 一般に、アプリケーションがループ サウンドを再生している場合には、どこかの時点でサウンドを停止する必要があります。  
  
## バックグラウンド サウンドの再生を停止  
 `My.Computer.Audio.Stop` メソッドを使用して、アプリケーションが現在再生しているバックグラウンド サウンドまたはループ サウンドを停止します。  
  
 一般に、アプリケーションがループ サウンドを再生している場合には、どこかの時点でサウンドを停止する必要があります。  
  
 次の例では、バックグラウンドで再生しているサウンドを停止します。  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class1.vb#18)]  
  
 前のコード例では、 IntelliSense コード スニペットとしても使用できます。  コード スニペット ピッカーでは、これは **\[Windows Forms Applications\] の \[Sound\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## システム サウンドをできます。  
 `My.Computer.Audio.PlaySystemSound` メソッドを使用して、指定したシステム サウンドを再生します。  
  
 `My.Computer.Audio.PlaySystemSound` メソッドは、<xref:System.Media.SystemSound> クラスのいずれかの共有メンバーをパラメーターとして受け取ります。  システム サウンド <xref:System.Media.SystemSounds.Asterisk%2A> は、一般にエラーを表します。  
  
 次の例では、システム サウンドの再生に `My.Computer.Audio.PlaySystemSound` のメソッドを使用します。  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class1.vb#17)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>