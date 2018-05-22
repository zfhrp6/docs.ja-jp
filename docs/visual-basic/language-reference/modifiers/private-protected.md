---
title: Private Protected (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="2955c-102">Private Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2955c-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="2955c-103">`Private Protected`キーワードの組み合わせは、メンバー アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="2955c-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2955c-104">A`Private Protected`メンバーがアクセスできるは、外側のクラスから派生した型およびその外側のクラスのすべてのメンバーでは、含んでいるアセンブリ内にある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="2955c-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="2955c-105">指定できます`Private Protected`クラスのメンバーにのみ適用することはできません`Private Protected`構造体のメンバーにため、構造体は継承できません。</span><span class="sxs-lookup"><span data-stu-id="2955c-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="2955c-106">`Private Protected`アクセス修飾子は Visual Basic 15.5 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2955c-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="2955c-107">これを使用するには、Visual Basic プロジェクト (\*.vbproj) ファイルに次の要素を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2955c-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="2955c-108">Visual Basic 15.5 として時間またはそれ以降は、システムにインストールされているが、最新バージョンの Visual Basic コンパイラでサポートされているすべての言語機能を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="2955c-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="2955c-109">Visual Studio で、の F1 ヘルプ`private protected`いずれかのヘルプを提供[プライベート](private.md)または[保護](protected.md)です。</span><span class="sxs-lookup"><span data-stu-id="2955c-109">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="2955c-110">IDE では、複合語ではなく、カーソルの下にある 1 つのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2955c-110">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="2955c-111">ルール</span><span class="sxs-lookup"><span data-stu-id="2955c-111">Rules</span></span>

- <span data-ttu-id="2955c-112">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="2955c-112">**Declaration Context.**</span></span> <span data-ttu-id="2955c-113">使用することができます`Private Protected`クラス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="2955c-113">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="2955c-114">つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2955c-114">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="2955c-115">動作</span><span class="sxs-lookup"><span data-stu-id="2955c-115">Behavior</span></span>

- <span data-ttu-id="2955c-116">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="2955c-116">**Access Level.**</span></span> <span data-ttu-id="2955c-117">クラスのすべてのコードは、その要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2955c-117">All code in a class can access its elements.</span></span> <span data-ttu-id="2955c-118">基本クラスから派生し、同じアセンブリに含まれる任意のクラス内のコードはすべてにアクセスできます、`Private Protected`基底クラスの要素。</span><span class="sxs-lookup"><span data-stu-id="2955c-118">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="2955c-119">基本クラスから派生し、別のアセンブリに含まれるクラスにコードが、基底クラスにアクセスできませんただし、`Private Protected`要素。</span><span class="sxs-lookup"><span data-stu-id="2955c-119">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="2955c-120">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="2955c-120">**Access Modifiers.**</span></span> <span data-ttu-id="2955c-121">アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。</span><span class="sxs-lookup"><span data-stu-id="2955c-121">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2955c-122">アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="2955c-122">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="2955c-123">`Private Protected` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2955c-123">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="2955c-124">[Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)の入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="2955c-124">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="2955c-125">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-125">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2955c-126">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-126">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="2955c-127">[Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)デリゲートのクラスで入れ子になった</span><span class="sxs-lookup"><span data-stu-id="2955c-127">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="2955c-128">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="2955c-129">[Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)eumeration のクラスで入れ子になった</span><span class="sxs-lookup"><span data-stu-id="2955c-129">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="2955c-130">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-130">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2955c-131">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-131">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="2955c-132">[Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)インターフェイスのクラスで入れ子になった</span><span class="sxs-lookup"><span data-stu-id="2955c-132">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="2955c-133">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="2955c-134">[ステートメントを構造体](../../../visual-basic/language-reference/statements/structure-statement.md)クラスで入れ子になった構造体</span><span class="sxs-lookup"><span data-stu-id="2955c-134">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="2955c-135">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="2955c-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2955c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2955c-136">See Also</span></span>

[<span data-ttu-id="2955c-137">Public</span><span class="sxs-lookup"><span data-stu-id="2955c-137">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="2955c-138">Protected</span><span class="sxs-lookup"><span data-stu-id="2955c-138">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="2955c-139">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="2955c-139">[Friend](friend.md) </span></span>  
[<span data-ttu-id="2955c-140">Private</span><span class="sxs-lookup"><span data-stu-id="2955c-140">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="2955c-141">[保護されたフレンド](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="2955c-141">[Protected Friend](./protected-friend.md) </span></span>  
[<span data-ttu-id="2955c-142">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="2955c-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="2955c-143">手順</span><span class="sxs-lookup"><span data-stu-id="2955c-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="2955c-144">構造体</span><span class="sxs-lookup"><span data-stu-id="2955c-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="2955c-145">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="2955c-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
