---
title: "構造体の変数 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42c44de84caffde909eb2b3e9361016a6abb97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="c7bdf-102">構造体の変数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7bdf-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="c7bdf-103">構造体を作成した後は、その型としてプロシージャ レベルとモジュール レベル変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="c7bdf-104">たとえば、コンピューター システムに関する情報を記録する構造体を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="c7bdf-105">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="c7bdf-106">その型の変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-106">You can now declare variables of that type.</span></span> <span data-ttu-id="c7bdf-107">次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="c7bdf-108">クラスやモジュールで宣言された構造体を使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)既定でパブリック アクセスです。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="c7bdf-109">構造体をプライベートにする場合を使用して宣言を確認してください、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="c7bdf-110">構造体の値へのアクセス</span><span class="sxs-lookup"><span data-stu-id="c7bdf-110">Access to Structure Values</span></span>  
 <span data-ttu-id="c7bdf-111">割り当てるし、構造体変数の要素から値を取得、設定し、オブジェクトのプロパティの取得に使用すると同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="c7bdf-112">メンバー アクセス演算子を配置する (`.`) 構造体の変数名と要素名の間です。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="c7bdf-113">次の例では、要素型として以前に宣言された変数の`systemInfo`します。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="c7bdf-114">構造体の変数を割り当てる</span><span class="sxs-lookup"><span data-stu-id="c7bdf-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="c7bdf-115">どちらも、同じ構造体型の場合、別に 1 つの変数を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="c7bdf-116">これにより、1 つの構造体のすべての要素が、他の対応する要素にコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="c7bdf-117">次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="c7bdf-118">構造体の要素が、参照型など、 `String`、 `Object`、またはデータへのポインターの配列をコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="c7bdf-119">前の例では場合、`systemInfo`のポインターが前の例をコピーしたが、オブジェクト変数が含まれていた`mySystem`に`yourSystem`、アクセスするときに、1 つの構造を使用して、オブジェクトのデータへの変更が有効にすると、を介して、他の構造体。</span><span class="sxs-lookup"><span data-stu-id="c7bdf-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7bdf-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7bdf-120">See Also</span></span>  
 [<span data-ttu-id="c7bdf-121">データの種類</span><span class="sxs-lookup"><span data-stu-id="c7bdf-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="c7bdf-122">基本データ型</span><span class="sxs-lookup"><span data-stu-id="c7bdf-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="c7bdf-123">複合データ型</span><span class="sxs-lookup"><span data-stu-id="c7bdf-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="c7bdf-124">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="c7bdf-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="c7bdf-125">構造体</span><span class="sxs-lookup"><span data-stu-id="c7bdf-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="c7bdf-126">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="c7bdf-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="c7bdf-127">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="c7bdf-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="c7bdf-128">構造体とその他のプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="c7bdf-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="c7bdf-129">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="c7bdf-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="c7bdf-130">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="c7bdf-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
