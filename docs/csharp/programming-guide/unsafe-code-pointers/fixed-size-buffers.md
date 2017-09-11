---
title: "固定サイズ バッファー (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
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
ms.openlocfilehash: e1a3dcf953cb56fc3436fdd5e7ecb60478a12922
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="1726f-102">固定サイズ バッファー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1726f-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="1726f-103">C# では、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使って、データの構造体に固定サイズの配列を持ったバッファーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1726f-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="1726f-104">これは既存のコード (他の言語で記述されたコード、既存の DLL、COM プロジェクトなど) を扱う場面で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1726f-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="1726f-105">この固定配列には、標準的な構造体メンバーで許容されている属性または修飾子であれば、何でも適用することができます。</span><span class="sxs-lookup"><span data-stu-id="1726f-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="1726f-106">ただし配列の型は `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float`、`double` のいずれかに該当する必要があり、それが唯一の制限となります。</span><span class="sxs-lookup"><span data-stu-id="1726f-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="1726f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1726f-107">Remarks</span></span>  
 <span data-ttu-id="1726f-108">以前のバージョンの C# では、C++ スタイルの固定サイズ構造体を宣言することが困難でした。配列を含んだ C# の構造体には、配列の要素は格納されないためです。</span><span class="sxs-lookup"><span data-stu-id="1726f-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="1726f-109">この場合、構造体には、配列の要素ではなく、その参照が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1726f-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="1726f-110">C# 2.0 では、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) のコード ブロックで使われている [struct](../../../csharp/language-reference/keywords/struct.md) に、固定サイズの配列を埋め込むことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1726f-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="1726f-111">たとえば C# 2.0 未満では、以下の `struct` のサイズは 8 バイトとなります。</span><span class="sxs-lookup"><span data-stu-id="1726f-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="1726f-112">`pathName` 配列は、ヒープに割り当てられた配列の参照です。</span><span class="sxs-lookup"><span data-stu-id="1726f-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 <span data-ttu-id="1726f-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1726f-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span></span>  
  
 <span data-ttu-id="1726f-114">C# 2.0 以降では、`struct` が埋め込み配列を保持できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1726f-114">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="1726f-115">以下の例の `fixedBuffer` 配列は固定サイズです。</span><span class="sxs-lookup"><span data-stu-id="1726f-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="1726f-116">配列の要素にアクセスするには、`fixed` ステートメントを使用して先頭要素へのポインターを確立します。</span><span class="sxs-lookup"><span data-stu-id="1726f-116">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="1726f-117">`fixed` ステートメントによって、`fixedBuffer` のインスタンスがメモリ内の特定の位置に固定されます。</span><span class="sxs-lookup"><span data-stu-id="1726f-117">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 <span data-ttu-id="1726f-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1726f-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span></span>  
  
 <span data-ttu-id="1726f-119">要素数 128 の `char` 配列のサイズは 256 バイトです。</span><span class="sxs-lookup"><span data-stu-id="1726f-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="1726f-120">固定サイズの [char](../../../csharp/language-reference/keywords/char.md) 型バッファーは、エンコーディングに関係なく常に、1 文字あたり 2 バイトを消費します。</span><span class="sxs-lookup"><span data-stu-id="1726f-120">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="1726f-121">これは、char 型のバッファーが、`CharSet = CharSet.Auto` または `CharSet = CharSet.Ansi` で API メソッドや構造体にマーシャリングされたときにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="1726f-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="1726f-122">詳細については、「<xref:System.Runtime.InteropServices.CharSet>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1726f-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="1726f-123">一般的な固定サイズの配列としては、他にも [bool](../../../csharp/language-reference/keywords/bool.md) 配列があります。</span><span class="sxs-lookup"><span data-stu-id="1726f-123">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="1726f-124">`bool` 配列内の要素のサイズは常に 1 バイトです。</span><span class="sxs-lookup"><span data-stu-id="1726f-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="1726f-125">`bool` 配列は、ビット配列やバッファーの作成には適していません。</span><span class="sxs-lookup"><span data-stu-id="1726f-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1726f-126">C# コンパイラおよび共通言語ランタイム (CLR) は、[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) を使って作成されたメモリを除き、バッファー オーバーランのセキュリティ チェックを実行しません。</span><span class="sxs-lookup"><span data-stu-id="1726f-126">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="1726f-127">その他のアンセーフ コードと同様、十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="1726f-127">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="1726f-128">アンセーフ バッファーは、次の点で通常の配列とは異なります。</span><span class="sxs-lookup"><span data-stu-id="1726f-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="1726f-129">アンセーフ バッファーの使用は、unsafe コンテキストに限られます。</span><span class="sxs-lookup"><span data-stu-id="1726f-129">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="1726f-130">アンセーフ バッファーは常にベクタ (1 次元配列) です。</span><span class="sxs-lookup"><span data-stu-id="1726f-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="1726f-131">配列の宣言には要素数を指定する必要があります (例: `char id[8]`)。</span><span class="sxs-lookup"><span data-stu-id="1726f-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="1726f-132">`char id[]` のようにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1726f-132">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="1726f-133">アンセーフ バッファーは、unsafe コンテキストで構造体のインスタンス フィールドとしてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1726f-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1726f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="1726f-134">See Also</span></span>  
 <span data-ttu-id="1726f-135">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1726f-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1726f-136">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="1726f-136">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="1726f-137">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1726f-137">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="1726f-138">相互運用性</span><span class="sxs-lookup"><span data-stu-id="1726f-138">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)

