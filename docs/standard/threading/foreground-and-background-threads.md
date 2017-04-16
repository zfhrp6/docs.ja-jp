---
title: "Foreground and Background Threads | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], foreground"
  - "threading [.NET Framework], background"
  - "foreground threads"
  - "background threads"
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Foreground and Background Threads
マネージ スレッドは、バックグラウンド スレッドかフォアグラウンド スレッドのどちらかです。  バックグラウンド スレッドは、マネージ実行環境を実行されたままにしない点を除き、フォアグラウンド スレッドと同じです。  すべてのフォアグラウンド スレッドがマネージ プロセス \(.exe ファイルがマネージ アセンブリであるプロセス\) で停止されると、システムはすべてのバックグラウンド スレッドを停止し、シャットダウンします。  
  
> [!NOTE]
>  プロセスの終了によってランタイムがバックグラウンド スレッドを停止する場合、スレッドで例外はスローされません。  ただし、<xref:System.AppDomain.Unload%2A?displayProperty=fullName> メソッドがアプリケーション ドメインをアンロードしたためにスレッドが停止する場合、フォアグラウンドとバックグラウンドの両方のスレッドで <xref:System.Threading.ThreadAbortException> がスローされます。  
  
 スレッドがバックグラウンド スレッドかフォアグランド スレッドかを特定したり、その状態を変更したりするには、<xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName> プロパティを使用します。  <xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定すると、スレッドをいつでもバックグラウンド スレッドに変更できます。  
  
> [!IMPORTANT]
>  スレッドの状態 \(フォアグランドまたはバックグラウンド\) は、スレッドで処理されない例外の結果には影響しません。  .NET Framework Version 2.0 では、フォアグランド スレッドまたはバックグラウンド スレッドで処理されない例外が発生すると、アプリケーションが終了します。  「[Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md)」を参照してください。  
  
 マネージ スレッド プールに属しているスレッド \(つまり、<xref:System.Threading.Thread.IsThreadPoolThread%2A> プロパティが `true` のスレッド\) はバックグラウンド スレッドです。  アンマネージ コードからマネージ実行環境に入るすべてのスレッドは、バックグラウンド スレッドとしてマークされます。  新しい <xref:System.Threading.Thread> オブジェクトを作成および起動して生成されたすべてのスレッドは、既定でフォアグラウンド スレッドです。  
  
 ソケット接続などの動作を監視するためにスレッドを使用する場合、スレッドによってプロセスが終了しないように、<xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定します。  
  
## 参照  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadAbortException>