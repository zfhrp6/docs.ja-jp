---
title: Visual Basic 言語の機能
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, elements of
- Visual Basic code
ms.assetid: b0b21730-298c-47e6-9a2f-cc81f628067b
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7074206baa51259592cca3fdc224d99438791f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="visual-basic-language-features"></a><span data-ttu-id="f1b6e-102">Visual Basic 言語の機能</span><span class="sxs-lookup"><span data-stu-id="f1b6e-102">Visual Basic Language Features</span></span>
<span data-ttu-id="f1b6e-103">次のトピックでは、オブジェクト指向プログラミング言語である [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] の必須コンポーネントを紹介して説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-103">The following topics introduce and discuss the essential components of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], an object-oriented programming language.</span></span> <span data-ttu-id="f1b6e-104">フォームとコントロールを使用してアプリケーションのユーザー インターフェイスを作成した後、アプリケーションの動作を定義するコードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-104">After creating the user interface for your application using forms and controls, you need to write the code that defines the application's behavior.</span></span> <span data-ttu-id="f1b6e-105">他の最新のプログラミング言語と同じように、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] は、多数の一般的なプログラミング構成要素と言語要素をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-105">As with any modern programming language, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supports a number of common programming constructs and language elements.</span></span>  
  
 <span data-ttu-id="f1b6e-106">他の言語でプログラミングしたことがある場合、このセクションで説明されている内容の大半はすでに知っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-106">If you have programmed in other languages, much of the material covered in this section might seem familiar.</span></span> <span data-ttu-id="f1b6e-107">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] の構造体の大部分は他の言語の構造体と似ていますが、イベント ドリブン型という性質のため、いくつかの微妙な違いが発生しています。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-107">While most of the constructs are similar to those in other languages, the event-driven nature of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] introduces some subtle differences.</span></span>  
  
 <span data-ttu-id="f1b6e-108">プログラミングの経験がない場合、このセクションの説明は、コードを記述するための基礎を紹介するものになります。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-108">If you are new to programming, the material in this section serves as an introduction to the basic building blocks for writing code.</span></span> <span data-ttu-id="f1b6e-109">基礎を理解したら、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] を使用して強力なアプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-109">Once you understand the basics, you can create powerful applications using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1b6e-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f1b6e-110">In This Section</span></span>  
 [<span data-ttu-id="f1b6e-111">配列</span><span class="sxs-lookup"><span data-stu-id="f1b6e-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 <span data-ttu-id="f1b6e-112">複数の関連する値を格納する配列を宣言して使用することで、コードをよりコンパクトで強力にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-112">Discusses making your code more compact and powerful by declaring and using arrays, which hold multiple related values.</span></span>  
  
 [<span data-ttu-id="f1b6e-113">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="f1b6e-113">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 <span data-ttu-id="f1b6e-114">コレクションを作成して初期値を設定できるコレクション初期化子について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-114">Describes collection initializers, which enable you to create a collection and populate it with an initial set of values.</span></span>  
  
 [<span data-ttu-id="f1b6e-115">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="f1b6e-115">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 <span data-ttu-id="f1b6e-116">繰り返し使用する不変の値の格納について、関連する定数値のセットを含めて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-116">Discusses storing unchanging values for repeated use, including sets of related constant values.</span></span>  
  
 [<span data-ttu-id="f1b6e-117">制御フロー</span><span class="sxs-lookup"><span data-stu-id="f1b6e-117">Control Flow</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 <span data-ttu-id="f1b6e-118">プログラムの実行フローを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-118">Shows how to regulate the flow of your program's execution.</span></span>  
  
 [<span data-ttu-id="f1b6e-119">データの種類</span><span class="sxs-lookup"><span data-stu-id="f1b6e-119">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="f1b6e-120">プログラミング要素が保持できるデータの種類とそのデータの格納方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-120">Describes what kinds of data a programming element can hold and how that data is stored.</span></span>  
  
 [<span data-ttu-id="f1b6e-121">宣言された要素</span><span class="sxs-lookup"><span data-stu-id="f1b6e-121">Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 <span data-ttu-id="f1b6e-122">宣言可能なプログラミング要素、各要素の名前と特徴、およびコンパイラがプログラミング要素への参照を解決する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-122">Covers programming elements you can declare, their names and characteristics, and how the compiler resolves references to them.</span></span>  
  
 [<span data-ttu-id="f1b6e-123">デリゲート</span><span class="sxs-lookup"><span data-stu-id="f1b6e-123">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="f1b6e-124">デリゲートの概要と Visual Basic での使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-124">Provides an introduction to delegates and how they are used in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f1b6e-125">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="f1b6e-125">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 <span data-ttu-id="f1b6e-126">オブジェクトがオブジェクト変数に代入されるときにコンパイラによって実行されるバインディングと、事前バインディング オブジェクトと遅延バインディング オブジェクトの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-126">Describes binding, which is performed by the compiler when an object is assigned to an object variable, and the differences between early-bound and late-bound objects.</span></span>  
  
 [<span data-ttu-id="f1b6e-127">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="f1b6e-127">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 <span data-ttu-id="f1b6e-128">構文エラー、ランタイム エラー、および論理エラーの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-128">Provides an overview of syntax errors, run-time errors, and logic errors.</span></span>  
  
 [<span data-ttu-id="f1b6e-129">イベント</span><span class="sxs-lookup"><span data-stu-id="f1b6e-129">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 <span data-ttu-id="f1b6e-130">イベントの宣言方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-130">Shows how to declare and use events.</span></span>  
  
 [<span data-ttu-id="f1b6e-131">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b6e-131">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 <span data-ttu-id="f1b6e-132">インターフェイスの概要と、アプリケーションでの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-132">Describes what interfaces are and how you can use them in your applications.</span></span>  
  
 [<span data-ttu-id="f1b6e-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="f1b6e-133">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="f1b6e-134">[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] の機能とプログラミングの概要を説明するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-134">Provides links to topics that introduce [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] features and programming.</span></span>  
  
 [<span data-ttu-id="f1b6e-135">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="f1b6e-135">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 <span data-ttu-id="f1b6e-136">オブジェクトとクラスの概要、使用方法、相互関係、オブジェクトとクラスによって公開されるプロパティ、メソッド、イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-136">Provides an overview of objects and classes, how they are used, their relationships to each other, and the properties, methods, and events they expose.</span></span>  
  
 [<span data-ttu-id="f1b6e-137">演算子および式</span><span class="sxs-lookup"><span data-stu-id="f1b6e-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 <span data-ttu-id="f1b6e-138">値を保持する要素を操作するコード要素、それらを効率的に使用する方法、およびそれらを組み合わせて新しい値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-138">Describes the code elements that manipulate value-holding elements, how to use them efficiently, and how to combine them to yield new values.</span></span>  
  
 [<span data-ttu-id="f1b6e-139">手順</span><span class="sxs-lookup"><span data-stu-id="f1b6e-139">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 <span data-ttu-id="f1b6e-140">`Sub`、`Function`、`Property`、`Operator` の各プロシージャと、再帰プロシージャやオーバーロード プロシージャなどの高度なトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-140">Describes `Sub`, `Function`, `Property`, and `Operator` procedures, as well as advanced topics such as recursive and overloaded procedures.</span></span>  
  
 [<span data-ttu-id="f1b6e-141">ステートメント</span><span class="sxs-lookup"><span data-stu-id="f1b6e-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 <span data-ttu-id="f1b6e-142">宣言ステートメントと実行可能ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-142">Describes declaration and executable statements.</span></span>  
  
 [<span data-ttu-id="f1b6e-143">文字列</span><span class="sxs-lookup"><span data-stu-id="f1b6e-143">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 <span data-ttu-id="f1b6e-144">Visual Basic での文字列の使用に関する基本的な概念について説明しているトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-144">Provides links to topics that describe the basic concepts about using strings in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f1b6e-145">変数</span><span class="sxs-lookup"><span data-stu-id="f1b6e-145">Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/index.md)  
 <span data-ttu-id="f1b6e-146">変数の概要と Visual Basic でのその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-146">Introduces variables and describes how to use them in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f1b6e-147">XML</span><span class="sxs-lookup"><span data-stu-id="f1b6e-147">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="f1b6e-148">Visual Basic での XML の使用方法について説明しているトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-148">Provides links to topics that describe how to use XML in Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f1b6e-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1b6e-149">Related Sections</span></span>  
 [<span data-ttu-id="f1b6e-150">コレクション</span><span class="sxs-lookup"><span data-stu-id="f1b6e-150">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 <span data-ttu-id="f1b6e-151">.NET Framework で提供されているコレクションの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-151">Describes some of the types of collections that are provided by the .NET Framework.</span></span> <span data-ttu-id="f1b6e-152">単純なコレクションおよびキーと値のペアのコレクションを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-152">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>  
  
 [<span data-ttu-id="f1b6e-153">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="f1b6e-153">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 <span data-ttu-id="f1b6e-154">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] でのプログラミングのさまざまな側面に関するリファレンス情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f1b6e-154">Provides reference information on various aspects of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming.</span></span>
