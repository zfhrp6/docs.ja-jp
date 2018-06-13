---
title: '方法: ジェネリック クラスを使用する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: adea9f7e7dbbc2317e5b857a5153e3ec67d63344
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647918"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="cba34-102">方法: ジェネリック クラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cba34-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="cba34-103">*型パラメーター* を受け取るクラスは、 *ジェネリック クラス*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cba34-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="cba34-104">ジェネリック クラスを使用している場合は、このパラメーターのそれぞれに *型引数* を入力することで、ジェネリック クラスから *構築済みクラス* を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="cba34-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="cba34-105">これで、構築済みクラス型の変数を宣言し、構築済みクラスのインスタンスを作成して、その変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cba34-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="cba34-106">クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cba34-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="cba34-107">次のプロシージャは、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] で定義されたジェネリック クラスを受け取り、そこからインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cba34-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="cba34-108">型パラメーターを受け取るクラスを使用するには</span><span class="sxs-lookup"><span data-stu-id="cba34-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="cba34-109">ソース ファイルの先頭には、含める、 [Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)をインポートする、<xref:System.Collections.Generic?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="cba34-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="cba34-110">これにより、<xref:System.Collections.Queue?displayProperty=nameWithType> などの他のキュー クラスと区別するために完全修飾しなくても <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> クラスを参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cba34-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="cba34-111">通常の方法でオブジェクトを作成し、クラス名の直後に `(Of` `type``)` を追加します。</span><span class="sxs-lookup"><span data-stu-id="cba34-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="cba34-112">次の例では、同じクラス (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) を使用して、異なるデータ型の項目を保持する 2 つのキュー オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="cba34-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="cba34-113">項目は各キューの末尾に追加された後に削除され、各キューの先頭から項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cba34-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cba34-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="cba34-114">See Also</span></span>  
 [<span data-ttu-id="cba34-115">データの種類</span><span class="sxs-lookup"><span data-stu-id="cba34-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="cba34-116">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="cba34-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="cba34-117">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cba34-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="cba34-118">Of</span><span class="sxs-lookup"><span data-stu-id="cba34-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="cba34-119">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="cba34-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="cba34-120">方法 : 複数のデータ型に同一の機能を提供できるクラスを定義する</span><span class="sxs-lookup"><span data-stu-id="cba34-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="cba34-121">反復子</span><span class="sxs-lookup"><span data-stu-id="cba34-121">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
