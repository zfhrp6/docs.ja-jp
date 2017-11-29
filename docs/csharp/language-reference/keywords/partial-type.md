---
title: "partial (型) (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords: partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5212984cc577ce05fc4697e0d648fb5545528562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="450f3-102">partial (型) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="450f3-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="450f3-103">部分型定義では、クラス、構造体、またはインターフェイスの定義を複数のファイルに分割することができます。</span><span class="sxs-lookup"><span data-stu-id="450f3-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="450f3-104">次に File1.cs の部分型定義を示します。</span><span class="sxs-lookup"><span data-stu-id="450f3-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="450f3-105">次に File2.cs での宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="450f3-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="450f3-106">コメント</span><span class="sxs-lookup"><span data-stu-id="450f3-106">Remarks</span></span>  
 <span data-ttu-id="450f3-107">クラス型、構造体型、またはインターフェイス型を複数のファイルに分割する操作は、大規模なプロジェクトや、[Windows フォーム デザイナー](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)で自動生成されるコードを処理する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="450f3-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="450f3-108">部分型には、[部分メソッド](../../../csharp/language-reference/keywords/partial-method.md)が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="450f3-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="450f3-109">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="450f3-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="450f3-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="450f3-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="450f3-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="450f3-111">See Also</span></span>  
 [<span data-ttu-id="450f3-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="450f3-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="450f3-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="450f3-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="450f3-114">修飾子</span><span class="sxs-lookup"><span data-stu-id="450f3-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="450f3-115">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="450f3-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
