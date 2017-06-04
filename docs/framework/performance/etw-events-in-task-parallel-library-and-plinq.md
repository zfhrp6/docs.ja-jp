---
title: "タスク並列ライブラリおよび PLINQ での ETW イベント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "タスク、ETW イベント"
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# タスク並列ライブラリおよび PLINQ での ETW イベント
タスク並列ライブラリと PLINQ は、どちらも Event Trace for Windows \(ETW\) イベントを生成します。これらのイベントと Windows パフォーマンス最適化ツールなどのツールを使用すると、アプリケーションのプロファイリンやトラブルシューティングを行うことができます。  ただし、ほとんどのシナリオでは、並列アプリケーション コードのプロファイリングを行うための最善の方法は、[!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)]で [同時実行ビジュアライザー](../Topic/Concurrency%20Visualizer.md) を使用します。  
  
## タスク並列ライブラリでの ETW イベント  
 EVENT\_HEADER 構造体で、<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>、および <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=fullName> によって生成されるイベントの ProviderId GUID を次に示します。  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### 並列ループの開始  
 EVENT\_DESCRIPTOR.Task \= 1  
  
 EVENT\_DESCRIPTOR.Id \= 1  
  
#### \[ユーザー データ\]  
  
|**名前**|**型**|**説明**|  
|------------|-----------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ループを開始した TaskScheduler の ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ループを開始したタスクの ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|fork\/join セマンティクスのあるイベントの入れ子とペアの関係を示すために使用される一意の識別子。|  
|OperationType|<xref:System.Int32?displayProperty=fullName>|ループの種類。<br /><br /> 1 \= ParallelInvoke<br /><br /> 2 \= ParallelFor<br /><br /> 3 \= ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=fullName>|ループ カウンターの開始値。|  
|ExclusiveTo|<xref:System.Int64?displayProperty=fullName>|ループ カウンターの終了値。|  
  
### 並列ループの終了  
 EVENT\_DESCRIPTOR.Task \= 2  
  
 EVENT\_DESCRIPTOR.Id \= 2  
  
#### \[ユーザー データ\]  
  
|**名前**|**型**|**説明**|  
|------------|-----------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ループを開始した TaskScheduler の ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ループを開始したタスクの ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|fork\/join セマンティクスのあるイベントの入れ子とペアの関係を示すために使用される一意の識別子。|  
|totalIterations|<xref:System.Int64?displayProperty=fullName>|イテレーションの総数。|  
  
### 並列呼び出しの開始  
 EVENT\_DESCRIPTOR.Task \= 3  
  
 EVENT\_DESCRIPTOR.Id \= 3  
  
#### \[ユーザー データ\]  
  
|**名前**|**型**|**説明**|  
|------------|-----------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ループを開始した TaskScheduler の ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ループを開始したタスクの ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|fork\/join セマンティクスのあるイベントの入れ子とペアの関係を示すために使用される一意の識別子。|  
|totalIterations|<xref:System.Int64?displayProperty=fullName>|イテレーションの総数。|  
|operationType|<xref:System.Int32?displayProperty=fullName>|ループの種類。<br /><br /> 1 \= ParallelInvoke<br /><br /> 2 \= ParallelFor<br /><br /> 3 \= ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=fullName>|並列呼び出しで実行されるアクションの数。|  
  
### 並列呼び出しの終了  
 EVENT\_DESCRIPTOR.Task \= 4  
  
 EVENT\_DESCRIPTOR.Id \= 4  
  
#### \[ユーザー データ\]  
  
|**名前**|**型**|**説明**|  
|------------|-----------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ループを開始した TaskScheduler の ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ループを開始したタスクの ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|fork\/join セマンティクスのあるイベントの入れ子とペアの関係を示すために使用される一意の識別子。|  
  
## PLINQ での ETW イベント  
 PLINQ での EVENT\_HEADER.ProviderId GUID を次に示します。  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### 並列クエリの開始  
 EVENT\_DESCRIPTOR.Task \= 1  
  
 EVENT\_DESCRIPTOR.Id \= 1  
  
#### \[ユーザー データ\]  
  
|**名前**|**型**|**説明**|  
|------------|-----------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ループを開始した TaskScheduler の ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ループを開始したタスクの ID。|  
|QueryID|<xref:System.Int32?displayProperty=fullName>|一意のクエリ識別子。|  
  
### 並列クエリの終了  
 EVENT\_DESCRIPTOR.Task \= 2  
  
 EVENT\_DESCRIPTOR.Id \= 2  
  
#### \[ユーザー データ\]  
  
|**名前**|**型**|**説明**|  
|------------|-----------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ループを開始した TaskScheduler の ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ループを開始したタスクの ID。|  
|QueryID|<xref:System.Int32?displayProperty=fullName>|一意のクエリ識別子。|  
  
## 参照  
 [.NET Framework の ETW イベント](../../../docs/framework/performance/etw-events.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)