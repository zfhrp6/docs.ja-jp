---
title: "構造体 (Visual Basic) |Microsoft ドキュメント"
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
- structures
- user-defined data types, structures
- user-defined types, about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types, about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
caps.latest.revision: 13
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
ms.openlocfilehash: d1ba8671af9ff6d50499149fce6d55b3db78ffe0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="structures-visual-basic"></a><span data-ttu-id="fbf1c-102">構造体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf1c-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="fbf1c-103">A*構造*、ユーザー定義型 (UDT) の以前のバージョンでサポートされるを一般化した[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="fbf1c-104">構造体には、フィールドのほか、プロパティ、メソッド、およびイベントを公開できます。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="fbf1c-105">構造体が&1; つ以上のインターフェイスを実装し、フィールドごとに個別のアクセス レベルを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="fbf1c-106">構造を作成するさまざまな種類のデータ項目を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="fbf1c-107">構造体は、1 つまたは複数を関連付けます*要素*と構造体そのものです。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="fbf1c-108">構造体を宣言するときになったら、*複合データ型*、し、その型の変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="fbf1c-109">構造体は、いくつかの関連情報を保持するために&1; つの変数が必要な場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="fbf1c-110">たとえば、従業員の名前、内線番号、および給与をまとめて保存することができます。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="fbf1c-111">この詳細については、いくつかの変数を使用することが、または構造体を定義して、1 人の従業員の変数に使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="fbf1c-112">構造体の利点は、多くの従業員とそのため、変数の多くの場合がある場合に明らかになります。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbf1c-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fbf1c-113">In This Section</span></span>  
 [<span data-ttu-id="fbf1c-114">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="fbf1c-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="fbf1c-115">構造体とその要素を宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="fbf1c-116">構造体変数</span><span class="sxs-lookup"><span data-stu-id="fbf1c-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="fbf1c-117">構造体の変数に代入し、その要素へのアクセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="fbf1c-118">構造体とその他のプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="fbf1c-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="fbf1c-119">構造体が配列、オブジェクト、プロシージャ、および互いと対話する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="fbf1c-120">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="fbf1c-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="fbf1c-121">類似点と構造体とクラスの相違点について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fbf1c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbf1c-122">Related Sections</span></span>  
 [<span data-ttu-id="fbf1c-123">データの種類</span><span class="sxs-lookup"><span data-stu-id="fbf1c-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="fbf1c-124">導入されています、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のデータ型し、その使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-124">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="fbf1c-125">データの種類</span><span class="sxs-lookup"><span data-stu-id="fbf1c-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="fbf1c-126">によって提供される基本データ型を一覧表示[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="fbf1c-126">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>
