---
title: "方法: タスクに EAP パターンをラップする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae9d90c9bb3d0e8d315cbef510cdfe1b54e66da4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>方法: タスクに EAP パターンをラップする
次の例を使用して 1 つのタスクとイベント ベースの非同期パターン (EAP) の操作の任意の順序を公開する方法を示しています、<xref:System.Threading.Tasks.TaskCompletionSource%601>です。 使用する方法も示します、<xref:System.Threading.CancellationToken>メソッドを呼び出す、組み込みの取り消しで、<xref:System.Net.WebClient>オブジェクト。  
  
## <a name="example"></a>例  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>関連項目  
 [TPL と従来の .NET Framework 非同期プログラミング](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
