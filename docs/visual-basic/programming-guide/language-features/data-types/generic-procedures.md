---
title: Visual Basic におけるジェネリック プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 686087e4520ea5e6e69e5906c628af3ad54749da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649397"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="60f5d-102">Visual Basic におけるジェネリック プロシージャ</span><span class="sxs-lookup"><span data-stu-id="60f5d-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="60f5d-103">A*ジェネリック プロシージャ*もという、*ジェネリック メソッド*、少なくとも 1 つの型パラメーターで定義されているプロシージャは、します。</span><span class="sxs-lookup"><span data-stu-id="60f5d-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="60f5d-104">これにより、呼び出し元のコードをプロシージャが呼び出されるたびに、その要求をデータ型を調整できます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="60f5d-105">手順は、ジェネリック クラスまたはジェネリック構造体の内部で定義されていることだけでジェネリックではありません。</span><span class="sxs-lookup"><span data-stu-id="60f5d-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="60f5d-106">ジェネリックにするには、プロシージャはかかる場合があります、通常のパラメーターに加えて、少なくとも 1 つの型パラメーターを受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f5d-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="60f5d-107">ジェネリック クラスまたは構造体は、非ジェネリック プロシージャは、および非ジェネリックのクラス、構造体を含めることができます、またはモジュールには、ジェネリック プロシージャが含まれていることができます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="60f5d-108">ジェネリック プロシージャでは、戻り値の型、およびそのプロシージャのコードがある場合、通常のパラメーター リストにその型パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="60f5d-109">型推論</span><span class="sxs-lookup"><span data-stu-id="60f5d-109">Type Inference</span></span>  
 <span data-ttu-id="60f5d-110">すべての型引数を指定せず、ジェネリック プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="60f5d-111">この方法で呼び出すこと、コンパイラは、プロシージャの型引数を渡すための適切なデータ型を決定しようとします。</span><span class="sxs-lookup"><span data-stu-id="60f5d-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="60f5d-112">これと呼ばれる*型推論*です。</span><span class="sxs-lookup"><span data-stu-id="60f5d-112">This is called *type inference*.</span></span> <span data-ttu-id="60f5d-113">次のコードが呼び出しを示しているコンパイラが推論型を渡すかで`String`、型パラメーターに`t`です。</span><span class="sxs-lookup"><span data-stu-id="60f5d-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="60f5d-114">場合は、コンパイラは、呼び出しのコンテキストから型引数を推定できません、エラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="60f5d-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="60f5d-115">このようなエラーの考えられる原因の 1 つは、配列ランクの不一致です。</span><span class="sxs-lookup"><span data-stu-id="60f5d-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="60f5d-116">たとえば、型パラメーターの配列として、通常のパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="60f5d-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="60f5d-117">ジェネリック プロシージャを呼び出す場合は、異なるランク (次元の数) の配列を指定する、不一致が原因で型の推定が失敗します。</span><span class="sxs-lookup"><span data-stu-id="60f5d-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="60f5d-118">次のコードを 1 次元配列を受け取るプロシージャに渡される 2 次元配列にします。</span><span class="sxs-lookup"><span data-stu-id="60f5d-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 <span data-ttu-id="60f5d-119">型の推論は、すべての型引数を省略することによってのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="60f5d-120">1 つの型引数を指定する場合は、それらすべてを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f5d-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="60f5d-121">型の推定方法は、ジェネリック プロシージャにのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="60f5d-122">ジェネリック クラス、構造体、インターフェイス、またはデリゲートの型の推論を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="60f5d-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60f5d-123">例</span><span class="sxs-lookup"><span data-stu-id="60f5d-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="60f5d-124">説明</span><span class="sxs-lookup"><span data-stu-id="60f5d-124">Description</span></span>  
 <span data-ttu-id="60f5d-125">次の例では、汎用的な`Function`配列内の特定の要素を検索する手順。</span><span class="sxs-lookup"><span data-stu-id="60f5d-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="60f5d-126">1 つの型パラメーターを定義し、パラメーター リスト内の 2 つのパラメーターを構築するために使用します。</span><span class="sxs-lookup"><span data-stu-id="60f5d-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="60f5d-127">コード</span><span class="sxs-lookup"><span data-stu-id="60f5d-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="60f5d-128">コメント</span><span class="sxs-lookup"><span data-stu-id="60f5d-128">Comments</span></span>  
 <span data-ttu-id="60f5d-129">前の例を比較することが必要に`searchValue`の各要素に対して`searchArray`です。</span><span class="sxs-lookup"><span data-stu-id="60f5d-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="60f5d-130">この機能を保証するために、型パラメーター制約`T`を実装する、<xref:System.IComparable%601>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="60f5d-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="60f5d-131">コードを使用して、<xref:System.IComparable%601.CompareTo%2A>メソッドの代わりに、`=`演算子に渡される型引数の保証がないため`T`をサポートしている、`=`演算子。</span><span class="sxs-lookup"><span data-stu-id="60f5d-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="60f5d-132">テストすることができます、`findElement`次のコードを持つプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="60f5d-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="60f5d-133">呼び出す前に、 `MsgBox` 「0」、「1」、および「-1」をそれぞれ表示されます。</span><span class="sxs-lookup"><span data-stu-id="60f5d-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f5d-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="60f5d-134">See Also</span></span>  
 [<span data-ttu-id="60f5d-135">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="60f5d-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="60f5d-136">方法 : 複数のデータ型に同一の機能を提供できるクラスを定義する</span><span class="sxs-lookup"><span data-stu-id="60f5d-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="60f5d-137">方法 : ジェネリック クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="60f5d-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="60f5d-138">手順</span><span class="sxs-lookup"><span data-stu-id="60f5d-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="60f5d-139">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="60f5d-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="60f5d-140">型リスト</span><span class="sxs-lookup"><span data-stu-id="60f5d-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="60f5d-141">パラメーター リスト</span><span class="sxs-lookup"><span data-stu-id="60f5d-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
