---
title: メンバー (F#)
description: F# のプログラミング言語でオブジェクトのメンバーについて説明します。
keywords: visual f#, f#, 関数型プログラミング
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a><span data-ttu-id="8aec3-104">メンバー</span><span class="sxs-lookup"><span data-stu-id="8aec3-104">Members</span></span>

<span data-ttu-id="8aec3-105">このセクションでは、F# オブジェクト型のメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-105">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="8aec3-106">コメント</span><span class="sxs-lookup"><span data-stu-id="8aec3-106">Remarks</span></span>
<span data-ttu-id="8aec3-107">*メンバー*は、型定義の一部の機能であり、`member`キーワードを使用して宣言されます。</span><span class="sxs-lookup"><span data-stu-id="8aec3-107">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="8aec3-108">レコード、クラス、判別共用体、インターフェイス、構造体などの F# オブジェクト型がメンバーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8aec3-108">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="8aec3-109">詳細については、「[レコード](../records.md)」、「[クラス](../classes.md)」、「[判別共用体](../discriminated-Unions.md)」、「[インターフェイス](../interfaces.md)」、および「[構造体](../structures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aec3-109">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="8aec3-110">メンバーは通常、型のパブリック インターフェイスを構成するので、特に指定しない限りパブリックになります。</span><span class="sxs-lookup"><span data-stu-id="8aec3-110">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="8aec3-111">プライベートまたは内部としてメンバーを宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="8aec3-111">Members can also be declared private or internal.</span></span> <span data-ttu-id="8aec3-112">詳細については、「[Access Control](../access-Control.md)」(アクセス制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aec3-112">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="8aec3-113">型のシグネチャを使用して、型の特定のメンバーを公開するか公開しないこともできます。</span><span class="sxs-lookup"><span data-stu-id="8aec3-113">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="8aec3-114">詳細については、「[シグネチャ](../signatures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aec3-114">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="8aec3-115">クラスでのみ使用されるプライベート フィールドと `do` バインドは、パブリック インターフェイスの一部ではなく、`member` キーワードを使用して宣言されないので、真のメンバーではありませんが、このセクションではそれらについても説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-115">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="8aec3-116">関連トピック</span><span class="sxs-lookup"><span data-stu-id="8aec3-116">Related Topics</span></span>


|<span data-ttu-id="8aec3-117">トピック</span><span class="sxs-lookup"><span data-stu-id="8aec3-117">Topic</span></span>|<span data-ttu-id="8aec3-118">説明</span><span class="sxs-lookup"><span data-stu-id="8aec3-118">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="8aec3-119">クラス内の `let` バインド</span><span class="sxs-lookup"><span data-stu-id="8aec3-119">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="8aec3-120">クラス内のプライベート フィールドと関数の定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-120">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="8aec3-121">クラス内の `do` バインド</span><span class="sxs-lookup"><span data-stu-id="8aec3-121">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="8aec3-122">オブジェクトの初期化コードの仕様について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-122">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="8aec3-123">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8aec3-123">Properties</span></span>](properties.md)|<span data-ttu-id="8aec3-124">クラスのプロパティ メンバーとその他の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-124">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="8aec3-125">インデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="8aec3-125">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="8aec3-126">クラスの配列に似たプロパティとその他の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-126">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="8aec3-127">メソッド</span><span class="sxs-lookup"><span data-stu-id="8aec3-127">Methods</span></span>](methods.md)|<span data-ttu-id="8aec3-128">型のメンバーである関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-128">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="8aec3-129">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="8aec3-129">Constructors</span></span>](constructors.md)|<span data-ttu-id="8aec3-130">型のオブジェクトを初期化する特別な関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-130">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="8aec3-131">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="8aec3-131">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="8aec3-132">型のカスタマイズした演算子の定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-132">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="8aec3-133">イベント</span><span class="sxs-lookup"><span data-stu-id="8aec3-133">Events</span></span>](events.md)|<span data-ttu-id="8aec3-134">F# のイベントおよびイベント処理のサポートの定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-134">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="8aec3-135">明示的なフィールド: `val` キーワード</span><span class="sxs-lookup"><span data-stu-id="8aec3-135">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="8aec3-136">型の初期化されていないフィールドの定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="8aec3-136">Describes the definition of uninitialized fields in a type.</span></span>|
