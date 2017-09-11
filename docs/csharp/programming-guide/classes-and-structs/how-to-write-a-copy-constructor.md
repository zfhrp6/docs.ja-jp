---
title: "方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: 20
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
ms.openlocfilehash: 712d9d5e792d025dd7c91d4c1809eeba96759757
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="270fe-102">方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="270fe-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="270fe-103">C# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="270fe-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="270fe-104">例</span><span class="sxs-lookup"><span data-stu-id="270fe-104">Example</span></span>  
 <span data-ttu-id="270fe-105">次の例の `Person` [クラス](../../../csharp/language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。</span><span class="sxs-lookup"><span data-stu-id="270fe-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="270fe-106">引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="270fe-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="270fe-107">このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="270fe-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 <span data-ttu-id="270fe-108">[!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="270fe-108">[!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="270fe-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="270fe-109">See Also</span></span>  
 <span data-ttu-id="270fe-110"><xref:System.ICloneable></span><span class="sxs-lookup"><span data-stu-id="270fe-110"><xref:System.ICloneable></span></span>   
 <span data-ttu-id="270fe-111">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="270fe-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="270fe-112">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="270fe-112">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="270fe-113">[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="270fe-113">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 [<span data-ttu-id="270fe-114">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="270fe-114">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

