---
title: "フォアグラウンド スレッドとバックグラウンド スレッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a>フォアグラウンド スレッドとバックグラウンド スレッド
マネージ スレッドは、バック グラウンド スレッドまたはフォア グラウンド スレッドのいずれかです。 バック グラウンド スレッドは同じですがフォア グラウンド スレッドを 1 つの例外: バック グラウンド スレッドが実行されているマネージ実行環境を維持しません。 すべてのフォア グラウンド スレッドをマネージ プロセス (.exe ファイルは、マネージ アセンブリ) に停止すると、システムはすべてのバック グラウンド スレッドを停止し、シャット ダウンします。  
  
> [!NOTE]
>  ランタイムでは、プロセスをシャット ダウンしているため、バック グラウンド スレッドが停止したら、スレッドで例外はスローされません。 ただし、場合のスレッドは停止ため、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>メソッドは、アプリケーション ドメインをアンロード、<xref:System.Threading.ThreadAbortException>がフォア グラウンドとバック グラウンド スレッドでスローされます。  
  
 使用して、<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>スレッドがバック グラウンドまたはフォア グラウンド スレッドがかどうかを判断する、またはその状態を変更するプロパティです。 スレッドはバック グラウンド スレッドにいつでも設定してその<xref:System.Threading.Thread.IsBackground%2A>プロパティを`true`です。  
  
> [!IMPORTANT]
>  スレッドの前景色または背景の状態は、スレッドで未処理の例外の結果には影響しません。 .NET framework version 2.0 では、フォア グラウンドまたはバック グラウンド スレッドで未処理の例外は、アプリケーションの終了になります。 参照してください[マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)です。  
  
 マネージ スレッド プールに属するスレッドを (つまり、あるスレッド<xref:System.Threading.Thread.IsThreadPoolThread%2A>プロパティは`true`) スレッドがバック グラウンドします。 アンマネージ コードからマネージ実行環境を入力するすべてのスレッドがバック グラウンド スレッドとしてマークされます。 すべてのスレッドを作成して、新しい開始によって生成された<xref:System.Threading.Thread>オブジェクトは既定のフォア グラウンド スレッドでします。  
  
 スレッドを使用して、ソケット接続などのアクティビティを監視する場合は、設定、<xref:System.Threading.Thread.IsBackground%2A>プロパティを`true`スレッドが終了してから、プロセスをできないようにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
