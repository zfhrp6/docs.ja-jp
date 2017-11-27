---
title: "クラスの明示的なインスタンスを指定しないで、共有メソッドまたは共有メンバー初期化子内からクラスのインスタンス メンバーへ参照することはできません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="4ece0-102">クラスの明示的なインスタンスを指定しないで、共有メソッドまたは共有メンバー初期化子内からクラスのインスタンス メンバーへ参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="4ece0-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="4ece0-103">クラスを共有プロシージャ内での非共有メンバーを参照しようとしました。</span><span class="sxs-lookup"><span data-stu-id="4ece0-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="4ece0-104">次の例では、このような状況を示します。</span><span class="sxs-lookup"><span data-stu-id="4ece0-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="4ece0-105">前の例では、代入ステートメントで`x = 10`でこのエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4ece0-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="4ece0-106">これは、ため、インスタンス変数にアクセスしようとして、共有プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="4ece0-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="4ece0-107">変数`x`として宣言されていないため、インスタンス メンバーは、 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ece0-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="4ece0-108">クラスの各インスタンス`sample`独自の個別の変数が含まれる`x`です。</span><span class="sxs-lookup"><span data-stu-id="4ece0-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="4ece0-109">1 つのインスタンスを設定またはの値を変更するときに`x`の値は影響を与えない`x`他のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="4ece0-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="4ece0-110">ただし、プロシージャ`setX`は`Shared`クラスのすべてのインスタンス間で`sample`です。</span><span class="sxs-lookup"><span data-stu-id="4ece0-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="4ece0-111">つまり、クラスのインスタンスのいずれかに関連付けられていないことが、個々 のインスタンスから独立して動作ではなくです。</span><span class="sxs-lookup"><span data-stu-id="4ece0-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="4ece0-112">特定のインスタンスとの接続があるないため`setX`インスタンス変数にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="4ece0-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="4ece0-113">のみ動作する必要があります、`Shared`変数。</span><span class="sxs-lookup"><span data-stu-id="4ece0-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="4ece0-114">ときに`setX`その新しい値が、クラスのすべてのインスタンスで使用できる、共有変数の値を変更または設定します。</span><span class="sxs-lookup"><span data-stu-id="4ece0-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="4ece0-115">**エラー ID:** BC30369</span><span class="sxs-lookup"><span data-stu-id="4ece0-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ece0-116">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4ece0-116">To correct this error</span></span>  
  
1.  <span data-ttu-id="4ece0-117">クラスのすべてのインスタンス間で共有またはインスタンスごとに保持するメンバーにするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="4ece0-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2.  <span data-ttu-id="4ece0-118">すべてのインスタンス間で共有できるメンバーの 1 つのコピーを実行する場合に、追加、`Shared`メンバーの宣言するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="4ece0-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="4ece0-119">保持、`Shared`プロシージャ宣言でキーワード。</span><span class="sxs-lookup"><span data-stu-id="4ece0-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3.  <span data-ttu-id="4ece0-120">各インスタンスに、メンバーの個別コピーする場合を指定しない`Shared`メンバー宣言にします。</span><span class="sxs-lookup"><span data-stu-id="4ece0-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="4ece0-121">削除、`Shared`プロシージャ宣言からキーワード。</span><span class="sxs-lookup"><span data-stu-id="4ece0-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ece0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ece0-122">See Also</span></span>  
 [<span data-ttu-id="4ece0-123">Shared</span><span class="sxs-lookup"><span data-stu-id="4ece0-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
