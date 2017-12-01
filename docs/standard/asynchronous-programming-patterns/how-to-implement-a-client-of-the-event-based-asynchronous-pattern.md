---
title: "方法 : イベントベースの非同期パターンのクライアントを実装する"
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
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b70d4ba205d39ad8fcbc7c7f6fa1f5b34a36c98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>方法 : イベントベースの非同期パターンのクライアントを実装する
次のコード例に準拠しているコンポーネントを使用して、[イベント ベースの非同期パターン概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)です。 この例のフォームを使用して、`PrimeNumberCalculator`で記述されたコンポーネント[する方法: イベント ベースの非同期パターンをサポートするコンポーネントを実装する](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)です。  
  
 この例を使用するプロジェクトを実行するときにグリッドと 2 つのボタンを使用「素数を計算」フォームが表示されます:**新しいタスクの開始**と**キャンセル**です。 クリックすることができます、**新しいタスクの開始**連続して数回のボタンをクリックし、非同期操作をクリックするたびにランダムに生成されたテスト数が素数かどうかを判断する計算が開始されます。 進行状況およびインクリメンタル結果に定期的に、フォームが表示されます。 各操作には、固有のタスク ID が割り当てられます。 計算の結果に表示されます、**結果**列です。 テストの数が最適でない場合、ラベルが付いて**複合、**され、最初の除数が表示されます。  
  
 保留中の操作をキャンセルできます、**キャンセル**ボタンをクリックします。 複数選択が可能です。  
  
> [!NOTE]
>  ほとんどの数値には、素数はできません。 いくつかの完了操作の実行後、素数が見つからない場合は、単に以上のタスクを起動し、いくつか含まれる素数を検索する最終的にします。  
  
## <a name="example"></a>例  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
