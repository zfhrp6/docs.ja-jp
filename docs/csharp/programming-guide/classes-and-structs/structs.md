---
title: "構造体 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
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
ms.openlocfilehash: ce12f402c0748ea6729c82e3f188c0a58f63d628
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="538fa-102">構造体 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="538fa-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="538fa-103">構造体は [struct](../../../csharp/language-reference/keywords/struct.md) キーワードを使って定義します。次はその例です。</span><span class="sxs-lookup"><span data-stu-id="538fa-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 <span data-ttu-id="538fa-104">[!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="538fa-104">[!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]</span></span>  
  
 <span data-ttu-id="538fa-105">構造体は、構文上はクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。</span><span class="sxs-lookup"><span data-stu-id="538fa-105">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="538fa-106">構造体宣言内では、const または static と宣言されているフィールド以外は初期化できません。</span><span class="sxs-lookup"><span data-stu-id="538fa-106">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="538fa-107">構造体では、既定のコンストラクター (パラメーターなしのコンストラクター) やファイナライザーを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="538fa-107">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="538fa-108">構造体は、割り当て時にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="538fa-108">Structs are copied on assignment.</span></span> <span data-ttu-id="538fa-109">構造体を新しい変数に割り当てると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。</span><span class="sxs-lookup"><span data-stu-id="538fa-109">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="538fa-110">これは、Dictionary\<string, myStruct> などの値の型のコレクションを使用する際に重要です。</span><span class="sxs-lookup"><span data-stu-id="538fa-110">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="538fa-111">構造体は値型ですが、クラスは参照型です。</span><span class="sxs-lookup"><span data-stu-id="538fa-111">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="538fa-112">クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="538fa-112">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="538fa-113">構造体は、パラメーターのあるコンストラクターを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="538fa-113">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="538fa-114">構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。</span><span class="sxs-lookup"><span data-stu-id="538fa-114">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="538fa-115">すべての構造体が `System.ValueType` を直接継承し、System.ValueType は `System.Object` を継承します。</span><span class="sxs-lookup"><span data-stu-id="538fa-115">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="538fa-116">構造体は、インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="538fa-116">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="538fa-117">構造体は、null 許容型として使うことができ、null 値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="538fa-117">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="538fa-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="538fa-118">Related Sections</span></span>  
 <span data-ttu-id="538fa-119">詳細情報</span><span class="sxs-lookup"><span data-stu-id="538fa-119">For more information:</span></span>  
  
-   [<span data-ttu-id="538fa-120">構造体の使用</span><span class="sxs-lookup"><span data-stu-id="538fa-120">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="538fa-121">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="538fa-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="538fa-122">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="538fa-122">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="538fa-123">方法: メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する</span><span class="sxs-lookup"><span data-stu-id="538fa-123">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="538fa-124">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="538fa-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="538fa-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="538fa-125">See Also</span></span>  
 <span data-ttu-id="538fa-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="538fa-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="538fa-127">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="538fa-127">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 [<span data-ttu-id="538fa-128">クラス</span><span class="sxs-lookup"><span data-stu-id="538fa-128">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

