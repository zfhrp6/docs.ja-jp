---
title: メンバー (F#)
description: F# のプログラミング言語でオブジェクトのメンバーについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 6dcdb1d7fa061fb838d4aa8f7a2912fd168c3781
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562208"
---
# <a name="members"></a><span data-ttu-id="50633-103">メンバー</span><span class="sxs-lookup"><span data-stu-id="50633-103">Members</span></span>

<span data-ttu-id="50633-104">このセクションでは、F# オブジェクト型のメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-104">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="50633-105">コメント</span><span class="sxs-lookup"><span data-stu-id="50633-105">Remarks</span></span>
<span data-ttu-id="50633-106">*メンバー*は、型定義の一部の機能であり、`member`キーワードを使用して宣言されます。</span><span class="sxs-lookup"><span data-stu-id="50633-106">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="50633-107">レコード、クラス、判別共用体、インターフェイス、構造体などの F# オブジェクト型がメンバーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="50633-107">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="50633-108">詳細については、「[レコード](../records.md)」、「[クラス](../classes.md)」、「[判別共用体](../discriminated-Unions.md)」、「[インターフェイス](../interfaces.md)」、および「[構造体](../structures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50633-108">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="50633-109">メンバーは通常、型のパブリック インターフェイスを構成するので、特に指定しない限りパブリックになります。</span><span class="sxs-lookup"><span data-stu-id="50633-109">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="50633-110">プライベートまたは内部としてメンバーを宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="50633-110">Members can also be declared private or internal.</span></span> <span data-ttu-id="50633-111">詳細については、「[Access Control](../access-Control.md)」(アクセス制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50633-111">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="50633-112">型のシグネチャを使用して、型の特定のメンバーを公開するか公開しないこともできます。</span><span class="sxs-lookup"><span data-stu-id="50633-112">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="50633-113">詳細については、「[シグネチャ](../signatures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50633-113">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="50633-114">クラスでのみ使用されるプライベート フィールドと `do` バインドは、パブリック インターフェイスの一部ではなく、`member` キーワードを使用して宣言されないので、真のメンバーではありませんが、このセクションではそれらについても説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-114">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="50633-115">関連トピック</span><span class="sxs-lookup"><span data-stu-id="50633-115">Related Topics</span></span>


|<span data-ttu-id="50633-116">トピック</span><span class="sxs-lookup"><span data-stu-id="50633-116">Topic</span></span>|<span data-ttu-id="50633-117">説明</span><span class="sxs-lookup"><span data-stu-id="50633-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="50633-118">クラス内の `let` バインド</span><span class="sxs-lookup"><span data-stu-id="50633-118">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="50633-119">クラス内のプライベート フィールドと関数の定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-119">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="50633-120">クラス内の `do` バインド</span><span class="sxs-lookup"><span data-stu-id="50633-120">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="50633-121">オブジェクトの初期化コードの仕様について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-121">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="50633-122">プロパティ</span><span class="sxs-lookup"><span data-stu-id="50633-122">Properties</span></span>](properties.md)|<span data-ttu-id="50633-123">クラスのプロパティ メンバーとその他の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-123">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="50633-124">インデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="50633-124">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="50633-125">クラスの配列に似たプロパティとその他の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-125">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="50633-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="50633-126">Methods</span></span>](methods.md)|<span data-ttu-id="50633-127">型のメンバーである関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-127">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="50633-128">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="50633-128">Constructors</span></span>](constructors.md)|<span data-ttu-id="50633-129">型のオブジェクトを初期化する特別な関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-129">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="50633-130">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="50633-130">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="50633-131">型のカスタマイズした演算子の定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-131">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="50633-132">イベント</span><span class="sxs-lookup"><span data-stu-id="50633-132">Events</span></span>](events.md)|<span data-ttu-id="50633-133">F# のイベントおよびイベント処理のサポートの定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-133">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="50633-134">明示的なフィールド: `val` キーワード</span><span class="sxs-lookup"><span data-stu-id="50633-134">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="50633-135">型の初期化されていないフィールドの定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="50633-135">Describes the definition of uninitialized fields in a type.</span></span>|
