---
title: "C# インターフェイス - C# 言語のツアー"
description: "C# の型によって実装されるコントラクトを定義するインターフェイス"
keywords: ".NET, C#, インターフェイス, 多重継承, ポリモーフィズム"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="interfaces"></a><span data-ttu-id="865ff-104">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="865ff-104">Interfaces</span></span>

<span data-ttu-id="865ff-105">***インターフェイス***は、クラスと構造体によって実装できるコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="865ff-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="865ff-106">1 つのインターフェイスには、メソッド、プロパティ、イベント、およびインデクサーが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="865ff-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="865ff-107">インターフェイスでは、定義するメンバーの実装は行いません。インターフェイスを実装するクラスまたは構造体によって提供される必要があるメンバーを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="865ff-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="865ff-108">インターフェイスは***多重継承***を使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="865ff-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="865ff-109">次の例では、インターフェイス `IComboBox` は `ITextBox` と `IListBox` の両方から継承します。</span><span class="sxs-lookup"><span data-stu-id="865ff-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

<span data-ttu-id="865ff-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span><span class="sxs-lookup"><span data-stu-id="865ff-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span></span>

<span data-ttu-id="865ff-111">クラスと構造体は、複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="865ff-111">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="865ff-112">次の例では、クラス `EditBox` は `IControl` と `IDataBound` の両方を実装しています。</span><span class="sxs-lookup"><span data-stu-id="865ff-112">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

<span data-ttu-id="865ff-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span><span class="sxs-lookup"><span data-stu-id="865ff-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span></span>

<span data-ttu-id="865ff-114">クラスまたは構造体が特定のインターフェイスを実装する場合、そのクラスまたは構造体のインスタンスはそのインターフェイス型に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="865ff-114">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="865ff-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="865ff-115">For example</span></span>

<span data-ttu-id="865ff-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span><span class="sxs-lookup"><span data-stu-id="865ff-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span></span>

<span data-ttu-id="865ff-117">インスタンスが特定のインターフェイスを静的に実装しないとわかっている場合は、動的な型キャストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="865ff-117">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="865ff-118">たとえば、次のステートメントは動的な型キャストを使用して、オブジェクトの `IControl` および `IDataBound` のインターフェイス実装を取得します。</span><span class="sxs-lookup"><span data-stu-id="865ff-118">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="865ff-119">オブジェクトの実行時の実際の型が `EditBox` であるため、キャストは成功します。</span><span class="sxs-lookup"><span data-stu-id="865ff-119">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

<span data-ttu-id="865ff-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span><span class="sxs-lookup"><span data-stu-id="865ff-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span></span>

<span data-ttu-id="865ff-121">前述の `EditBox` クラスで、`IControl` インターフェイスからの `Paint` メソッドおよび `IDataBound` インターフェイスからの `Bind` メソッドは、パブリック メンバーを使用して実装されています。</span><span class="sxs-lookup"><span data-stu-id="865ff-121">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="865ff-122">C# ではまた、明示的な***インターフェイス メンバーの実装***をサポートしており、クラスまたは構造体がメンバーをパブリックにするのを回避するようにできます。</span><span class="sxs-lookup"><span data-stu-id="865ff-122">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="865ff-123">明示的なインターフェイス メンバーの実装は、完全修飾のインターフェイス メンバー名を使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="865ff-123">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="865ff-124">たとえば、`EditBox` クラスは、次のように明示的なインターフェイス メンバーの実装を使用して、`IControl.Paint` メソッドおよび `IDataBound.Bind` メソッドを実装できます。</span><span class="sxs-lookup"><span data-stu-id="865ff-124">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

<span data-ttu-id="865ff-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span><span class="sxs-lookup"><span data-stu-id="865ff-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span></span>

<span data-ttu-id="865ff-126">明示的なインターフェイス メンバーは、インターフェイス型を経由してのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="865ff-126">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="865ff-127">たとえば、前の EditBox クラスで提供された `IControl.Paint` の実装は、最初に `EditBox` 参照を `IControl` インターフェイス型に変換することでしか呼び出しできません。</span><span class="sxs-lookup"><span data-stu-id="865ff-127">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

<span data-ttu-id="865ff-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span><span class="sxs-lookup"><span data-stu-id="865ff-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="865ff-129">[前へ](arrays.md)
[次へ](enums.md)</span><span class="sxs-lookup"><span data-stu-id="865ff-129">[Previous](arrays.md)
[Next](enums.md)</span></span>

