---
title: "Using Threads and Threading | Microsoft Docs"
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
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Using Threads and Threading
このセクションの各トピックでは、マネージ スレッドを作成して管理する方法、マネージ スレッドにデータを渡して結果を取得する方法、およびスレッドの破棄や <xref:System.Threading.ThreadAbortException> の処理を行う方法について説明します。  
  
## このセクションの内容  
 [Creating Threads and Passing Data at Start Time](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 データを新しいスレッドに渡す方法とデータを取り戻す方法を含め、マネージ スレッドの作成について説明します。  
  
 [Pausing and Resuming Threads](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 マネージ スレッドを一時中断および再開した場合の動作について説明します。  
  
 [Destroying Threads](../../../docs/standard/threading/destroying-threads.md)  
 マネージ スレッドを破棄した場合の影響、および <xref:System.Threading.ThreadAbortException> の処理方法について説明します。  
  
 [Scheduling Threads](../../../docs/standard/threading/scheduling-threads.md)  
 スレッドの優先順位とそれがスレッドのスケジューリングに及ぼす影響について説明します。  
  
## 関連項目  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Thread> クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。  
  
 <xref:System.Threading.ThreadStart>  
 パラメーターのないスレッド プロシージャを表す <xref:System.Threading.ThreadStart> デリゲートのリファレンス ドキュメントです。  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 スレッド プロシージャにデータを渡す簡単な方法を示します。ただし、厳密な型指定は行いません。  
  
## 関連項目  
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)  
 マネージ スレッド処理の概要を説明します。