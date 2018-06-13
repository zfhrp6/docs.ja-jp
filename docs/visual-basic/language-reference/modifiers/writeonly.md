---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599204"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="8ea4f-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea4f-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="8ea4f-103">プロパティの記述が読み取らないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ea4f-104">コメント</span><span class="sxs-lookup"><span data-stu-id="8ea4f-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8ea4f-105">ルール</span><span class="sxs-lookup"><span data-stu-id="8ea4f-105">Rules</span></span>  
 <span data-ttu-id="8ea4f-106">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="8ea4f-106">**Declaration Context.**</span></span> <span data-ttu-id="8ea4f-107">`WriteOnly` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="8ea4f-108">つまりの宣言コンテキスト、`WriteOnly`プロパティは、クラス、構造体、またはモジュールにある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="8ea4f-109">としてプロパティを宣言する`WriteOnly`が変数ではありません。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="8ea4f-110">WriteOnly を使用する場合</span><span class="sxs-lookup"><span data-stu-id="8ea4f-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="8ea4f-111">コンシューマー コード値を設定するができないことができる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="8ea4f-112">たとえば、ソーシャル登録番号やパスワードなどの機密データを設定していないすべてのコンポーネントによるアクセスから保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="8ea4f-113">このような場合は、使用することができます、`WriteOnly`プロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ea4f-114">定義して使用するときに、`WriteOnly`プロパティ、次の追加の保護手段を検討してください。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="8ea4f-115">**上書きします。**</span><span class="sxs-lookup"><span data-stu-id="8ea4f-115">**Overriding.**</span></span> <span data-ttu-id="8ea4f-116">場合は、プロパティ、クラスのメンバーである、許可が既定に[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、宣言しないと`Overridable`または`MustOverride`です。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="8ea4f-117">これは派生クラスがオーバーライドによって不要なアクセスを作成することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="8ea4f-118">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="8ea4f-118">**Access Level.**</span></span> <span data-ttu-id="8ea4f-119">1 つまたは複数の変数で、プロパティの機密データを保持する場合は、宣言[プライベート](../../../visual-basic/language-reference/modifiers/private.md)できるように、その他のコードはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="8ea4f-120">**暗号化します。**</span><span class="sxs-lookup"><span data-stu-id="8ea4f-120">**Encryption.**</span></span> <span data-ttu-id="8ea4f-121">プレーン テキストではなく、暗号化された形式では、すべての機密データを格納します。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="8ea4f-122">何らかの理由で、悪意のあるコードそのメモリ領域にアクセスできる場合より少なく、データを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="8ea4f-123">暗号化も機密データをシリアル化する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="8ea4f-124">**リセットしています。**</span><span class="sxs-lookup"><span data-stu-id="8ea4f-124">**Resetting.**</span></span> <span data-ttu-id="8ea4f-125">クラス、構造体、またはプロパティを定義するモジュールが終了するときに既定値またはその他の意味のない値に機微なデータをリセットします。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="8ea4f-126">これにより、一般的なアクセスにそのメモリ領域が解放されるとき、保護を強化できます。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="8ea4f-127">**永続化します。**</span><span class="sxs-lookup"><span data-stu-id="8ea4f-127">**Persistence.**</span></span> <span data-ttu-id="8ea4f-128">これを回避する場合、たとえば、ディスク上の任意の機密データは保持されません。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="8ea4f-129">クリップボードには、機密データは書き込みませんも、します。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="8ea4f-130">`WriteOnly`修飾子は、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ea4f-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8ea4f-131">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="8ea4f-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ea4f-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ea4f-132">See Also</span></span>  
 [<span data-ttu-id="8ea4f-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8ea4f-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="8ea4f-134">Private</span><span class="sxs-lookup"><span data-stu-id="8ea4f-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="8ea4f-135">キーワード</span><span class="sxs-lookup"><span data-stu-id="8ea4f-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
