---
title: 構造体およびその他のプログラミング要素 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 7b375c5a45998fc0bd06f7c075f23a30dd377295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652026"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="ebf01-102">構造体およびその他のプログラミング要素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebf01-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="ebf01-103">構造体は、配列、オブジェクト、およびプロシージャ、相互に組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="ebf01-104">これらの要素が個別に使用すると、相互作用は同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf01-105">構造体の宣言で構造体の要素を初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="ebf01-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="ebf01-106">構造体型として宣言された変数の要素にのみ値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="ebf01-107">構造体と配列</span><span class="sxs-lookup"><span data-stu-id="ebf01-107">Structures and Arrays</span></span>  
 <span data-ttu-id="ebf01-108">構造体には、1 つまたは複数の要素として配列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="ebf01-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="ebf01-110">構造体の配列の値はオブジェクトのプロパティにアクセスする同じ方法でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ebf01-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="ebf01-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="ebf01-112">構造体の配列を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-112">You can also declare an array of structures.</span></span> <span data-ttu-id="ebf01-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="ebf01-114">このデータのアーキテクチャのコンポーネントにアクセスする同じ規則に従うします。</span><span class="sxs-lookup"><span data-stu-id="ebf01-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="ebf01-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="ebf01-116">構造とオブジェクト</span><span class="sxs-lookup"><span data-stu-id="ebf01-116">Structures and Objects</span></span>  
 <span data-ttu-id="ebf01-117">構造体には、1 つまたは複数の要素としてオブジェクトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="ebf01-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="ebf01-119">このような宣言で特定のオブジェクト クラスを使用する必要がなく`Object`です。</span><span class="sxs-lookup"><span data-stu-id="ebf01-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="ebf01-120">構造体とプロシージャ</span><span class="sxs-lookup"><span data-stu-id="ebf01-120">Structures and Procedures</span></span>  
 <span data-ttu-id="ebf01-121">構造体は、プロシージャの引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="ebf01-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="ebf01-123">前の例は、構造体を渡します*参照によって*、これにより、呼び出し元のコードの変更が反映されるように、その要素を変更する手順。</span><span class="sxs-lookup"><span data-stu-id="ebf01-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="ebf01-124">このような変更に対して構造体を保護するには、場合は、値によって渡します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="ebf01-125">構造体を取得することもできます、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="ebf01-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="ebf01-126">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="ebf01-127">構造体の構造体</span><span class="sxs-lookup"><span data-stu-id="ebf01-127">Structures Within Structures</span></span>  
 <span data-ttu-id="ebf01-128">構造体には、その他の構造を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-128">Structures can contain other structures.</span></span> <span data-ttu-id="ebf01-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ebf01-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="ebf01-130">また、別のモジュールで定義されている構造内の 1 つのモジュールで定義されている構造体をカプセル化するのにこの手法を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="ebf01-131">構造体には、任意の深さを他の構造体を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ebf01-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf01-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebf01-132">See Also</span></span>  
 [<span data-ttu-id="ebf01-133">データの種類</span><span class="sxs-lookup"><span data-stu-id="ebf01-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ebf01-134">基本データ型</span><span class="sxs-lookup"><span data-stu-id="ebf01-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="ebf01-135">複合データ型</span><span class="sxs-lookup"><span data-stu-id="ebf01-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="ebf01-136">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="ebf01-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="ebf01-137">構造体</span><span class="sxs-lookup"><span data-stu-id="ebf01-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="ebf01-138">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="ebf01-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="ebf01-139">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="ebf01-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="ebf01-140">構造体変数</span><span class="sxs-lookup"><span data-stu-id="ebf01-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="ebf01-141">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="ebf01-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="ebf01-142">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="ebf01-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
