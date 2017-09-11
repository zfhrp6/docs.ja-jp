---
title: "C# の属性 - C# 言語のツアー"
description: "C# で属性を使用した宣言型のプログラミングについて"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5f290b2cb7074d0b442d5971e5e08a0f6cac55ac
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="attributes"></a><span data-ttu-id="799cd-104">属性</span><span class="sxs-lookup"><span data-stu-id="799cd-104">Attributes</span></span>

<span data-ttu-id="799cd-105">C# プログラムにおける型、メンバー、およびその他のエンティティは、動作の特定の側面を制御する修飾子をサポートします。</span><span class="sxs-lookup"><span data-stu-id="799cd-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="799cd-106">たとえばメソッドのアクセシビリティは、`public`、`protected`、`internal`、および `private` 修飾子を使用して制御されます。</span><span class="sxs-lookup"><span data-stu-id="799cd-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="799cd-107">C# はこの機能を一般化し、宣言情報のユーザー定義型をプログラム エンティティに追加して実行時に取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="799cd-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="799cd-108">プログラムでは、***属性***を定義して使用することにより、この追加の宣言情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="799cd-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="799cd-109">次の例では、プログラムのエンティティに配置して関連するドキュメントへのリンクを提供することができる `HelpAttribute` 属性を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="799cd-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

<span data-ttu-id="799cd-110">[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]</span><span class="sxs-lookup"><span data-stu-id="799cd-110">[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]</span></span>

<span data-ttu-id="799cd-111">すべての属性クラスは、標準ライブラリによって提供される @System.Attribute 基底クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="799cd-111">All attribute classes derive from the @System.Attribute base class provided by the standard library.</span></span> <span data-ttu-id="799cd-112">属性は、関連付けられた宣言の直前に、名前を任意の変数とともに角かっこで囲んで与えることにより、適用できます。</span><span class="sxs-lookup"><span data-stu-id="799cd-112">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="799cd-113">属性の名前が `Attribute` 内で終わる場合、属性の参照時に、名前のその部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="799cd-113">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="799cd-114">たとえば、`HelpAttribute` 属性は次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="799cd-114">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

<span data-ttu-id="799cd-115">[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]</span><span class="sxs-lookup"><span data-stu-id="799cd-115">[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]</span></span>

<span data-ttu-id="799cd-116">この例では `HelpAttribute` を `Widget` クラスにアタッチしています。</span><span class="sxs-lookup"><span data-stu-id="799cd-116">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="799cd-117">別の `HelpAttribute` をクラス内の `Display` メソッドに追加しています。</span><span class="sxs-lookup"><span data-stu-id="799cd-117">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="799cd-118">属性クラスのパブリック コンストラクターは、属性がプログラム エンティティにアタッチされたときに提供する必要がある情報を制御します。</span><span class="sxs-lookup"><span data-stu-id="799cd-118">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="799cd-119">その属性クラスのパブリックの読み取り/書き込みプロパティを参照することにより (`Topic` プロパティへの参照のような)、追加情報を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="799cd-119">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="799cd-120">リフレクションによって特定の属性が要求されると、プログラム ソースで提供される情報で属性クラスのコンストラクターが呼び出され、結果の属性インスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="799cd-120">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="799cd-121">追加情報がプロパティを通じて提供された場合、属性インスタンスが返される前に、これらのプロパティは指定された値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="799cd-121">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="799cd-122">前へ</span><span class="sxs-lookup"><span data-stu-id="799cd-122">Previous</span></span>](delegates.md)

