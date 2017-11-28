---
title: "固定サイズ バッファー (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="394fa-102">固定サイズ バッファー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="394fa-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="394fa-103">C# では、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使って、データの構造体に固定サイズの配列を持ったバッファーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="394fa-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="394fa-104">これは既存のコード (他の言語で記述されたコード、既存の DLL、COM プロジェクトなど) を扱う場面で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="394fa-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="394fa-105">この固定配列には、標準的な構造体メンバーで許容されている属性または修飾子であれば、何でも適用することができます。</span><span class="sxs-lookup"><span data-stu-id="394fa-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="394fa-106">ただし配列の型は `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float`、`double` のいずれかに該当する必要があり、それが唯一の制限となります。</span><span class="sxs-lookup"><span data-stu-id="394fa-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="394fa-107">コメント</span><span class="sxs-lookup"><span data-stu-id="394fa-107">Remarks</span></span>  
 <span data-ttu-id="394fa-108">以前のバージョンの C# では、C++ スタイルの固定サイズ構造体を宣言することが困難でした。配列を含んだ C# の構造体には、配列の要素は格納されないためです。</span><span class="sxs-lookup"><span data-stu-id="394fa-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="394fa-109">この場合、構造体には、配列の要素ではなく、その参照が格納されます。</span><span class="sxs-lookup"><span data-stu-id="394fa-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="394fa-110">C# 2.0 では、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) のコード ブロックで使われている [struct](../../../csharp/language-reference/keywords/struct.md) に、固定サイズの配列を埋め込むことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="394fa-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="394fa-111">たとえば C# 2.0 未満では、以下の `struct` のサイズは 8 バイトとなります。</span><span class="sxs-lookup"><span data-stu-id="394fa-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="394fa-112">`pathName` 配列は、ヒープに割り当てられた配列の参照です。</span><span class="sxs-lookup"><span data-stu-id="394fa-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 <span data-ttu-id="394fa-113">C# 2.0 以降では、`struct` が埋め込み配列を保持できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="394fa-113">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="394fa-114">以下の例の `fixedBuffer` 配列は固定サイズです。</span><span class="sxs-lookup"><span data-stu-id="394fa-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="394fa-115">配列の要素にアクセスするには、`fixed` ステートメントを使用して先頭要素へのポインターを確立します。</span><span class="sxs-lookup"><span data-stu-id="394fa-115">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="394fa-116">`fixed` ステートメントによって、`fixedBuffer` のインスタンスがメモリ内の特定の位置に固定されます。</span><span class="sxs-lookup"><span data-stu-id="394fa-116">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 <span data-ttu-id="394fa-117">要素数 128 の `char` 配列のサイズは 256 バイトです。</span><span class="sxs-lookup"><span data-stu-id="394fa-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="394fa-118">固定サイズの [char](../../../csharp/language-reference/keywords/char.md) 型バッファーは、エンコーディングに関係なく常に、1 文字あたり 2 バイトを消費します。</span><span class="sxs-lookup"><span data-stu-id="394fa-118">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="394fa-119">これは、char 型のバッファーが、`CharSet = CharSet.Auto` または `CharSet = CharSet.Ansi` で API メソッドや構造体にマーシャリングされたときにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="394fa-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="394fa-120">詳細については、「<xref:System.Runtime.InteropServices.CharSet>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="394fa-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="394fa-121">一般的な固定サイズの配列としては、他にも [bool](../../../csharp/language-reference/keywords/bool.md) 配列があります。</span><span class="sxs-lookup"><span data-stu-id="394fa-121">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="394fa-122">`bool` 配列内の要素のサイズは常に 1 バイトです。</span><span class="sxs-lookup"><span data-stu-id="394fa-122">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="394fa-123">`bool` 配列は、ビット配列やバッファーの作成には適していません。</span><span class="sxs-lookup"><span data-stu-id="394fa-123">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="394fa-124">C# コンパイラおよび共通言語ランタイム (CLR) は、[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) を使って作成されたメモリを除き、バッファー オーバーランのセキュリティ チェックを実行しません。</span><span class="sxs-lookup"><span data-stu-id="394fa-124">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="394fa-125">その他のアンセーフ コードと同様、十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="394fa-125">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="394fa-126">アンセーフ バッファーは、次の点で通常の配列とは異なります。</span><span class="sxs-lookup"><span data-stu-id="394fa-126">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="394fa-127">アンセーフ バッファーの使用は、unsafe コンテキストに限られます。</span><span class="sxs-lookup"><span data-stu-id="394fa-127">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="394fa-128">アンセーフ バッファーは常にベクタ (1 次元配列) です。</span><span class="sxs-lookup"><span data-stu-id="394fa-128">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="394fa-129">配列の宣言には要素数を指定する必要があります (例: `char id[8]`)。</span><span class="sxs-lookup"><span data-stu-id="394fa-129">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="394fa-130">`char id[]` のようにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="394fa-130">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="394fa-131">アンセーフ バッファーは、unsafe コンテキストで構造体のインスタンス フィールドとしてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="394fa-131">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394fa-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="394fa-132">See Also</span></span>  
 [<span data-ttu-id="394fa-133">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="394fa-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="394fa-134">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="394fa-134">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="394fa-135">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="394fa-135">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="394fa-136">相互運用性</span><span class="sxs-lookup"><span data-stu-id="394fa-136">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
