---
title: "インスタンスを通じて共有メンバーへのアクセス正規の式は評価されません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
dev_langs:
- VB
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 49dc785131e257b19d0d1d57627ccb6cf8a3c63e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="583d3-102">インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="583d3-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="583d3-103">クラスまたは構造体のインスタンス変数の使用にアクセスする、`Shared`変数、プロパティ、プロシージャ、またはそのクラスまたは構造体で定義されたイベント。</span><span class="sxs-lookup"><span data-stu-id="583d3-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="583d3-104">この警告は、インスタンス変数を使用して、クラスまたは構造体、定数または列挙型、または入れ子になったクラスや構造体などの暗黙的な共有メンバーにアクセスする場合にも発生することができます。</span><span class="sxs-lookup"><span data-stu-id="583d3-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="583d3-105">メンバーの共有の目的は、そのメンバーの&1; つのコピーのみを作成し、その&1; つのコピーのクラスまたは構造体の宣言されているすべてのインスタンスを使用できるようにです。</span><span class="sxs-lookup"><span data-stu-id="583d3-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="583d3-106">アクセスするには、この目的で一貫性が、`Shared`メンバーがそのクラスまたは構造体の個々 のインスタンスを保持する変数ではなく、クラスまたは構造の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="583d3-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="583d3-107">アクセス、`Shared`インスタンス変数を使用してメンバー コードも容易に、メンバーであるという事実を隠すことで理解しづらい`Shared`します。</span><span class="sxs-lookup"><span data-stu-id="583d3-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="583d3-108">さらに、このようなアクセスが式の一部である場合などに、他のアクションを実行するには`Function`共有メンバーのインスタンスを返すプロシージャ[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]式とそれ以外の場合、その他の操作をバイパスします。</span><span class="sxs-lookup"><span data-stu-id="583d3-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="583d3-109">詳細と例では、次を参照してください。 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)します。</span><span class="sxs-lookup"><span data-stu-id="583d3-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="583d3-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="583d3-110">By default, this message is a warning.</span></span> <span data-ttu-id="583d3-111">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="583d3-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="583d3-112">**エラー ID:** BC42025</span><span class="sxs-lookup"><span data-stu-id="583d3-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="583d3-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="583d3-113">To correct this error</span></span>  
  
-   <span data-ttu-id="583d3-114">クラスまたは定義する構造体の名前を使用して、`Shared`メンバーへのアクセスに、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="583d3-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="583d3-115">スコープの影響に関する警告は、2 つのプログラミング要素は、同じ名前を付けるときにあります。</span><span class="sxs-lookup"><span data-stu-id="583d3-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="583d3-116">使用してインスタンスを宣言する場合、前の例で`Dim testClass as testClass = Nothing`、コンパイラは、処理の呼び出し`testClass.sayHello()`クラス名、および警告は表示されず、メソッドのアクセスが発生するとします。</span><span class="sxs-lookup"><span data-stu-id="583d3-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583d3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="583d3-117">See Also</span></span>  
 <span data-ttu-id="583d3-118">[共有](../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="583d3-118">[Shared](../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="583d3-119"> [Visual Basic におけるスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span><span class="sxs-lookup"><span data-stu-id="583d3-119"> [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span></span>
