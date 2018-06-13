---
title: '方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 8a7cc85d40272918f4839d13fcccb79b558eeac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322498"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="42c84-102">方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="42c84-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="42c84-103">C# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="42c84-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42c84-104">例</span><span class="sxs-lookup"><span data-stu-id="42c84-104">Example</span></span>  
 <span data-ttu-id="42c84-105">次の例の `Person` [クラス](../../../csharp/language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。</span><span class="sxs-lookup"><span data-stu-id="42c84-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="42c84-106">引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="42c84-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="42c84-107">このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="42c84-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="42c84-108">参照</span><span class="sxs-lookup"><span data-stu-id="42c84-108">See Also</span></span>  
 <xref:System.ICloneable>  
 [<span data-ttu-id="42c84-109">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="42c84-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="42c84-110">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="42c84-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="42c84-111">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="42c84-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="42c84-112">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="42c84-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
