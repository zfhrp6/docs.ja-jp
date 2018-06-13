---
title: C# インターフェイス - C# 言語のツアー
description: C# の型によって実装されるコントラクトを定義するインターフェイス
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 0ad02d5b2792656783d93b2cc767aeb81efbc30e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343897"
---
# <a name="interfaces"></a><span data-ttu-id="d5215-103">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5215-103">Interfaces</span></span>

<span data-ttu-id="d5215-104">***インターフェイス***は、クラスと構造体によって実装できるコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5215-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="d5215-105">1 つのインターフェイスには、メソッド、プロパティ、イベント、およびインデクサーが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5215-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="d5215-106">インターフェイスでは、定義するメンバーの実装は行いません。インターフェイスを実装するクラスまたは構造体によって提供される必要があるメンバーを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="d5215-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="d5215-107">インターフェイスは***多重継承***を使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5215-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="d5215-108">次の例では、インターフェイス `IComboBox` は `ITextBox` と `IListBox` の両方から継承します。</span><span class="sxs-lookup"><span data-stu-id="d5215-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="d5215-109">クラスと構造体は、複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="d5215-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="d5215-110">次の例では、クラス `EditBox` は `IControl` と `IDataBound` の両方を実装しています。</span><span class="sxs-lookup"><span data-stu-id="d5215-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="d5215-111">クラスまたは構造体が特定のインターフェイスを実装する場合、そのクラスまたは構造体のインスタンスはそのインターフェイス型に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="d5215-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="d5215-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d5215-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="d5215-113">インスタンスが特定のインターフェイスを静的に実装しないとわかっている場合は、動的な型キャストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5215-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="d5215-114">たとえば、次のステートメントは動的な型キャストを使用して、オブジェクトの `IControl` および `IDataBound` のインターフェイス実装を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5215-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="d5215-115">オブジェクトの実行時の実際の型が `EditBox` であるため、キャストは成功します。</span><span class="sxs-lookup"><span data-stu-id="d5215-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="d5215-116">前述の `EditBox` クラスで、`IControl` インターフェイスからの `Paint` メソッドおよび `IDataBound` インターフェイスからの `Bind` メソッドは、パブリック メンバーを使用して実装されています。</span><span class="sxs-lookup"><span data-stu-id="d5215-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="d5215-117">C# ではまた、明示的な***インターフェイス メンバーの実装***をサポートしており、クラスまたは構造体がメンバーをパブリックにするのを回避するようにできます。</span><span class="sxs-lookup"><span data-stu-id="d5215-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="d5215-118">明示的なインターフェイス メンバーの実装は、完全修飾のインターフェイス メンバー名を使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d5215-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="d5215-119">たとえば、`EditBox` クラスは、次のように明示的なインターフェイス メンバーの実装を使用して、`IControl.Paint` メソッドおよび `IDataBound.Bind` メソッドを実装できます。</span><span class="sxs-lookup"><span data-stu-id="d5215-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="d5215-120">明示的なインターフェイス メンバーは、インターフェイス型を経由してのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d5215-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="d5215-121">たとえば、前の EditBox クラスで提供された `IControl.Paint` の実装は、最初に `EditBox` 参照を `IControl` インターフェイス型に変換することでしか呼び出しできません。</span><span class="sxs-lookup"><span data-stu-id="d5215-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="d5215-122">[前へ](arrays.md)
[次へ](enums.md)</span><span class="sxs-lookup"><span data-stu-id="d5215-122">[Previous](arrays.md)
[Next](enums.md)</span></span>
