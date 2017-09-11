---
title: "partial (型) (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
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
ms.openlocfilehash: 5405455d933f6512cfa3a18e1a545556c5715151
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="partial-type-c-reference"></a><span data-ttu-id="ba877-102">partial (型) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ba877-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="ba877-103">部分型定義では、クラス、構造体、またはインターフェイスの定義を複数のファイルに分割することができます。</span><span class="sxs-lookup"><span data-stu-id="ba877-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="ba877-104">次に File1.cs の部分型定義を示します。</span><span class="sxs-lookup"><span data-stu-id="ba877-104">In File1.cs:</span></span>  
  
 <span data-ttu-id="ba877-105">[!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ba877-105">[!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]</span></span>  
  
 <span data-ttu-id="ba877-106">次に File2.cs での宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="ba877-106">In File2.cs the declaration:</span></span>  
  
 <span data-ttu-id="ba877-107">[!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ba877-107">[!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba877-108">コメント</span><span class="sxs-lookup"><span data-stu-id="ba877-108">Remarks</span></span>  
 <span data-ttu-id="ba877-109">クラス型、構造体型、またはインターフェイス型を複数のファイルに分割する操作は、大規模なプロジェクトや、[Windows フォーム デザイナー](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)で自動生成されるコードを処理する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ba877-109">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).</span></span> <span data-ttu-id="ba877-110">部分型には、[部分メソッド](../../../csharp/language-reference/keywords/partial-method.md)が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba877-110">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="ba877-111">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba877-111">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ba877-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ba877-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba877-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba877-113">See Also</span></span>  
 <span data-ttu-id="ba877-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ba877-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ba877-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ba877-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ba877-116">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ba877-116">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="ba877-117">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="ba877-117">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)

