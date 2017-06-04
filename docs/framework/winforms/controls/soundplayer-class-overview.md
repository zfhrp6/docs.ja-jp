---
title: "SoundPlayer クラスの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "SoundPlayer クラスのサウンドを再生"
  - "SoundPlayer クラスの概要の SoundPlayer クラス"
  - "サウンドの再生"
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# SoundPlayer クラスの概要
<xref:System.Media.SoundPlayer>クラスでは、アプリケーションにサウンドを簡単に追加することができます。  
  
 <xref:System.Media.SoundPlayer>クラスは、.wav 形式、リソースとは UNC または HTTP の場所からのサウンド ファイルを再生できます。 さらに、 <xref:System.Media.SoundPlayer>クラスを使用すると、読み込みまたは非同期的にサウンドを再生します。  
  
 使用することも、 <xref:System.Media.SystemSounds>ビープ音を含む、共通のシステム サウンドを再生するクラス。  
  
## <a name="commonly-used-properties-methods-and-events"></a>一般的に使用されるプロパティ、メソッド、およびイベント  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A>プロパティ|ファイル パスまたはサウンドの Web アドレス。 使用可能な値には、UNC または HTTP を指定できます。|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A>プロパティ|プログラムが前に、サウンドの読み込みを待機するミリ秒数では、例外をスローします。 既定値は 10 秒です。|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A>プロパティ|サウンドの読み込みが終了するかどうかを示すブール値。|  
|<xref:System.Media.SoundPlayer.Load%2A>メソッド|サウンドを同期的に読み込まれます。|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A>メソッド|サウンドを非同期的に読み込みを開始します。 読み込みが完了したらを生成、 <xref:System.Media.SoundPlayer.OnLoadCompleted%2A>イベントです。|  
|<xref:System.Media.SoundPlayer.Play%2A>メソッド|指定したサウンドを再生して、 <xref:System.Media.SoundPlayer.SoundLocation%2A>または<xref:System.Media.SoundPlayer.Stream%2A>新しいスレッドのプロパティです。|  
|<xref:System.Media.SoundPlayer.PlaySync%2A>メソッド|指定したサウンドを再生して、 <xref:System.Media.SoundPlayer.SoundLocation%2A>または<xref:System.Media.SoundPlayer.Stream%2A>現在のスレッドのプロパティです。|  
|<xref:System.Media.SoundPlayer.Stop%2A>メソッド|再生されているすべてのサウンドを停止します。|  
|<xref:System.Media.SoundPlayer.LoadCompleted>イベント|サウンドの読み込みを試みた後に発生します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer>   
 <xref:System.Media.SystemSounds>