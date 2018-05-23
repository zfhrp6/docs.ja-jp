---
title: C# の属性 - C# 言語のツアー
description: C# で属性を使用した宣言型のプログラミングについて
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 671023f268ae78d63db8868ef6046b8f13880659
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="attributes"></a><span data-ttu-id="e6833-103">属性</span><span class="sxs-lookup"><span data-stu-id="e6833-103">Attributes</span></span>

<span data-ttu-id="e6833-104">C# プログラムにおける型、メンバー、およびその他のエンティティは、動作の特定の側面を制御する修飾子をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e6833-104">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="e6833-105">たとえばメソッドのアクセシビリティは、`public`、`protected`、`internal`、および `private` 修飾子を使用して制御されます。</span><span class="sxs-lookup"><span data-stu-id="e6833-105">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="e6833-106">C# はこの機能を一般化し、宣言情報のユーザー定義型をプログラム エンティティに追加して実行時に取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e6833-106">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="e6833-107">プログラムでは、***属性***を定義して使用することにより、この追加の宣言情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6833-107">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="e6833-108">次の例では、プログラムのエンティティに配置して関連するドキュメントへのリンクを提供することができる `HelpAttribute` 属性を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="e6833-108">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="e6833-109">すべての属性クラスは、標準ライブラリによって提供される <xref:System.Attribute> 基底クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="e6833-109">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="e6833-110">属性は、関連付けられた宣言の直前に、名前を任意の変数とともに角かっこで囲んで与えることにより、適用できます。</span><span class="sxs-lookup"><span data-stu-id="e6833-110">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="e6833-111">属性の名前が `Attribute` 内で終わる場合、属性の参照時に、名前のその部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e6833-111">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="e6833-112">たとえば、`HelpAttribute` は次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6833-112">For example, the `HelpAttribute` can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="e6833-113">この例では `HelpAttribute` を `Widget` クラスにアタッチしています。</span><span class="sxs-lookup"><span data-stu-id="e6833-113">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="e6833-114">別の `HelpAttribute` をクラス内の `Display` メソッドに追加しています。</span><span class="sxs-lookup"><span data-stu-id="e6833-114">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="e6833-115">属性クラスのパブリック コンストラクターは、属性がプログラム エンティティにアタッチされたときに提供する必要がある情報を制御します。</span><span class="sxs-lookup"><span data-stu-id="e6833-115">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="e6833-116">その属性クラスのパブリックの読み取り/書き込みプロパティを参照することにより (`Topic` プロパティへの参照のような)、追加情報を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="e6833-116">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="e6833-117">リフレクションによって特定の属性が要求されると、プログラム ソースで提供される情報で属性クラスのコンストラクターが呼び出され、結果の属性インスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="e6833-117">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="e6833-118">追加情報がプロパティを通じて提供された場合、属性インスタンスが返される前に、これらのプロパティは指定された値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e6833-118">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="e6833-119">前へ</span><span class="sxs-lookup"><span data-stu-id="e6833-119">Previous</span></span>](delegates.md)
