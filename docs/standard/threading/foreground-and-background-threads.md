---
title: フォアグラウンド スレッドとバックグラウンド スレッド
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 476dc75a569224db405eb7498ecb35eb6bda24d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="foreground-and-background-threads"></a>フォアグラウンド スレッドとバックグラウンド スレッド
マネージ スレッドは、バックグラウンド スレッドまたはフォアグラウンド スレッドのいずれかです。 バックグラウンド スレッドは、1 つの例外を除き、フォアグラウンド スレッドと同じです。その例外とは、バックグラウンド スレッドではマネージ実行環境を実行させておくことができないことです。 すべてのフォアグラウンド スレッドが (.exe ファイルがマネージ アセンブリである) マネージ プロセスで停止されると、システムはすべてのバックグラウンド スレッドを停止し、シャットダウンします。  
  
> [!NOTE]
>  プロセスがシャットダウンしているため、ランタイムがバックグラウンド スレッドを停止した場合、スレッドでは例外がスローされません。 ただし、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドがアプリケーション ドメインをアンロードしたために、スレッドが停止された場合、フォアグラウンド スレッドとバックグラウンド スレッドの両方で <xref:System.Threading.ThreadAbortException> がスローされます。  
  
 スレッドがバックグラウンド スレッドであるか、フォアグラウンド スレッドであるかを判断する場合や、その状態を変更する場合は、<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> プロパティを使用します。 スレッドは、<xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定することで、いつでもバックグラウンド スレッドに変更できます。  
  
> [!IMPORTANT]
>  スレッドのフォアグラウンドまたはバックグラウンドの状態が、スレッドのハンドルされない例外の結果に影響することはありません。 .NET framework Version 2.0 では、フォアグラウンドまたはバックグラウンド スレッドのハンドルされない例外により、アプリケーションが終了します。 「[マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)」を参照してください。  
  
 マネージ スレッド プールに属するスレッド (つまり、<xref:System.Threading.Thread.IsThreadPoolThread%2A> プロパティが `true` のスレッド) はバックグラウンド スレッドです。 アンマネージ コードからマネージ実行環境に入るすべてのスレッドは、バックグラウンド スレッドとしてマークされます。 新しい <xref:System.Threading.Thread> オブジェクトを作成して開始することで生成されるすべてのスレッドは、既定でフォアグラウンド スレッドとなります。  
  
 スレッドを使用して、ソケット接続などのアクティビティを監視する場合は、その <xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定して、スレッドがプロセスの終了を回避しないようにします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
