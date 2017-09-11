---
title: "方法 : C# で定数を定義する"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: 7
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
ms.openlocfilehash: 6c5a6f63675893eb0700afab462bf237f5639d74
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="2f4d1-102">方法 : C# で定数を定義する</span><span class="sxs-lookup"><span data-stu-id="2f4d1-102">How to: Define Constants in C#</span></span>
<span data-ttu-id="2f4d1-103">定数とは、値がコンパイル時に設定され、変更できないフィールドです。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="2f4d1-104">定数を使用して、特殊な値の数値リテラル ("マジック ナンバー") の代わりにわかりやすい名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f4d1-105">C# では、C と C++ で通常使用される方法で、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) プリプロセッサ ディレクティブを使用して定数を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="2f4d1-106">整数型 (`int`、`byte` など) の定数値を定義するには、列挙型を使用します。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="2f4d1-107">詳細については、「[enum](../../../csharp/language-reference/keywords/enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="2f4d1-108">整数型以外の定数を定義する 1 つの方法は、`Constants` という名前の 1 つの静的クラスにそれらをグループ化することです。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="2f4d1-109">これを行うには、次の例に示すように、クラス名の前に定数へのすべての参照を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f4d1-110">例</span><span class="sxs-lookup"><span data-stu-id="2f4d1-110">Example</span></span>  
 <span data-ttu-id="2f4d1-111">[!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2f4d1-111">[!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]</span></span>  
  
 <span data-ttu-id="2f4d1-112">クラス名修飾子を使用すると、定数を使用するユーザーは、それが定数であり、変更できないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="2f4d1-112">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4d1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f4d1-113">See Also</span></span>  
 [<span data-ttu-id="2f4d1-114">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="2f4d1-114">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)

