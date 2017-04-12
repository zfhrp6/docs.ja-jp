---
title: "サウンドの再生 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ed4ee0a09067900a6bead04abec02f141936ba42
ms.lasthandoff: 03/13/2017

---
# <a name="playing-sounds-visual-basic"></a>サウンドの再生 (Visual Basic)
`My.Computer.Audio` オブジェクトには、サウンドを再生するためのメソッドが用意されています。  
  
## <a name="playing-sounds"></a>サウンドの再生  
 バックグラウンド再生により、アプリケーションでサウンドを再生しながら他のコードを実行できます。 `My.Computer.Audio.Play` メソッドを使用すると、アプリケーションでバックグラウンド サウンドを一度に 1 つだけ再生できます。アプリケーションで新しいバックグラウンド サウンドが再生されると、その前のバックグラウンド サウンドの再生は停止します。 また、サウンドを再生してから、その再生が完了するまで待機することもできます。  
  
 次の例では、`My.Computer.Audio.Play` メソッドによってサウンドが再生されます。 `AudioPlayMode.WaitToComplete` が指定されている場合、`My.Computer.Audio.Play` はサウンドの再生が完了するまで待機し、その後呼び出し元のコードが処理を再開します。 この例を使用する場合は、必ず自分のコンピューター上の .wav サウンド ファイルを示すファイル名を指定してください。  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 次の例では、`My.Computer.Audio.Play` メソッドによってサウンドが再生されます。 この例を使用する場合は、アプリケーション リソースに Waterfall という名前の .wav サウンド ファイルが含まれていることを確認してください。  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>ループ サウンドの再生  
 次の例では、`PlayMode.BackgroundLoop` が指定されている場合に、指定されているサウンドが `My.Computer.Audio.Play` メソッドによってバックグラウンドで再生されます。 この例を使用する場合は、必ず自分のコンピューター上の .wav サウンド ファイルを示すファイル名を指定してください。  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 次の例では、`PlayMode.BackgroundLoop` が指定されている場合に、指定されているサウンドが `My.Computer.Audio.Play` メソッドによってバックグラウンドで再生されます。 この例を使用する場合は、アプリケーション リソースに Waterfall という名前の .wav サウンド ファイルが含まれていることを確認してください。  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 上記のコード例は、IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでこのスニペットにアクセスするには、**[Windows フォーム アプリケーション]、[サウンド]** の順に移動します。 詳細については、「[Code Snippets](https://docs.microsoft.com/visualstudio/ide/code-snippets)」を参照してください。  
  
 一般に、アプリケーションでループ サウンドを再生する場合は、最終的にそのサウンドを停止する必要があります。  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>バックグラウンドで再生しているサウンドの停止  
 `My.Computer.Audio.Stop` メソッドを使用し、アプリケーションで現在再生中のバックグラウンド サウンドまたはループ サウンドを停止します。  
  
 一般に、アプリケーションでループ サウンドを再生する場合は、どこかの時点でそのサウンドを停止する必要があります。  
  
 次の例では、バックグラウンドで再生中のサウンドを停止します。  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 上記のコード例は、IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでこのスニペットにアクセスするには、**[Windows フォーム アプリケーション]、[サウンド]** の順に移動します。 詳細については、「[Code Snippets](https://docs.microsoft.com/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="playing-system-sounds"></a>システム サウンドの再生  
 `My.Computer.Audio.PlaySystemSound` メソッドを使用して、指定したシステム サウンドを再生します。  
  
 `My.Computer.Audio.PlaySystemSound` メソッドでは、パラメーターとして <xref:System.Media.SystemSound> クラスのいずれかの共有メンバーを受け取ります。 システム サウンドの <xref:System.Media.SystemSounds.Asterisk%2A> は、通常はエラーを表します。  
  
 次の例では、`My.Computer.Audio.PlaySystemSound` メソッドを使用してシステム サウンドを再生しています。  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>
