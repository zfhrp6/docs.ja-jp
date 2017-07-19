---
title: "方法 : イベント プロパティを使用して複数のイベントを処理する | Microsoft Docs"
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
  - "イベント処理 [.NET Framework], 複数のイベントで"
  - "イベント プロパティ [.NET Framework]"
  - "イベント [.NET Framework], 複数の"
  - "複数のイベント [.NET Framework]"
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : イベント プロパティを使用して複数のイベントを処理する
イベント プロパティを使用するには、イベントを発生させるクラスにイベント プロパティを定義し、そのイベントを処理するクラスにイベント プロパティのデリゲートを設定します。  1 つのクラスにイベント プロパティを複数実装するには、そのクラス内部に、各イベント用に定義されたデリゲートを格納および保持する必要があります。  通常は、イベント キーをインデックスとするデリゲート コレクションを実装することによってこれを実現します。  
  
 イベントのデリゲートを格納するには、<xref:System.ComponentModel.EventHandlerList> クラスを使用するか、独自のコレクションを実装します。  コレクション クラスには、イベント キーに基づいてイベント ハンドラー デリゲートに対する設定、アクセス、および取得を行うメソッドを用意する必要があります。  たとえば、<xref:System.Collections.Hashtable> クラスを使用したり、<xref:System.Collections.DictionaryBase> クラスからカスタム クラスを派生させたりできます。  デリゲート コレクションの実装の詳細をクラスの外部に公開する必要はありません。  
  
 クラス内の各イベント プロパティには、add アクセサー メソッドおよび remove アクセサー メソッドを定義します。  イベント プロパティの add アクセサーは、入力デリゲート インスタンスをデリゲート コレクションに追加します。  イベント プロパティの remove アクセサーは、デリゲート コレクションから入力デリゲート インスタンスを削除します。  これらのイベント プロパティ アクセサーでは、イベント プロパティに定義済みのキーを使用して、デリゲート コレクションに対するインスタンスの追加や削除を行います。  
  
### イベント プロパティを使用して複数のイベントを処理するには  
  
1.  イベントを発生させるクラスにデリゲート コレクションを定義します。  
  
2.  各イベントについて、キーを定義します。  
  
3.  イベントを発生させるクラスにイベント プロパティを定義します。  
  
4.  デリゲート コレクションを使用して、各イベント プロパティに対する add アクセサーおよび remove アクセサーを実装します。  
  
5.  パブリック イベント プロパティを使用して、イベントを処理するクラスのイベント ハンドラー デリゲートの追加と削除を行います。  
  
## 使用例  
 各イベントのデリゲートを格納するために `MouseDown` を使用して、`MouseUp` イベント プロパティおよび <xref:System.ComponentModel.EventHandlerList> イベント プロパティを実装する C\# コードの例を次に示します。  イベント プロパティ コンストラクトのキーワードは、太字で示されています。  
  
> [!NOTE]
>  イベント プロパティは、[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] ではサポートされていません。  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## 参照  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=fullName>   
 [イベント](../../../docs/standard/events/index.md)   
 [System.Web.UI.Control.Events](frlrfSystemWebUIControlClassEventsTopic)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)