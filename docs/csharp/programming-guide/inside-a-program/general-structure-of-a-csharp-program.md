---
title: "C# プログラムの一般構造 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, program structure
ms.assetid: 5ae964a5-0ef0-40fe-88fb-6d1793371d0d
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d55ac6a6d35e5f47ab26da681afe9fb5555331ec
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="general-structure-of-a-c-program-c-programming-guide"></a><span data-ttu-id="b0e21-102">C# プログラムの一般構造 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b0e21-102">General Structure of a C# Program (C# Programming Guide)</span></span>
<span data-ttu-id="b0e21-103">C# プログラムは、1 つ以上のファイルで構成できます。</span><span class="sxs-lookup"><span data-stu-id="b0e21-103">C# programs can consist of one or more files.</span></span> <span data-ttu-id="b0e21-104">各ファイルには、0 個以上の名前空間を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b0e21-104">Each file can contain zero or more namespaces.</span></span> <span data-ttu-id="b0e21-105">名前空間には、その他の名前空間以外に、クラス、構造体、インターフェイス、列挙型、デリゲートなどの型を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b0e21-105">A namespace can contain types such as classes, structs, interfaces, enumerations, and delegates, in addition to other namespaces.</span></span> <span data-ttu-id="b0e21-106">次に示すのは、これら要素をすべて含む C# プログラムのスケルトンです。</span><span class="sxs-lookup"><span data-stu-id="b0e21-106">The following is the skeleton of a C# program that contains all of these elements.</span></span>  
  
 <span data-ttu-id="b0e21-107">[!code-cs[csProgGuide#34](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/general-structure-of-a-csharp-program_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b0e21-107">[!code-cs[csProgGuide#34](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/general-structure-of-a-csharp-program_1.cs)]</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0e21-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0e21-108">Related Sections</span></span>  
 <span data-ttu-id="b0e21-109">詳細情報</span><span class="sxs-lookup"><span data-stu-id="b0e21-109">For more information:</span></span>  
  
-   [<span data-ttu-id="b0e21-110">クラス</span><span class="sxs-lookup"><span data-stu-id="b0e21-110">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [<span data-ttu-id="b0e21-111">構造体</span><span class="sxs-lookup"><span data-stu-id="b0e21-111">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [<span data-ttu-id="b0e21-112">名前空間</span><span class="sxs-lookup"><span data-stu-id="b0e21-112">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="b0e21-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0e21-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [<span data-ttu-id="b0e21-114">デリゲート</span><span class="sxs-lookup"><span data-stu-id="b0e21-114">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="b0e21-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b0e21-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0e21-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0e21-116">See Also</span></span>  
 <span data-ttu-id="b0e21-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0e21-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b0e21-118">[インサイド C# プログラム](../../../csharp/programming-guide/inside-a-program/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0e21-118">[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md) </span></span>  
 <span data-ttu-id="b0e21-119">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0e21-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="b0e21-120">\<paveover>C# サンプル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b0e21-120">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)

