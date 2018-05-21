---
title: partial (型) (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4f57149dd18deb08aa11b72d0a6d5f71b3838bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="cb09c-102">partial (型) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cb09c-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="cb09c-103">部分型定義では、クラス、構造体、またはインターフェイスの定義を複数のファイルに分割することができます。</span><span class="sxs-lookup"><span data-stu-id="cb09c-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="cb09c-104">次に File1.cs の部分型定義を示します。</span><span class="sxs-lookup"><span data-stu-id="cb09c-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="cb09c-105">次に File2.cs での宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="cb09c-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="cb09c-106">コメント</span><span class="sxs-lookup"><span data-stu-id="cb09c-106">Remarks</span></span>  
 <span data-ttu-id="cb09c-107">クラス型、構造体型、またはインターフェイス型を複数のファイルに分割する操作は、大規模なプロジェクトや、[Windows フォーム デザイナー](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)で自動生成されるコードを処理する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cb09c-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="cb09c-108">部分型には、[部分メソッド](../../../csharp/language-reference/keywords/partial-method.md)が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb09c-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="cb09c-109">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb09c-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cb09c-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="cb09c-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb09c-111">参照</span><span class="sxs-lookup"><span data-stu-id="cb09c-111">See Also</span></span>  
 [<span data-ttu-id="cb09c-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="cb09c-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cb09c-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cb09c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cb09c-114">修飾子</span><span class="sxs-lookup"><span data-stu-id="cb09c-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="cb09c-115">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="cb09c-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
