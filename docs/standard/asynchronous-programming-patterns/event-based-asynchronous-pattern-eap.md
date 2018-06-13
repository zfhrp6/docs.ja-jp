---
title: イベント ベースの非同期パターン (EAP)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7811113244d8c5f7d79a55ebb01f04e99e9bd2a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567807"
---
# <a name="event-based-asynchronous-pattern-eap"></a>イベント ベースの非同期パターン (EAP)
非同期機能をクライアント コードに公開する方法は数多くあります。 イベント ベースの非同期パターンは、クラスが非同期動作を示す 1 つの方法を規定します。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、タスク並列ライブラリによって非同期/並列プログラミングの新しいモデルが提供されます。 詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 イベント ベースの非同期パターンによって、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用できるしくみを説明します。  
  
 [イベントベースの非同期パターンの実装](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 非同期機能を持つクラスをパッケージ化するための標準的な方法について説明します。  
  
 [イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンに従って非同期機能を公開するための要件について説明します。  
  
 [イベントベースの非同期パターンをいつ実装するかの決定](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 どのような場合に、<xref:System.IAsyncResult> パターンではなく、イベント ベースの非同期パターンの実装を選択するかを判断する方法について説明します。  
  
 [チュートリアル: イベントベースの非同期パターンをサポートするコンポーネントの実装](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンを実装するコンポーネントの作成方法を示します。 これは、<xref:System.ComponentModel?displayProperty=nameWithType> 名前空間のヘルパー クラスを使用して実装します。これにより、コンポーネントは任意のアプリケーション モデルで正常に動作します。  
  
 [方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 イベント ベースの非同期パターンをサポートするコンポーネントの使用方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperation> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncOperationManager> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.BackgroundWorker> コンポーネントについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 非同期操作および並列操作のプログラミング モデルについて説明します。  
  
 [スレッド化](../../../docs/standard/threading/index.md)  
 .NET Framework のマルチスレッド機能について説明します。  
  
 [スレッド化](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 C# 言語と Visual Basic 言語のマルチスレッド機能について説明します。  
  
## <a name="see-also"></a>参照  
 [マネージ スレッド処理の実施](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [イベント](../../../docs/standard/events/index.md)  
 [コンポーネントのマルチスレッド](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [非同期プログラミングのデザイン パターン](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
