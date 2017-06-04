---
title: "Thread.Suspend, Garbage Collection, and Safe Points | Microsoft Docs"
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
  - "suspending threads"
  - "safe points"
  - "threading [.NET Framework], suspending"
  - "threading [.NET Framework], garbage collection"
  - "garbage collection, threads"
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Thread.Suspend, Garbage Collection, and Safe Points
スレッドで <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> を呼び出すと、システムはスレッドの中断が要求されたことを認識しますが、スレッドを実際に中断する前に、スレッドがセーフ ポイントに達するまで待機して、その実行を許可します。  スレッドのセーフ ポイントとは、ガベージ コレクションを行うことができる、実行中のポイントのことです。  
  
 セーフ ポイントに達した後は、中断されたスレッドがマネージ コード内でこれ以上進行しないことが、ランタイムによって保証されます。  マネージ コードの外部で実行されているスレッドは、いつでもガベージ コレクションを実行でき、このスレッドの実行は、マネージ コードの実行の再開を試みるまで継続されます。  
  
> [!NOTE]
>  ガベージ コレクションを実行するには、そのコレクションを実行しているスレッドを除き、すべてのスレッドを中断する必要があります。  各スレッドを中断するには、そのスレッドをセーフ ポイントに移動する必要があります。  
  
## 参照  
 <xref:System.Threading.Thread>   
 <xref:System.GC>   
 [Threading](../../../docs/standard/threading/index.md)   
 [自動メモリ管理](../../../docs/standard/automatic-memory-management.md)