---
title: "方法: 変数の可用性を制御する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="5a486-102">方法: 変数の可用性を制御する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a486-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="5a486-103">指定して、変数の可用性を制御するその*アクセス レベル*です。</span><span class="sxs-lookup"><span data-stu-id="5a486-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="5a486-104">アクセス レベルは、どのようなコードは、変数に対する読み取りまたは書き込みするアクセス許可を決定します。</span><span class="sxs-lookup"><span data-stu-id="5a486-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="5a486-105">*メンバー変数*(モジュール レベルと、プロシージャの外側で定義) 既定でパブリック アクセスは、すべてのコードを見ることがアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="5a486-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="5a486-106">アクセス修飾子を指定することによって、これを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="5a486-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="5a486-107">*ローカル変数*(プロシージャ内で定義) 名目上、プロシージャ内のコードだけがアクセスできますが、パブリック アクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="5a486-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="5a486-108">ローカル変数のアクセス レベルを変更することはできませんが、それを含むプロシージャのアクセス レベルを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="5a486-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="5a486-109">詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a486-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="5a486-110">プライベートとパブリックのアクセス</span><span class="sxs-lookup"><span data-stu-id="5a486-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="5a486-111">変数をモジュール、クラスまたは構造体内からのみアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="5a486-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="5a486-112">場所、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)プロシージャ外ではなく、モジュール、クラス、または構造体、内部変数。</span><span class="sxs-lookup"><span data-stu-id="5a486-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a486-113">含める、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a486-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a486-114">読み取りまたはからではなく、モジュール、クラス、または構造内で任意の場所から変数への書き込みが外側にします。</span><span class="sxs-lookup"><span data-stu-id="5a486-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="5a486-115">変数を参照できる任意のコードからアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="5a486-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="5a486-116">メンバー変数の場合は、配置、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。</span><span class="sxs-lookup"><span data-stu-id="5a486-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a486-117">含める、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a486-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a486-118">読み取りまたはアセンブリと相互運用する任意のコードから変数への書き込みことができます。</span><span class="sxs-lookup"><span data-stu-id="5a486-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="5a486-119">または</span><span class="sxs-lookup"><span data-stu-id="5a486-119">-or-</span></span>  
  
1.  <span data-ttu-id="5a486-120">ローカル変数では、配置、`Dim`変数、プロシージャ内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="5a486-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="5a486-121">含めないでください、`Public`キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a486-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a486-122">読み取りまたはからではなく、プロシージャ内で任意の場所から変数への書き込みが外側にします。</span><span class="sxs-lookup"><span data-stu-id="5a486-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="5a486-123">保護されているとフレンド アクセス</span><span class="sxs-lookup"><span data-stu-id="5a486-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="5a486-124">変数をクラスおよび派生クラス、またはそのアセンブリへのアクセス レベルを制限することができます。</span><span class="sxs-lookup"><span data-stu-id="5a486-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="5a486-125">同じアセンブリ内の他の場所または任意の派生クラスでは、コードからへのアクセスを許可するこれらの制限の和集合を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5a486-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="5a486-126">結合することでこの共用体を指定する、`Protected`と`Friend`同じ宣言内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="5a486-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="5a486-127">変数をそのクラスと派生クラス内からのみアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="5a486-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="5a486-128">場所、`Dim`変数、プロシージャの外側ですが、クラス内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="5a486-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a486-129">含める、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a486-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a486-130">読み取りまたはからではなく、そこから派生クラス内からだけでなく、クラス内で任意の場所から変数への書き込みができる派生チェーン内のクラス外です。</span><span class="sxs-lookup"><span data-stu-id="5a486-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="5a486-131">変数を同じアセンブリ内からのみアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="5a486-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="5a486-132">場所、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。</span><span class="sxs-lookup"><span data-stu-id="5a486-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a486-133">含める、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a486-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a486-134">読み取りまたは、モジュール、クラス、または構造内で任意の場所だけでなく、同じアセンブリ内からではなく、任意のコードからから変数への書き込みができるアセンブリの外側です。</span><span class="sxs-lookup"><span data-stu-id="5a486-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a486-135">例</span><span class="sxs-lookup"><span data-stu-id="5a486-135">Example</span></span>  
 <span data-ttu-id="5a486-136">次の例は、変数の宣言を示しています。 `Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`アクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="5a486-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="5a486-137">場合、`Dim`ステートメントがアクセス レベルを指定しますを含める必要はありません、`Dim`キーワード。</span><span class="sxs-lookup"><span data-stu-id="5a486-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="5a486-138">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5a486-138">.NET Framework Security</span></span>  
 <span data-ttu-id="5a486-139">制限の厳しいアクセス レベルで、変数、悪意のあるコードが不正にする可能性が小さいそれを使用します。</span><span class="sxs-lookup"><span data-stu-id="5a486-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a486-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a486-140">See Also</span></span>  
 [<span data-ttu-id="5a486-141">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="5a486-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="5a486-142">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="5a486-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="5a486-143">Public</span><span class="sxs-lookup"><span data-stu-id="5a486-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="5a486-144">Protected</span><span class="sxs-lookup"><span data-stu-id="5a486-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="5a486-145">Friend</span><span class="sxs-lookup"><span data-stu-id="5a486-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="5a486-146">Private</span><span class="sxs-lookup"><span data-stu-id="5a486-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
