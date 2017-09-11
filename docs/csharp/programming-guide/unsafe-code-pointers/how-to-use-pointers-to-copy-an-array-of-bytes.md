---
title: "方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
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
ms.openlocfilehash: 808a74f75e4dcbcec47735d98063138e2c7456e5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="e6af7-102">方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e6af7-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="e6af7-103">次の例では、ポインターを使って 1 つの配列から別の配列にバイトをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e6af7-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="e6af7-104">この例では、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使います。このキーワードは、`Copy` メソッドでのポインターの使用を可能にします。</span><span class="sxs-lookup"><span data-stu-id="e6af7-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="e6af7-105">[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使って、コピー元とコピー先の配列へのポインターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e6af7-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="e6af7-106">これにより、コピー元配列とコピー先配列のメモリ内での位置を "*固定*" し、ガベージ コレクションによって移動されないようにします。</span><span class="sxs-lookup"><span data-stu-id="e6af7-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="e6af7-107">`fixed` ブロックが完了すると、これらの配列のメモリ ブロックは固定解除されます。</span><span class="sxs-lookup"><span data-stu-id="e6af7-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="e6af7-108">この例の `Copy` メソッドは `unsafe` キーワードを使っているので、**/unsafe** コンパイラ オプションを指定してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6af7-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="e6af7-109">Visual Studio でオプションを設定するには、プロジェクト名を右クリックして、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6af7-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="e6af7-110">**[ビルド]** タブで **[アンセーフ コードの許可]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6af7-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6af7-111">例</span><span class="sxs-lookup"><span data-stu-id="e6af7-111">Example</span></span>  
 <span data-ttu-id="e6af7-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e6af7-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]</span></span>  
  
 <span data-ttu-id="e6af7-113">[!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e6af7-113">[!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6af7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6af7-114">See Also</span></span>  
 <span data-ttu-id="e6af7-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6af7-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e6af7-116">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6af7-116">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="e6af7-117">[/unsafe (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="e6af7-117">[/unsafe (C# Compiler Options)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) </span></span>  
 [<span data-ttu-id="e6af7-118">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="e6af7-118">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

