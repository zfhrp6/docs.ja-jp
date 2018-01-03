---
title: "参照と Imports ステートメント (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c62eae57ae127fcbb860fe72853604802cccd9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="4af48-102">参照と Imports ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4af48-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="4af48-103">利用できる外部オブジェクトをプロジェクトを選択して、**参照の追加**コマンドを**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="4af48-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="4af48-104">参照[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]タイプ ライブラリが含まれていますが、詳細についてにと似ていますが、アセンブリを指すことができます。</span><span class="sxs-lookup"><span data-stu-id="4af48-104">References in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="4af48-105">Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="4af48-105">The Imports Statement</span></span>  
 <span data-ttu-id="4af48-106">アセンブリには、1 つまたは複数の名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4af48-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="4af48-107">アセンブリへの参照を追加するときに追加することも、`Imports`ステートメント、モジュール内でそのアセンブリの名前空間の表示を制御するモジュールにします。</span><span class="sxs-lookup"><span data-stu-id="4af48-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="4af48-108">`Imports`ステートメントは、一意の参照を指定するために必要な名前空間の部分のみを使用できるスコープのコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="4af48-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="4af48-109">`Imports`ステートメントでは、次の構文。</span><span class="sxs-lookup"><span data-stu-id="4af48-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="4af48-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="4af48-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="4af48-111">`Aliasname`インポート済み名前空間を参照するコード内で使用できる短い名前を指します。</span><span class="sxs-lookup"><span data-stu-id="4af48-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="4af48-112">`Namespace`名前空間のいずれかで使用可能なプロジェクト参照をプロジェクト内で定義、または以前を通じて`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4af48-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="4af48-113">モジュールは、任意の数を含めることがあります`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4af48-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="4af48-114">いずれかの後に出現する必要があります`Option`ステートメント、存在する場合、その他のコードの前にします。</span><span class="sxs-lookup"><span data-stu-id="4af48-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4af48-115">プロジェクト参照とを混同しないでください、`Imports`ステートメントまたは`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4af48-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="4af48-116">プロジェクトの参照、アセンブリ内のオブジェクトなど、外部のオブジェクトを利用[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="4af48-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projects.</span></span> <span data-ttu-id="4af48-117">`Imports`ステートメントは、プロジェクト参照へのアクセスを簡素化されますが、これらのオブジェクトへのアクセスを提供しません。</span><span class="sxs-lookup"><span data-stu-id="4af48-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="4af48-118">`Declare`ダイナミック リンク ライブラリ (DLL) で外部プロシージャへの参照を宣言するステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4af48-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="4af48-119">Imports ステートメントを使用してエイリアスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4af48-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="4af48-120">`Imports`ステートメント簡単にクラスのアクセス方法によって明示的に参照の完全修飾名を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4af48-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="4af48-121">エイリアスを使用する名前空間の 1 つの部分に付けるわかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4af48-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="4af48-122">たとえばの一部は、復帰/改行シーケンスに複数の行に表示されるテキストの 1 つの原因となる、<xref:Microsoft.VisualBasic.ControlChars>内のモジュール、<xref:Microsoft.VisualBasic?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="4af48-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4af48-123">この定数を使用して、エイリアスがなければプログラムに、次のコードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4af48-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="4af48-124">`Imports`ステートメントはすぐに次のいずれかの最初の行を常にある`Option`モジュール内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="4af48-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="4af48-125">次のコード フラグメントをインポートし、エイリアスを割り当てる方法を示しています、<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>モジュール。</span><span class="sxs-lookup"><span data-stu-id="4af48-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="4af48-126">この名前空間への今後の参照が大幅に短くなります。</span><span class="sxs-lookup"><span data-stu-id="4af48-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="4af48-127">場合、`Imports`ステートメントは、エイリアス名を指定していない、インポートされた名前空間内で定義されている要素を修飾なしのモジュールで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4af48-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="4af48-128">エイリアス名が指定されている場合その名前空間内に含まれる名前の修飾子として使用するあります。</span><span class="sxs-lookup"><span data-stu-id="4af48-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af48-129">参照</span><span class="sxs-lookup"><span data-stu-id="4af48-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [<span data-ttu-id="4af48-130">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="4af48-130">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="4af48-131">アセンブリとグローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="4af48-131">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="4af48-132">方法: コマンド ラインを使用してアセンブリを作成および使用する</span><span class="sxs-lookup"><span data-stu-id="4af48-132">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="4af48-133">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="4af48-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
