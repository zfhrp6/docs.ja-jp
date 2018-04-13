---
title: XML ファイルの処理 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d44f58951d99f1b4b551af75dc0a0e895e337e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="39f8c-102">XML ファイルの処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39f8c-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="39f8c-103">コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="39f8c-104">(コードをタグ付けする方法については、次を参照してください[XML コメント タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)。ID 文字列によって、コンストラクトは一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="39f8c-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="39f8c-105">XML ファイルを処理するプログラムが、対応するを識別する ID 文字列を使用して[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メタデータ/リフレクション項目。</span><span class="sxs-lookup"><span data-stu-id="39f8c-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="39f8c-106">XML ファイルは、コードの階層的な表現ではありません。単純なリストの各要素に対して生成された ID を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39f8c-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="39f8c-107">コンパイラは、次の規則に基づいて ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="39f8c-108">文字列内の空白文字は配置されません。</span><span class="sxs-lookup"><span data-stu-id="39f8c-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="39f8c-109">ID 文字列の最初の部分では、その後にコロン、1 文字で識別されるメンバーの種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="39f8c-110">次のメンバーの種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="39f8c-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="39f8c-111">文字</span><span class="sxs-lookup"><span data-stu-id="39f8c-111">Character</span></span>|<span data-ttu-id="39f8c-112">説明</span><span class="sxs-lookup"><span data-stu-id="39f8c-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="39f8c-113">N</span><span class="sxs-lookup"><span data-stu-id="39f8c-113">N</span></span>|<span data-ttu-id="39f8c-114">namespace</span><span class="sxs-lookup"><span data-stu-id="39f8c-114">namespace</span></span><br /><br /> <span data-ttu-id="39f8c-115">名前空間にドキュメント コメントを追加することはできませんが、それらを CREF 参照を行うことができます、サポートされている場合。</span><span class="sxs-lookup"><span data-stu-id="39f8c-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="39f8c-116">T</span><span class="sxs-lookup"><span data-stu-id="39f8c-116">T</span></span>|<span data-ttu-id="39f8c-117">型: `Class`、 `Module`、 `Interface`、 `Structure`、 `Enum`、`Delegate`</span><span class="sxs-lookup"><span data-stu-id="39f8c-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="39f8c-118">F</span><span class="sxs-lookup"><span data-stu-id="39f8c-118">F</span></span>|<span data-ttu-id="39f8c-119">フィールド:`Dim`</span><span class="sxs-lookup"><span data-stu-id="39f8c-119">field: `Dim`</span></span>|  
|<span data-ttu-id="39f8c-120">P</span><span class="sxs-lookup"><span data-stu-id="39f8c-120">P</span></span>|<span data-ttu-id="39f8c-121">プロパティ: `Property` (既定のプロパティを含む)</span><span class="sxs-lookup"><span data-stu-id="39f8c-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="39f8c-122">M</span><span class="sxs-lookup"><span data-stu-id="39f8c-122">M</span></span>|<span data-ttu-id="39f8c-123">方法: `Sub`、 `Function`、 `Declare`、`Operator`</span><span class="sxs-lookup"><span data-stu-id="39f8c-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="39f8c-124">E</span><span class="sxs-lookup"><span data-stu-id="39f8c-124">E</span></span>|<span data-ttu-id="39f8c-125">イベント:`Event`</span><span class="sxs-lookup"><span data-stu-id="39f8c-125">event: `Event`</span></span>|  
|<span data-ttu-id="39f8c-126">!</span><span class="sxs-lookup"><span data-stu-id="39f8c-126">!</span></span>|<span data-ttu-id="39f8c-127">エラー文字列</span><span class="sxs-lookup"><span data-stu-id="39f8c-127">error string</span></span><br /><br /> <span data-ttu-id="39f8c-128">あとに続く文字列で、エラーの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="39f8c-129">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラを解決できないリンクのエラー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-129">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="39f8c-130">2 番目の部分、 `String` 、名前空間のルートにある項目の完全修飾の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="39f8c-131">アイテム、その外側の型、および名前空間の名前は、ピリオドで区切られます。</span><span class="sxs-lookup"><span data-stu-id="39f8c-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="39f8c-132">項目自体の名前にピリオドが含まれている場合は、置き換えられるシャープ記号 (#)。</span><span class="sxs-lookup"><span data-stu-id="39f8c-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="39f8c-133">項目の名前には、番号記号がないことが前提です。</span><span class="sxs-lookup"><span data-stu-id="39f8c-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="39f8c-134">たとえば、完全修飾名の`String`コンス トラクターになる`System.String.#ctor`です。</span><span class="sxs-lookup"><span data-stu-id="39f8c-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="39f8c-135">プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="39f8c-136">引数がない場合は、かっこはありません。</span><span class="sxs-lookup"><span data-stu-id="39f8c-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="39f8c-137">引数はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="39f8c-137">The arguments are separated by commas.</span></span> <span data-ttu-id="39f8c-138">エンコード方法に直接依存引数はそれぞれのエンコード、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]署名します。</span><span class="sxs-lookup"><span data-stu-id="39f8c-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39f8c-139">例</span><span class="sxs-lookup"><span data-stu-id="39f8c-139">Example</span></span>  
 <span data-ttu-id="39f8c-140">次のコードは、クラスの ID の文字列し、そのメンバーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="39f8c-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="39f8c-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="39f8c-141">See Also</span></span>  
 [<span data-ttu-id="39f8c-142">/doc</span><span class="sxs-lookup"><span data-stu-id="39f8c-142">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="39f8c-143">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="39f8c-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
