---
title: '方法 : イベント プロパティを使用して複数のイベントを処理する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a2dbde5df0f475b0bd7da4b022f11b82b257f40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572867"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="3eb9b-102">方法 : イベント プロパティを使用して複数のイベントを処理する</span><span class="sxs-lookup"><span data-stu-id="3eb9b-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="3eb9b-103">イベント プロパティを使用するには、イベントを発生させるクラスにイベント プロパティを定義し、そのイベントを処理するクラスにイベント プロパティのデリゲートを設定します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="3eb9b-104">1 つのクラスにイベント プロパティを複数実装するには、そのクラス内部に、各イベント用に定義されたデリゲートを格納および保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="3eb9b-105">通常は、イベント キーをインデックスとするデリゲート コレクションを実装することによってこれを実現します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="3eb9b-106">イベントのデリゲートを格納するには、<xref:System.ComponentModel.EventHandlerList> クラスを使用するか、独自のコレクションを実装します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="3eb9b-107">コレクション クラスには、イベント キーに基づいてイベント ハンドラー デリゲートに対する設定、アクセス、および取得を行うメソッドを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="3eb9b-108">たとえば、<xref:System.Collections.Hashtable> クラスを使用したり、<xref:System.Collections.DictionaryBase> クラスからカスタム クラスを派生させたりできます。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="3eb9b-109">デリゲート コレクションの実装の詳細をクラスの外部に公開する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="3eb9b-110">クラス内の各イベント プロパティには、add アクセサー メソッドおよび remove アクセサー メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="3eb9b-111">イベント プロパティの add アクセサーは、入力デリゲート インスタンスをデリゲート コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="3eb9b-112">イベント プロパティの remove アクセサーは、デリゲート コレクションから入力デリゲート インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="3eb9b-113">これらのイベント プロパティ アクセサーでは、イベント プロパティに定義済みのキーを使用して、デリゲート コレクションに対するインスタンスの追加や削除を行います。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="3eb9b-114">イベント プロパティを使用して複数のイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="3eb9b-114">To handle multiple events using event properties</span></span>  
  
1.  <span data-ttu-id="3eb9b-115">イベントを発生させるクラスにデリゲート コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2.  <span data-ttu-id="3eb9b-116">各イベントについて、キーを定義します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-116">Define a key for each event.</span></span>  
  
3.  <span data-ttu-id="3eb9b-117">イベントを発生させるクラスにイベント プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-117">Define the event properties in the class that raises the events.</span></span>  
  
4.  <span data-ttu-id="3eb9b-118">デリゲート コレクションを使用して、各イベント プロパティに対する add アクセサーおよび remove アクセサーを実装します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5.  <span data-ttu-id="3eb9b-119">パブリック イベント プロパティを使用して、イベントを処理するクラスのイベント ハンドラー デリゲートの追加と削除を行います。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eb9b-120">例</span><span class="sxs-lookup"><span data-stu-id="3eb9b-120">Example</span></span>  
 <span data-ttu-id="3eb9b-121">各イベントのデリゲートを格納するために `MouseDown` を使用して、`MouseUp` イベント プロパティおよび <xref:System.ComponentModel.EventHandlerList> イベント プロパティを実装する C# コードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="3eb9b-122">イベント プロパティ コンストラクトのキーワードは、太字で示されています。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-122">The keywords of the event property constructs are in bold type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3eb9b-123">イベント プロパティは、[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3eb9b-123">Event properties are not supported in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="3eb9b-124">参照</span><span class="sxs-lookup"><span data-stu-id="3eb9b-124">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
 [<span data-ttu-id="3eb9b-125">イベント</span><span class="sxs-lookup"><span data-stu-id="3eb9b-125">Events</span></span>](../../../docs/standard/events/index.md)  
 <xref:System.Web.UI.Control.Events%2A>  
 [<span data-ttu-id="3eb9b-126">方法: カスタム イベントを宣言してメモリを節約する</span><span class="sxs-lookup"><span data-stu-id="3eb9b-126">How to: Declare Custom Events To Conserve Memory</span></span>](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
