---
title: "How to: Enable Thread-Tracking Mode in SpinLock | Microsoft Docs"
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
  - "SpinLock, how to enable thread-tracking"
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Enable Thread-Tracking Mode in SpinLock
<xref:System.Threading.SpinLock?displayProperty=fullName> は、待機時間が非常に短いシナリオに使用できる下位レベルの相互排他ロックです。  <xref:System.Threading.SpinLock> は再入不可能です。  スレッドがロックに入った後、再入するには、まず適切にロックを終了する必要があります。  通常、ロックに再入しようとするとデッドロックが発生します。デッドロックのデバッグは非常に困難な場合があります。  開発が簡単になるように、<xref:System.Threading.SpinLock?displayProperty=fullName> はスレッド追跡モードをサポートしています。このモードでは、スレッドが既に保持しているロックに再入しようとすると例外がスローされます。  これにより、ロックを適切に終了しなかったポイントを簡単に特定できるようになります。  スレッド追跡モードを有効にするには、ブール型の入力パラメーターを受け取る <xref:System.Threading.SpinLock> コンストラクターを使用し、引数として `true` を渡します。  開発段階およびテスト段階が完了した後は、パフォーマンスが向上するようにスレッド追跡モードを無効にしてください。  
  
## 使用例  
 スレッド追跡モードの例を次に示します。  ロックを適切に終了する行は、コーディング エラーをシミュレートするためにコメント アウトされています。このエラーの結果は、次のいずれかになります。  
  
-   引数に `true` \(Visual Basic では `True`\) を使用して <xref:System.Threading.SpinLock> が作成された場合は、例外がスローされます。  
  
-   引数に `false` \(Visual Basic では `False`\) を使用して <xref:System.Threading.SpinLock> が作成された場合は、デッドロックが発生します。  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## 参照  
 [SpinLock](../../../docs/standard/threading/spinlock.md)