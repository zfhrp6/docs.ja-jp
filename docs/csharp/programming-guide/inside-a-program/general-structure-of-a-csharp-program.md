---
title: "C# プログラムの一般構造 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: C# language, program structure
ms.assetid: 5ae964a5-0ef0-40fe-88fb-6d1793371d0d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8886f7601ce4d1de4a6b277a803ff87eb67bee78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="general-structure-of-a-c-program-c-programming-guide"></a><span data-ttu-id="3fd14-102">C# プログラムの一般構造 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3fd14-102">General Structure of a C# Program (C# Programming Guide)</span></span>
<span data-ttu-id="3fd14-103">C# プログラムは、1 つ以上のファイルで構成できます。</span><span class="sxs-lookup"><span data-stu-id="3fd14-103">C# programs can consist of one or more files.</span></span> <span data-ttu-id="3fd14-104">各ファイルには、0 個以上の名前空間を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3fd14-104">Each file can contain zero or more namespaces.</span></span> <span data-ttu-id="3fd14-105">名前空間には、その他の名前空間以外に、クラス、構造体、インターフェイス、列挙型、デリゲートなどの型を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3fd14-105">A namespace can contain types such as classes, structs, interfaces, enumerations, and delegates, in addition to other namespaces.</span></span> <span data-ttu-id="3fd14-106">次に示すのは、これら要素をすべて含む C# プログラムのスケルトンです。</span><span class="sxs-lookup"><span data-stu-id="3fd14-106">The following is the skeleton of a C# program that contains all of these elements.</span></span>  
  
 [!code-csharp[csProgGuide#34](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/general-structure-of-a-csharp-program_1.cs)]  
  
## <a name="related-sections"></a><span data-ttu-id="3fd14-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fd14-107">Related Sections</span></span>  
 <span data-ttu-id="3fd14-108">詳細情報</span><span class="sxs-lookup"><span data-stu-id="3fd14-108">For more information:</span></span>  
  
-   [<span data-ttu-id="3fd14-109">クラス</span><span class="sxs-lookup"><span data-stu-id="3fd14-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [<span data-ttu-id="3fd14-110">構造体</span><span class="sxs-lookup"><span data-stu-id="3fd14-110">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [<span data-ttu-id="3fd14-111">名前空間</span><span class="sxs-lookup"><span data-stu-id="3fd14-111">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="3fd14-112">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fd14-112">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [<span data-ttu-id="3fd14-113">デリゲート</span><span class="sxs-lookup"><span data-stu-id="3fd14-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3fd14-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="3fd14-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3fd14-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fd14-115">See Also</span></span>  
 [<span data-ttu-id="3fd14-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="3fd14-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3fd14-117">インサイド C# プログラム</span><span class="sxs-lookup"><span data-stu-id="3fd14-117">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="3fd14-118">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="3fd14-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3fd14-119">\<paveover>C# サンプル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3fd14-119">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)
