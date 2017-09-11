---
title: "XML ファイル (Visual Basic) の処理 |Microsoft ドキュメント"
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
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
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
ms.openlocfilehash: cf15cf59413e0e019086dd1a79951ccb212f037b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="bc3e7-102">XML ファイルの処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc3e7-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="bc3e7-103">コンパイラでは、ドキュメントを生成するタグが付けられて、コードの中に各構成体の ID 文字列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="bc3e7-104">(コードをタグ付けする方法については、次を参照してください[XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)。ID 文字列は、構成要素を一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="bc3e7-105">XML ファイルを処理するプログラムは、対応するを識別する ID 文字列を使用して[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]メタデータ/リフレクション項目。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="bc3e7-106">XML ファイルは、コードの階層的な表現ではありません。単純なリストの各要素に対して生成された ID を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="bc3e7-107">コンパイラは、次の規則をに基づいて ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="bc3e7-108">文字列に空白文字は適用されません。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="bc3e7-109">ID 文字列の最初の部分では、一文字、コロンで識別されるメンバーの種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="bc3e7-110">次のメンバーの型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="bc3e7-111">文字</span><span class="sxs-lookup"><span data-stu-id="bc3e7-111">Character</span></span>|<span data-ttu-id="bc3e7-112">説明</span><span class="sxs-lookup"><span data-stu-id="bc3e7-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="bc3e7-113">N</span><span class="sxs-lookup"><span data-stu-id="bc3e7-113">N</span></span>|<span data-ttu-id="bc3e7-114">namespace</span><span class="sxs-lookup"><span data-stu-id="bc3e7-114">namespace</span></span><br /><br /> <span data-ttu-id="bc3e7-115">ドキュメント コメントを名前空間に追加することはできませんが、CREF 参照を行うことができます、サポートされている場合。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="bc3e7-116">T</span><span class="sxs-lookup"><span data-stu-id="bc3e7-116">T</span></span>|<span data-ttu-id="bc3e7-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`</span><span class="sxs-lookup"><span data-stu-id="bc3e7-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="bc3e7-118">F</span><span class="sxs-lookup"><span data-stu-id="bc3e7-118">F</span></span>|<span data-ttu-id="bc3e7-119">フィールド:`Dim`</span><span class="sxs-lookup"><span data-stu-id="bc3e7-119">field: `Dim`</span></span>|  
|<span data-ttu-id="bc3e7-120">P</span><span class="sxs-lookup"><span data-stu-id="bc3e7-120">P</span></span>|<span data-ttu-id="bc3e7-121">プロパティ: `Property` (既定のプロパティを含む)</span><span class="sxs-lookup"><span data-stu-id="bc3e7-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="bc3e7-122">M</span><span class="sxs-lookup"><span data-stu-id="bc3e7-122">M</span></span>|<span data-ttu-id="bc3e7-123">method: `Sub`, `Function`, `Declare`,`Operator`</span><span class="sxs-lookup"><span data-stu-id="bc3e7-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="bc3e7-124">E</span><span class="sxs-lookup"><span data-stu-id="bc3e7-124">E</span></span>|<span data-ttu-id="bc3e7-125">イベント:`Event`</span><span class="sxs-lookup"><span data-stu-id="bc3e7-125">event: `Event`</span></span>|  
|<span data-ttu-id="bc3e7-126">!</span><span class="sxs-lookup"><span data-stu-id="bc3e7-126">!</span></span>|<span data-ttu-id="bc3e7-127">エラー文字列</span><span class="sxs-lookup"><span data-stu-id="bc3e7-127">error string</span></span><br /><br /> <span data-ttu-id="bc3e7-128">文字列の残りの部分では、エラーに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="bc3e7-129">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが解決できないリンクのエラー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="bc3e7-130">第&2; 部、 `String` 、名前空間のルートにある項目の完全修飾の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="bc3e7-131">アイテム、その外側の型、および名前空間の名前は、ピリオドで区切られます。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="bc3e7-132">項目自体の名前にピリオドが含まれている場合、それらはシャープ記号で置き換えられます。 (#)。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="bc3e7-133">項目の名前には、番号記号がないことが前提です。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="bc3e7-134">たとえば、完全修飾名の`String`コンス トラクターになる`System.String.#ctor`します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="bc3e7-135">プロパティとメソッドは、メソッドの引数がある場合、引数リストをかっこで囲まれたをたどります。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="bc3e7-136">引数がない場合は、かっこは存在しません。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="bc3e7-137">引数は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-137">The arguments are separated by commas.</span></span> <span data-ttu-id="bc3e7-138">エンコード方法に直接依存各引数のエンコーディング、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]署名します。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3e7-139">例</span><span class="sxs-lookup"><span data-stu-id="bc3e7-139">Example</span></span>  
 <span data-ttu-id="bc3e7-140">次のコードは、クラスの ID 文字列がどのようにあり、そのメンバーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc3e7-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 <span data-ttu-id="bc3e7-141">[!code-vb[VbVbcnXmlDocComments&#10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc3e7-141">[!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc3e7-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc3e7-142">See Also</span></span>  
 <span data-ttu-id="bc3e7-143">[/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="bc3e7-143">[/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="bc3e7-144"> [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="bc3e7-144"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
