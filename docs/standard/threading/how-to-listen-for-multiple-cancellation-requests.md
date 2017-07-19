---
title: "How to: Listen for Multiple Cancellation Requests | Microsoft Docs"
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
  - "cancellation tokens, joining"
  - "LinkedTokenSource, how to"
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Listen for Multiple Cancellation Requests
この例では、同時に 2 つのキャンセル トークンを待機して、どちらのトークンから要求があっても操作を取り消すことができるようにする方法を示します。  
  
> [!NOTE]
>  \[マイ コードのみ\] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。このエラーは問題にはなりません。  F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。  Visual Studio による処理が最初のエラーで中断しないようにするには、**\[ツール\]** メニューの \[オプション\]、\[デバッグ\] の順にクリックし、\[全般\] で \[マイ コードのみ\] チェック ボックスをオフにします。  
  
## 使用例  
 次の例では、<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> メソッドを使用して、2 つのトークンを 1 つのトークンに結合します。  これにより、結合後のトークンを、キャンセル トークンを 1 つしか引数として受け取らないメソッドに渡すことができます。  この例では、クラス外から渡されるトークンと、クラス内で生成されるトークンの両方をメソッドで監視する必要がある一般的なシナリオを示します。  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 結合後のトークンが <xref:System.OperationCanceledException> をスローする場合、その例外に渡されるトークンは結合後のトークンであり、元のトークンのどちらでもありません。  どちらのトークンが取り消されたかを判断するには、元のトークンの状態を直接確認します。  
  
 この例では、<xref:System.AggregateException> がスローされることはありませんが、現実的な状況ではタスク デリゲートからスローされる <xref:System.OperationCanceledException> と他のすべての例外は、<xref:System.OperationCanceledException> にラップされるので、ここではキャッチされています。  
  
## 参照  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)