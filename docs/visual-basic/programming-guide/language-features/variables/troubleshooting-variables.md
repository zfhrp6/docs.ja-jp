---
title: "Visual Basic における変数のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ccf7ee3b0205dcd85d82c06e1822c4d3f9296a1c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-variables-in-visual-basic"></a><span data-ttu-id="2bd69-102">Visual Basic における変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2bd69-102">Troubleshooting Variables in Visual Basic</span></span>
<span data-ttu-id="2bd69-103">このページの一覧で変数を使用するときに発生する一般的な問題について[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-103">This page lists some common problems that can occur when working with variables in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="unable-to-access-members-of-an-object"></a><span data-ttu-id="2bd69-104">オブジェクトのメンバーにアクセスできない</span><span class="sxs-lookup"><span data-stu-id="2bd69-104">Unable to Access Members of an Object</span></span>  
 <span data-ttu-id="2bd69-105">コードからオブジェクトのプロパティまたはメソッドにアクセスしようとしたときに、発生する可能性があるエラーは&2; つあります。</span><span class="sxs-lookup"><span data-stu-id="2bd69-105">If your code attempts to access a property or method on an object, there are two possible error outcomes:</span></span>  
  
-   <span data-ttu-id="2bd69-106">オブジェクト変数を特定の型として宣言した後、その型で定義されていないメンバーを参照すると、コンパイラによってエラー メッセージが生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2bd69-106">The compiler can generate an error message if you declare the object variable to be of a specific type and then refer to a member not defined by that type.</span></span>  
  
-   <span data-ttu-id="2bd69-107">実行時<xref:System.MemberAccessException>オブジェクト変数に割り当てられているオブジェクトがアクセスしようとして、コードのメンバーを公開していないときに発生します</xref:System.MemberAccessException>。</span><span class="sxs-lookup"><span data-stu-id="2bd69-107">A run-time <xref:System.MemberAccessException> occurs when the object assigned to an object variable does not expose the member your code is trying to access.</span></span> <span data-ttu-id="2bd69-108">変数の場合[Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)、メンバーがない場合に、この例外を取得することもできます`Public`します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-108">In the case of a variable of [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md), you can also get this exception if the member is not `Public`.</span></span> <span data-ttu-id="2bd69-109">この原因は、遅延バインディングで許可されているのは、 `Public` メンバーへのアクセスのみのためです。</span><span class="sxs-lookup"><span data-stu-id="2bd69-109">This is because late binding allows access only to `Public` members.</span></span>  
  
 <span data-ttu-id="2bd69-110">ときに、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)セットの型チェック`On`、オブジェクト変数が宣言するクラスのプロパティとメソッドのみにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2bd69-110">When the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets type checking `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="2bd69-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-111">The following example illustrates this.</span></span>  

 <span data-ttu-id="2bd69-112">[!code-vb[VbVbalrVariables&#2;](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2bd69-112">[!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]</span></span>  
  
 <span data-ttu-id="2bd69-113">この例では`p`のメンバーのみを使用して、<xref:System.Object>変数名は、クラス自体、`Left`プロパティ</xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="2bd69-113">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="2bd69-114">これに対して、`q`型として宣言された<xref:System.Windows.Forms.Label>、すべてのメソッドとプロパティを使用できるように、<xref:System.Windows.Forms.Label>クラス、<xref:System.Windows.Forms>名前空間</xref:System.Windows.Forms></xref:System.Windows.Forms.Label></xref:System.Windows.Forms.Label>。</span><span class="sxs-lookup"><span data-stu-id="2bd69-114">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
### <a name="correct-approach"></a><span data-ttu-id="2bd69-115">修正方法</span><span class="sxs-lookup"><span data-stu-id="2bd69-115">Correct Approach</span></span>  
 <span data-ttu-id="2bd69-116">特定のクラスのオブジェクトにあるすべてのメンバーにアクセスできるようにするには、オブジェクト変数をできる限りそのクラスの型で宣言します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-116">To be able to access all the members of an object of a particular class, declare the object variable to be of the type of that class when possible.</span></span> <span data-ttu-id="2bd69-117">設定する必要がある場合はコンパイル時に入力オブジェクトを把握していない場合の例については、これを行うことはできません、`Option Strict`に`Off`を指定して変数を宣言し、 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-117">If you cannot do this, for example if you do not know the object type at compile time, you must set `Option Strict` to `Off` and declare the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="2bd69-118">これにより任意の型のオブジェクトを変数に代入できます。また、現在変数に代入されているオブジェクトが受け入れ可能な型であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bd69-118">This allows objects of any type to be assigned to the variable, and you should take steps to ensure that the currently assigned object is of an acceptable type.</span></span> <span data-ttu-id="2bd69-119">使用することができます、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)この判断を行うためです。</span><span class="sxs-lookup"><span data-stu-id="2bd69-119">You can use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to make this determination.</span></span>  
  
## <a name="other-components-cannot-access-your-variable"></a><span data-ttu-id="2bd69-120">他のコンポーネントが変数にアクセスできない</span><span class="sxs-lookup"><span data-stu-id="2bd69-120">Other Components Cannot Access Your Variable</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2bd69-121">名前は*大文字*します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-121"> names are *case-insensitive*.</span></span> <span data-ttu-id="2bd69-122">2 つの名前の違いが英字の大文字と小文字の違いだけの場合、コンパイラでは&2; つを同じ名前と解釈します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-122">If two names differ in alphabetic case only, the compiler interprets them as the same name.</span></span> <span data-ttu-id="2bd69-123">たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="2bd69-123">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="2bd69-124">しかし、共通言語ランタイム (CLR) のバインディングでは *大文字と小文字が区別されます* 。</span><span class="sxs-lookup"><span data-stu-id="2bd69-124">However, the common language runtime (CLR) uses *case-sensitive* binding.</span></span> <span data-ttu-id="2bd69-125">このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。</span><span class="sxs-lookup"><span data-stu-id="2bd69-125">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="2bd69-126">たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bd69-126">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="2bd69-127">後でクラスを再コンパイルして要素の名前を `abc`に変更すると、このクラスを使用していた他のアセンブリがこの要素にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="2bd69-127">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class can no longer access that element.</span></span> <span data-ttu-id="2bd69-128">したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="2bd69-128">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
 <span data-ttu-id="2bd69-129">詳細については、次を参照してください。[共通言語ランタイム](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-129">For more information, see [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span></span>  
  
### <a name="correct-approach"></a><span data-ttu-id="2bd69-130">修正方法</span><span class="sxs-lookup"><span data-stu-id="2bd69-130">Correct Approach</span></span>  
 <span data-ttu-id="2bd69-131">他のコンポーネントから変数にアクセスできるようにするには、その変数の名前を、大文字と小文字が区別されるものとして扱います。</span><span class="sxs-lookup"><span data-stu-id="2bd69-131">To allow other components to access your variables, treat their names as if they were case-sensitive.</span></span> <span data-ttu-id="2bd69-132">作成したクラスまたはモジュールをテストするときには、他のアセンブリが適切な変数にバインドされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-132">When you are testing your class or module, make sure other assemblies are binding to the variables you expect them to.</span></span> <span data-ttu-id="2bd69-133">コンポーネントの公開後は、大文字と小文字の変更を含め、既存の変数名は変更しないようにします。</span><span class="sxs-lookup"><span data-stu-id="2bd69-133">Once you have published a component, do not make any modifications to existing variable names, including changing their cases.</span></span>  
  
## <a name="wrong-variable-being-used"></a><span data-ttu-id="2bd69-134">誤った変数が使用される</span><span class="sxs-lookup"><span data-stu-id="2bd69-134">Wrong Variable Being Used</span></span>  
 <span data-ttu-id="2bd69-135">同じ名前の&1; つ以上の変数がある場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラはその名前への参照を解決しようとしています。</span><span class="sxs-lookup"><span data-stu-id="2bd69-135">When you have more than one variable with the same name, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler attempts to resolve each reference to that name.</span></span> <span data-ttu-id="2bd69-136">変数のスコープが異なる場合、コンパイラは、参照を最も狭いスコープの宣言に解決します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-136">If the variables have different scope, the compiler resolves a reference to the declaration with the narrowest scope.</span></span> <span data-ttu-id="2bd69-137">変数のスコープが同じ場合、解決は失敗し、コンパイラはエラーを発行します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-137">If they have the same scope, the resolution fails and the compiler signals an error.</span></span> <span data-ttu-id="2bd69-138">詳細については、次を参照してください。[宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-138">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
### <a name="correct-approach"></a><span data-ttu-id="2bd69-139">修正方法</span><span class="sxs-lookup"><span data-stu-id="2bd69-139">Correct Approach</span></span>  
 <span data-ttu-id="2bd69-140">同じ名前でスコープが異なる変数を使わないようにします。</span><span class="sxs-lookup"><span data-stu-id="2bd69-140">Avoid using variables with the same name but different scope.</span></span> <span data-ttu-id="2bd69-141">他のアセンブリまたはプロジェクトを使用している場合は、その外部コンポーネントで定義された名前を使うことはできるだけ避けてください。</span><span class="sxs-lookup"><span data-stu-id="2bd69-141">If you are using other assemblies or projects, avoid using any names defined in those external components as much as possible.</span></span> <span data-ttu-id="2bd69-142">同じ名前の変数が複数ある場合は、変数への参照ごとに修飾子を付けるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2bd69-142">If you have more than one variable with the same name, be sure you qualify every reference to it.</span></span> <span data-ttu-id="2bd69-143">詳細については、次を参照してください。[宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。</span><span class="sxs-lookup"><span data-stu-id="2bd69-143">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd69-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bd69-144">See Also</span></span>  
 <span data-ttu-id="2bd69-145">[変数](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-145">[Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="2bd69-146"> [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-146"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="2bd69-147"> [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-147"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="2bd69-148"> [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-148"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="2bd69-149"> [方法: オブジェクトのメンバーにアクセス](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-149"> [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span></span>  
<span data-ttu-id="2bd69-150"> [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-150"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="2bd69-151"> [方法: オブジェクト変数が指す型を確認](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-151"> [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span></span>  
<span data-ttu-id="2bd69-152"> [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="2bd69-152"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="2bd69-153"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)</span><span class="sxs-lookup"><span data-stu-id="2bd69-153"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)</span></span>
