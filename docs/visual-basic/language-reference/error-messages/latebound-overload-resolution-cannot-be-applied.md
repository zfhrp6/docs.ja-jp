---
title: "遅延バインディングされたオーバー ロードの解決には適用できません &#39;です。&lt;procedurename&gt;&#39;へのアクセスのインスタンスがインターフェイス型であるためです。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="2c29e-102">遅延バインディングされたオーバー ロードの解決には適用できません &#39;です。&lt;procedurename&gt;&#39;へのアクセスのインスタンスがインターフェイス型であるためです。</span><span class="sxs-lookup"><span data-stu-id="2c29e-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="2c29e-103">オーバー ロードされたプロパティまたはプロシージャへの参照を解決するのには、コンパイラがしようとしていますが、型の引数であるため、参照が失敗した`Object`と参照元のオブジェクトには、インターフェイスのデータ型。</span><span class="sxs-lookup"><span data-stu-id="2c29e-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="2c29e-104">`Object`引数は、遅延バインディングとして参照を解決するのには、コンパイラを強制します。</span><span class="sxs-lookup"><span data-stu-id="2c29e-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="2c29e-105">このような場合は、コンパイラは、基になるインターフェイスの代わりに、実装するクラスをオーバー ロードを解決します。</span><span class="sxs-lookup"><span data-stu-id="2c29e-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="2c29e-106">クラスのオーバー ロードされたバージョンのいずれかの名前を変更、コンパイラでは、名前が異なるため、オーバー ロードするには、そのバージョンは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="2c29e-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="2c29e-107">これで、コンパイラを無視する、名前を変更したバージョンの参照を解決するのには、適切な選択されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c29e-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="2c29e-108">**エラー ID:** BC30933</span><span class="sxs-lookup"><span data-stu-id="2c29e-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c29e-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2c29e-109">To correct this error</span></span>  
  
-   <span data-ttu-id="2c29e-110">使用して`CType`から引数をキャストする`Object`を呼び出したいオーバー ロードのシグネチャで指定された型にします。</span><span class="sxs-lookup"><span data-stu-id="2c29e-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="2c29e-111">注意を参照しているオブジェクトは基になるインターフェイスにキャストも効果はありません。</span><span class="sxs-lookup"><span data-stu-id="2c29e-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="2c29e-112">このエラーを回避する引数をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c29e-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c29e-113">例</span><span class="sxs-lookup"><span data-stu-id="2c29e-113">Example</span></span>  
 <span data-ttu-id="2c29e-114">次の例では、オーバー ロードされたへの呼び出し`Sub`コンパイル時にこのエラーが発生するプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="2c29e-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2c29e-115">コンパイラへの呼び出しを許可された場合、上記の例では`s1`が書き込まれると、解決が行わクラスを通じて`c1`インターフェイスではなく`i1`です。</span><span class="sxs-lookup"><span data-stu-id="2c29e-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="2c29e-116">つまり、コンパイラは見なしません`s2`名前が異なるため`c1`で定義されている適切な選択である場合でも、`i1`です。</span><span class="sxs-lookup"><span data-stu-id="2c29e-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="2c29e-117">次のコード行のいずれかへの呼び出しを変更することで、エラーを修正することができます。</span><span class="sxs-lookup"><span data-stu-id="2c29e-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="2c29e-118">前の行のコードに明示的にキャスト、`Object`変数`o1`オーバー ロードでは定義されているパラメーターの型のいずれかにします。</span><span class="sxs-lookup"><span data-stu-id="2c29e-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c29e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c29e-119">See Also</span></span>  
 [<span data-ttu-id="2c29e-120">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="2c29e-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="2c29e-121">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="2c29e-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [<span data-ttu-id="2c29e-122">CType 関数</span><span class="sxs-lookup"><span data-stu-id="2c29e-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
