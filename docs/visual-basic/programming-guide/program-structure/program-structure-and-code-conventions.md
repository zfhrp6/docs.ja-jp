---
title: "プログラム構造とコード規則 (Visual Basic) |Microsoft ドキュメント"
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
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
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
ms.openlocfilehash: c3a091d64b3c55ad3f1291a635fd499da2dacdc8
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="b20fb-102">プログラム構造とコード規則 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b20fb-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="b20fb-103">ここでは、一般的な [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムの構造を紹介します。また、単純な [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラム "Hello World" を示し、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のコード規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-103">This section introduces the typical [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program structure, provides a simple [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code conventions.</span></span> <span data-ttu-id="b20fb-104">コード規則は、プログラムのロジックではなくプログラムの物理的な構造と外観に焦点を合わせた提案です。</span><span class="sxs-lookup"><span data-stu-id="b20fb-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="b20fb-105">コード規則に従うと、コードの読み取り、理解、保守が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="b20fb-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="b20fb-106">コード規則には、以下の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b20fb-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="b20fb-107">コードのラベル付けとコメント付けに関する標準化された書式</span><span class="sxs-lookup"><span data-stu-id="b20fb-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="b20fb-108">コードのスペーシング、書式指定、およびインデント設定に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="b20fb-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="b20fb-109">オブジェクト、変数、およびプロシージャの名前付け規則</span><span class="sxs-lookup"><span data-stu-id="b20fb-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="b20fb-110">以下のトピックでは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムの一連のプログラミング ガイドラインを適切な使用例と共に示します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b20fb-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b20fb-111">In This Section</span></span>  
 [<span data-ttu-id="b20fb-112">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="b20fb-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="b20fb-113">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムを構成する要素の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 [<span data-ttu-id="b20fb-114">Visual Basic の main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b20fb-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="b20fb-115">アプリケーションの開始点となり、アプリケーションの総合的な制御を行うプロシージャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="b20fb-116">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="b20fb-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="b20fb-117">他のアセンブリのオブジェクトを参照する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="b20fb-118">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="b20fb-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="b20fb-119">アセンブリ内のオブジェクトが名前空間でどのように編成されているのかを説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="b20fb-120">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="b20fb-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="b20fb-121">プロシージャ、定数、変数、引数、およびオブジェクトの名前付けに関する一般的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="b20fb-122">Visual Basic のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="b20fb-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="b20fb-123">このドキュメントのサンプルを開発するときに使用したガイドラインについてレビューします。</span><span class="sxs-lookup"><span data-stu-id="b20fb-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="b20fb-124">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="b20fb-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="b20fb-125">特定のコード ブロックを選択的にコンパイルし、その間は他のコード ブロックを無視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="b20fb-126">方法 : コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="b20fb-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="b20fb-127">長いステートメントを複数の行に分割する方法と、複数の短いステートメントを&1; 行に結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="b20fb-128">方法 : コードのセクションを折りたたんで非表示にする</span><span class="sxs-lookup"><span data-stu-id="b20fb-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="b20fb-129">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のコード エディターでコードをセクションごとに折りたたんで非表示にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="b20fb-130">方法 : ステートメントへのラベル付け</span><span class="sxs-lookup"><span data-stu-id="b20fb-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="b20fb-131">`On Error Goto` などのステートメントで使用するために、コード行に識別用のマーキングをする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="b20fb-132">コード内の特殊文字</span><span class="sxs-lookup"><span data-stu-id="b20fb-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="b20fb-133">英数字以外の文字を使用する方法と場所について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="b20fb-134">コード内のコメント</span><span class="sxs-lookup"><span data-stu-id="b20fb-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="b20fb-135">説明的なコメントをコードに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="b20fb-136">コード内の要素名としてのキーワード</span><span class="sxs-lookup"><span data-stu-id="b20fb-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="b20fb-137">角かっこ (`[]`) を使用して [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] キーワードにもなる変数名を区切る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="b20fb-138">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="b20fb-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="b20fb-139">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムの要素を参照するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 [<span data-ttu-id="b20fb-140">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="b20fb-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="b20fb-141">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の既知のコーディングの制限の解除について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b20fb-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="b20fb-142">Related Sections</span></span>  
 [<span data-ttu-id="b20fb-143">表記規則とコード規則</span><span class="sxs-lookup"><span data-stu-id="b20fb-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="b20fb-144">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の標準的なコーディング規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-144">Provides standard coding conventions for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="b20fb-145">コードの作成</span><span class="sxs-lookup"><span data-stu-id="b20fb-145">Writing Code</span></span>](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="b20fb-146">コードの記述と管理を容易にする機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="b20fb-146">Describes features that make it easier for you to write and manage your code.</span></span>
