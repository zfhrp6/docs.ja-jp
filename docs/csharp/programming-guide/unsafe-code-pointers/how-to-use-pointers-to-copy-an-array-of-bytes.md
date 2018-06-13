---
title: '方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 800a600f0fa7ca52d0433c8d90039434bf6b7f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331202"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="6172f-102">方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6172f-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="6172f-103">次の例では、ポインターを使って 1 つの配列から別の配列にバイトをコピーします。</span><span class="sxs-lookup"><span data-stu-id="6172f-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="6172f-104">この例では、[unsafe](../../language-reference/keywords/unsafe.md) キーワードを使います。このキーワードは、`Copy` メソッドでのポインターの使用を可能にします。</span><span class="sxs-lookup"><span data-stu-id="6172f-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="6172f-105">[fixed](../../language-reference/keywords/fixed-statement.md) ステートメントを使って、コピー元とコピー先の配列へのポインターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="6172f-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="6172f-106">`fixed` ステートメントを使って、コピー元配列とコピー先配列のメモリ内での位置を "*固定*" し、ガベージ コレクションによって移動されないようにします。</span><span class="sxs-lookup"><span data-stu-id="6172f-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="6172f-107">`fixed` ブロックが完了すると、これらの配列のメモリ ブロックは固定解除されます。</span><span class="sxs-lookup"><span data-stu-id="6172f-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="6172f-108">この例の `Copy` メソッドは `unsafe` キーワードを使っているので、[-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを指定してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6172f-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="6172f-109">この例では、2 番目のアンマネージド ポインターではなくインデックスを使って、両方の配列の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6172f-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="6172f-110">`pSource` と `pTarget` のポインターの宣言を使って配列を固定します。</span><span class="sxs-lookup"><span data-stu-id="6172f-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="6172f-111">この機能は、C# 7.3 以降から使用できます。</span><span class="sxs-lookup"><span data-stu-id="6172f-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="6172f-112">例</span><span class="sxs-lookup"><span data-stu-id="6172f-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="6172f-113">参照</span><span class="sxs-lookup"><span data-stu-id="6172f-113">See Also</span></span>
 [<span data-ttu-id="6172f-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6172f-114">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="6172f-115">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="6172f-115">Unsafe Code and Pointers</span></span>](index.md)  
 [<span data-ttu-id="6172f-116">-unsafe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="6172f-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="6172f-117">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="6172f-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
