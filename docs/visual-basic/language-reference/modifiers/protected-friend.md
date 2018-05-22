---
title: 保護されたフレンド (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="1d12c-102">保護されたフレンド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d12c-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="1d12c-103">`Protected Friend`キーワードの組み合わせは、メンバー アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="1d12c-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="1d12c-104">両方を設定する[フレンド](friend.md)アクセスおよび[Protected](protected.md)に独自のクラスおよび派生クラスからは、同じアセンブリに任意の場所からアクセスできるように、宣言された要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1d12c-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="1d12c-105">指定できます`Protected Friend`クラスのメンバーにのみ適用することはできません`Protected Friend`構造体のメンバーにため、構造体は継承できません。</span><span class="sxs-lookup"><span data-stu-id="1d12c-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="1d12c-106">Visual Studio で、の F1 ヘルプ`protected friend`いずれかのヘルプを提供[保護](protected.md)または[フレンド](friend.md)です。</span><span class="sxs-lookup"><span data-stu-id="1d12c-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="1d12c-107">IDE では、複合語ではなく、カーソルの下にある 1 つのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1d12c-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="1d12c-108">ルール</span><span class="sxs-lookup"><span data-stu-id="1d12c-108">Rules</span></span>

- <span data-ttu-id="1d12c-109">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="1d12c-109">**Declaration Context.**</span></span> <span data-ttu-id="1d12c-110">使用することができます`Protected Friend`クラス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="1d12c-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="1d12c-111">つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1d12c-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="1d12c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d12c-112">See Also</span></span>

[<span data-ttu-id="1d12c-113">Public</span><span class="sxs-lookup"><span data-stu-id="1d12c-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="1d12c-114">Protected</span><span class="sxs-lookup"><span data-stu-id="1d12c-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="1d12c-115">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="1d12c-115">[Friend](friend.md) </span></span>  
[<span data-ttu-id="1d12c-116">Private</span><span class="sxs-lookup"><span data-stu-id="1d12c-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="1d12c-117">[保護されたプライベート](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="1d12c-117">[Private Protected](./private-protected.md) </span></span>  
[<span data-ttu-id="1d12c-118">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="1d12c-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="1d12c-119">手順</span><span class="sxs-lookup"><span data-stu-id="1d12c-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="1d12c-120">構造体</span><span class="sxs-lookup"><span data-stu-id="1d12c-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="1d12c-121">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="1d12c-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
