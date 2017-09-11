---
title: "方法: ジェネリック クラス (Visual Basic) を使用して |Microsoft ドキュメント"
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
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters, data type
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
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
ms.openlocfilehash: d6f5f941887dfc1f93221be1c184f0dcc2789352
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="c224f-102">方法: ジェネリック クラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c224f-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="c224f-103">*型パラメーター* を受け取るクラスは、 *ジェネリック クラス*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c224f-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="c224f-104">ジェネリック クラスを使用している場合は、このパラメーターのそれぞれに *型引数* を入力することで、ジェネリック クラスから *構築済みクラス* を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="c224f-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="c224f-105">これで、構築済みクラス型の変数を宣言し、構築済みクラスのインスタンスを作成して、その変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c224f-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="c224f-106">クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c224f-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="c224f-107">次のプロシージャは、 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] で定義されたジェネリック クラスを受け取り、そこからインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c224f-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="c224f-108">型パラメーターを受け取るクラスを使用するには</span><span class="sxs-lookup"><span data-stu-id="c224f-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="c224f-109">ソース ファイルの先頭に含める、 [Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)をインポートする、<xref:System.Collections.Generic?displayProperty=fullName>名前空間</xref:System.Collections.Generic?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="c224f-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="c224f-110">これにより、 <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> <xref:System.Collections.Queue?displayProperty=fullName>。</xref:System.Collections.Queue?displayProperty=fullName>などその他のキューのクラスから区別するために、完全修飾しなくてもクラス</xref:System.Collections.Generic.Queue%601?displayProperty=fullName>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c224f-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=fullName>.</span></span>  
  
2.  <span data-ttu-id="c224f-111">通常の方法でオブジェクトを作成し、クラス名の直後に `(Of` `type``)` を追加します。</span><span class="sxs-lookup"><span data-stu-id="c224f-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="c224f-112">次のコードの例では、同じクラス (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) 異なるデータ型の項目を保持する&2; つのキュー オブジェクトを作成します</xref:System.Collections.Generic.Queue%601?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="c224f-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="c224f-113">項目は各キューの末尾に追加された後に削除され、各キューの先頭から項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c224f-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     <span data-ttu-id="c224f-114">[!code-vb[VbVbalrDataTypes&#9;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c224f-114">[!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c224f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c224f-115">See Also</span></span>  
 <span data-ttu-id="c224f-116">[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="c224f-116">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="c224f-117"> [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="c224f-117"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="c224f-118"> [言語への非依存性、および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3) </span><span class="sxs-lookup"><span data-stu-id="c224f-118"> [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) </span></span>  
<span data-ttu-id="c224f-119"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c224f-119"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="c224f-120"> [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="c224f-120"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="c224f-121"> [方法: 複数のデータ型に同一の機能を提供できるクラスを定義する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="c224f-121"> [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md) </span></span>  
<span data-ttu-id="c224f-122"> [反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span><span class="sxs-lookup"><span data-stu-id="c224f-122"> [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span></span>
