---
title: "参照と Imports ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
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
ms.openlocfilehash: 4c6ce65005f84317c96a1124d609c46734d3cc66
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="7c38e-102">参照と Imports ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c38e-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="7c38e-103">利用できる外部のオブジェクトをプロジェクトを選択して、**参照の追加**コマンドを**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="7c38e-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="7c38e-104">参照[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アセンブリでは、タイプ ライブラリの詳細に説明のようなものを指すことができます。</span><span class="sxs-lookup"><span data-stu-id="7c38e-104">References in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="7c38e-105">Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="7c38e-105">The Imports Statement</span></span>  
 <span data-ttu-id="7c38e-106">アセンブリには、1 つ以上の名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c38e-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="7c38e-107">アセンブリへの参照を追加するときに追加することも、`Imports`ステートメント、モジュール内でそのアセンブリの名前空間の表示を制御するモジュールにします。</span><span class="sxs-lookup"><span data-stu-id="7c38e-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="7c38e-108">`Imports`ステートメントができるように一意の参照を指定するために必要な名前空間の部分のみを使用するスコープのコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="7c38e-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="7c38e-109">`Imports`ステートメントでは、次の構文。</span><span class="sxs-lookup"><span data-stu-id="7c38e-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="7c38e-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="7c38e-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="7c38e-111">`Aliasname`インポートされた名前空間を参照するコード内で使用できる短い名前を参照します。</span><span class="sxs-lookup"><span data-stu-id="7c38e-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="7c38e-112">`Namespace`いずれかで利用可能な名前空間、プロジェクト内の定義、または以前を通じて、プロジェクトの参照は、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7c38e-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="7c38e-113">モジュールは、任意の数を含めることがあります`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7c38e-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="7c38e-114">いずれかの後に現れる必要があります`Option`存在する場合、ステートメントが、その他のコードよりも前に、です。</span><span class="sxs-lookup"><span data-stu-id="7c38e-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c38e-115">プロジェクト参照とを混同しないでください、`Imports`ステートメント、または`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7c38e-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="7c38e-116">プロジェクト参照を指定するように、アセンブリ内のオブジェクトなど、外部のオブジェクトは使用できる[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="7c38e-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projects.</span></span> <span data-ttu-id="7c38e-117">`Imports`ステートメントは、プロジェクト参照へのアクセスを簡略化されますが、これらのオブジェクトへのアクセスを提供しません。</span><span class="sxs-lookup"><span data-stu-id="7c38e-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="7c38e-118">`Declare`ダイナミック リンク ライブラリ (DLL) で外部プロシージャへの参照を宣言するステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7c38e-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="7c38e-119">Imports ステートメントを使用してエイリアスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7c38e-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="7c38e-120">`Imports`ステートメントをやすくクラスのアクセス方法によって明示的に参照の完全修飾名を入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7c38e-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="7c38e-121">エイリアスを使用する名前空間の一部に過ぎませんをわかりやすい名前を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7c38e-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="7c38e-122">などの一部は、復帰/改行に複数の行に表示されるテキストの&1; つの原因となるシーケンス、<xref:Microsoft.VisualBasic.ControlChars>のモジュール、<xref:Microsoft.VisualBasic?displayProperty=fullName>名前空間</xref:Microsoft.VisualBasic?displayProperty=fullName></xref:Microsoft.VisualBasic.ControlChars>。</span><span class="sxs-lookup"><span data-stu-id="7c38e-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="7c38e-123">この定数を使用して、エイリアスを使わずにプログラムには、次のコードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c38e-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 <span data-ttu-id="7c38e-124">[!code-vb[VbVbalrApplication&#3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c38e-124">[!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="7c38e-125">`Imports`ステートメントはすぐに次のいずれかの最初の行に常にあります`Option`モジュール内のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7c38e-125">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="7c38e-126">次のコード フラグメントをインポートしてのエイリアスを割り当てる方法を示しています、<xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>モジュール:</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7c38e-126">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName> module:</span></span>  
  
 <span data-ttu-id="7c38e-127">[!code-vb[VbVbalrApplication&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c38e-127">[!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="7c38e-128">この名前空間への今後の参照が大幅に短くなります。</span><span class="sxs-lookup"><span data-stu-id="7c38e-128">Future references to this namespace can be considerably shorter:</span></span>  
  
 <span data-ttu-id="7c38e-129">[!code-vb[VbVbalrApplication&#5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c38e-129">[!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="7c38e-130">場合、`Imports`ステートメントにエイリアス名を含まない、インポートされた名前空間内で定義されている要素を修飾なしのモジュールで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7c38e-130">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="7c38e-131">エイリアス名が指定されている場合は、その名前空間内に含まれる名前の修飾子として使用するあります。</span><span class="sxs-lookup"><span data-stu-id="7c38e-131">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c38e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c38e-132">See Also</span></span>  
 <span data-ttu-id="7c38e-133"><xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="7c38e-133"><xref:Microsoft.VisualBasic.ControlChars></span></span>   
 <span data-ttu-id="7c38e-134"><xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic></span><span class="sxs-lookup"><span data-stu-id="7c38e-134"><xref:Microsoft.VisualBasic></span></span>   
<span data-ttu-id="7c38e-135"> [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="7c38e-135"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="7c38e-136"> [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="7c38e-136"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="7c38e-137"> [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="7c38e-137"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="7c38e-138"> [方法: を作成し、コマンドラインを使用してアセンブリを使用します。](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span><span class="sxs-lookup"><span data-stu-id="7c38e-138"> [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span></span>  
<span data-ttu-id="7c38e-139"> [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="7c38e-139"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>
