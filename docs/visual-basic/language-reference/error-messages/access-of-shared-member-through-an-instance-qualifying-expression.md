---
title: "インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords: BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="73e08-102">インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="73e08-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="73e08-103">クラスまたは構造体のインスタンス変数の使用にアクセスする、`Shared`変数、プロパティ、プロシージャ、またはそのクラスまたは構造体で定義されたイベント。</span><span class="sxs-lookup"><span data-stu-id="73e08-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="73e08-104">この警告は、クラスまたは定数または列挙型、または入れ子になったクラスまたは構造体などの構造体の暗黙的な共有メンバーにアクセスするインスタンス変数を使用する場合にも発生することができます。</span><span class="sxs-lookup"><span data-stu-id="73e08-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="73e08-105">メンバーの共有の目的は、そのメンバーの 1 つのコピーだけを作成し、その 1 つのコピーをクラスまたは構造体が宣言されているのすべてのインスタンスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="73e08-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="73e08-106">アクセスするには、この目的で一貫性が、`Shared`メンバーがそのクラスまたは構造体の個々 のインスタンスを保持する変数ではなく、そのクラスまたは構造の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="73e08-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="73e08-107">アクセス、`Shared`メンバー インスタンス変数を使用できますが、コード メンバーであるという事実を隠すことがわかりにくくなる`Shared`です。</span><span class="sxs-lookup"><span data-stu-id="73e08-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="73e08-108">さらに、このようなアクセスが、式の一部である場合などに、他の操作を実行するには`Function`共有のメンバーのインスタンスを返すプロシージャ[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]式と本来は実行されているその他の操作をバイパスします。</span><span class="sxs-lookup"><span data-stu-id="73e08-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="73e08-109">例および詳細については、次を参照してください。 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)です。</span><span class="sxs-lookup"><span data-stu-id="73e08-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="73e08-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="73e08-110">By default, this message is a warning.</span></span> <span data-ttu-id="73e08-111">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="73e08-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="73e08-112">**エラー ID:** BC42025</span><span class="sxs-lookup"><span data-stu-id="73e08-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73e08-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="73e08-113">To correct this error</span></span>  
  
-   <span data-ttu-id="73e08-114">クラスまたは定義する構造体の名前を使用して、`Shared`に次の例で示すように、アクセスするメンバー。</span><span class="sxs-lookup"><span data-stu-id="73e08-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="73e08-115">スコープの効果のアラートは、2 つのプログラミング要素が同じ名前を付けるとき。</span><span class="sxs-lookup"><span data-stu-id="73e08-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="73e08-116">使用してインスタンスを宣言する場合、前の例で`Dim testClass as testClass = Nothing`、コンパイラはへの呼び出しを処理`testClass.sayHello()`クラス名、および警告なしでメソッドのアクセスが発生するとします。</span><span class="sxs-lookup"><span data-stu-id="73e08-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e08-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="73e08-117">See Also</span></span>  
 [<span data-ttu-id="73e08-118">Shared</span><span class="sxs-lookup"><span data-stu-id="73e08-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="73e08-119">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="73e08-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
