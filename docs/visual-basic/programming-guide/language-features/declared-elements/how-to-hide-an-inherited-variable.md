---
title: '方法: 継承された変数を隠す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: c59fdd8c6c6d2444b8d687c78c61f4e0d4bf9a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="28b3c-102">方法: 継承された変数を隠す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28b3c-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="28b3c-103">派生クラスでは、その基本クラスのすべての定義を継承します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="28b3c-104">基本クラスの要素として同じ名前を使用して変数を定義する場合は、非表示にできます、または*シャドウ*、派生クラスで変数を定義するときにその基本クラスの要素。</span><span class="sxs-lookup"><span data-stu-id="28b3c-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="28b3c-105">これを行うと、派生クラス内のコードにアクセスする場合、変数シャドウ機構が明示的にバイパスされる場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="28b3c-106">継承された変数を非表示にすることができます別の理由は、基本クラスのリビジョンから保護するためです。</span><span class="sxs-lookup"><span data-stu-id="28b3c-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="28b3c-107">基本クラスには、継承している要素を変更する変更を行うこともします。</span><span class="sxs-lookup"><span data-stu-id="28b3c-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="28b3c-108">この場合、`Shadows`修飾子は、基底クラス要素の代わりに、変数を解決する派生クラスからの参照。</span><span class="sxs-lookup"><span data-stu-id="28b3c-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="28b3c-109">継承された変数を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="28b3c-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="28b3c-110">(プロシージャ) の外側のクラス レベルで非表示にする、変数が宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="28b3c-111">それ以外の場合、非表示にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="28b3c-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="28b3c-112">クラス内で、派生書き込み、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="28b3c-113">継承された変数のと同じ名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="28b3c-114">含める、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣言でキーワード。</span><span class="sxs-lookup"><span data-stu-id="28b3c-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="28b3c-115">派生クラス内のコードは、変数名が参照されているとき、コンパイラは、変数への参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="28b3c-116">次の例では、継承された変数のシャドウを示します。</span><span class="sxs-lookup"><span data-stu-id="28b3c-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="28b3c-117">前の例は、変数を宣言`shadowString`基底クラスと派生クラスでシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="28b3c-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="28b3c-118">プロシージャ`showStrings`シャドウのバージョンの文字列が表示されます、派生クラスでときに名前`shadowString`が修飾されていません。</span><span class="sxs-lookup"><span data-stu-id="28b3c-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="28b3c-119">影付きのバージョンを次に、表示と`shadowString`で修飾されて、`MyBase`キーワード。</span><span class="sxs-lookup"><span data-stu-id="28b3c-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="28b3c-120">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="28b3c-120">Robust Programming</span></span>  
 <span data-ttu-id="28b3c-121">シャドウ処理には、1 つ以上のバージョンの同じ名前の変数が導入されています。</span><span class="sxs-lookup"><span data-stu-id="28b3c-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="28b3c-122">コードのステートメントは、変数名が参照されているときに、コンパイラが参照を解決するバージョンは、コードのステートメントの場所が存在している修飾文字列のなどの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="28b3c-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="28b3c-123">これにより、意図しないシャドウされた変数のバージョンを参照するリスクが増加することができます。</span><span class="sxs-lookup"><span data-stu-id="28b3c-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="28b3c-124">シャドウされた変数へのすべての参照を完全に修飾することによってそのリスクを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="28b3c-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b3c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="28b3c-125">See Also</span></span>  
 [<span data-ttu-id="28b3c-126">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="28b3c-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="28b3c-127">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="28b3c-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="28b3c-128">シャドウとオーバーライドの違い</span><span class="sxs-lookup"><span data-stu-id="28b3c-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="28b3c-129">方法: 自分で宣言した変数と同じ名前の変数を隠す</span><span class="sxs-lookup"><span data-stu-id="28b3c-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="28b3c-130">方法: 派生クラスによって非表示になっている変数にアクセスする</span><span class="sxs-lookup"><span data-stu-id="28b3c-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="28b3c-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="28b3c-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="28b3c-132">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="28b3c-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="28b3c-133">継承の基本</span><span class="sxs-lookup"><span data-stu-id="28b3c-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
