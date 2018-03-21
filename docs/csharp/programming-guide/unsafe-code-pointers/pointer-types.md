---
title: "ポインター型 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe7b926bdf9f662d25f2fe960b51fc8254b7aa3a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="8e2cd-102">ポインター型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="8e2cd-103">unsafe コンテキストの型には、ポインター型、値型、または参照型を設定できます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="8e2cd-104">ポインター型の宣言は、次のいずれかの形式になります。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="8e2cd-105">次の型はいずれもポインター型になります。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="8e2cd-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[char](../../../csharp/language-reference/keywords/char.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md)、または [bool](../../../csharp/language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="8e2cd-107">任意の[列挙](../../../csharp/language-reference/keywords/enum.md)型。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="8e2cd-108">任意のポインター型。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="8e2cd-109">アンマネージ型のフィールドのみを含むユーザー定義の struct 型。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="8e2cd-110">ポインター型は [object](../../../csharp/language-reference/keywords/object.md) を継承せず、ポインター型と `object` の間で変換を行う方法はありません。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="8e2cd-111">また、ボックス化とボックス化解除もポインターをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="8e2cd-112">ただし、異なるポインター型の間で変換したり、ポインター型と整数型の間で変換したりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="8e2cd-113">同じ 1 つの宣言で複数のポインターを宣言する場合、アスタリスク (\*) は基底の型だけに記述します。各ポインター名のプレフィックスとしては使用しません。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-113">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="8e2cd-114">例:</span><span class="sxs-lookup"><span data-stu-id="8e2cd-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="8e2cd-115">オブジェクト参照は、それを指すポインターがあってもガベージ コレクションされる可能性があるため、ポインターによって参照や参照を含む[構造体](../../../csharp/language-reference/keywords/struct.md)を指すことはできません。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="8e2cd-116">ガベージ コレクターは、オブジェクトを指すポインター型があるかどうかを追跡しません。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="8e2cd-117">`myType*` 型のポインター変数の値は、`myType` 型の変数のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="8e2cd-118">ポインター型の宣言の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="8e2cd-119">例</span><span class="sxs-lookup"><span data-stu-id="8e2cd-119">Example</span></span>|<span data-ttu-id="8e2cd-120">説明</span><span class="sxs-lookup"><span data-stu-id="8e2cd-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="8e2cd-121">`p` は、整数へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="8e2cd-122">`p` は、整数へのポインターのポインターです。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="8e2cd-123">`p` は、整数へのポインターの 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="8e2cd-124">`p` は、char へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="8e2cd-125">`p` は、未知の型へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="8e2cd-126">ポインター間接演算子 \* を使用すると、ポインター変数が指す位置にあるコンテンツにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-126">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="8e2cd-127">たとえば、次のような宣言があるとします。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="8e2cd-128">この例の式 `*myVariable` は、`int` に含まれているアドレスの位置にある `myVariable` 変数を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="8e2cd-129">トピック「[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)」および「[ポインター変換](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)」に、ポインターの例がいくつか記載されています。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="8e2cd-130">次の例は、`unsafe` キーワードと `fixed` ステートメントの必要性、および内部ポインターのインクリメント方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="8e2cd-131">このコードは、コンソール アプリケーションの Main 関数に貼り付けて実行することができます </span><span class="sxs-lookup"><span data-stu-id="8e2cd-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="8e2cd-132">(**プロジェクト デザイナー**でアンセーフ コードを有効にすることを忘れないでください。**[プロジェクト]** を選択し、メニュー バーの **[プロパティ]** をクリックし、**[ビルド]** タブで **[アンセーフ コードの許可]** を選択します)。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="8e2cd-133">間接演算子は、`void*` 型のポインターに適用できません。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="8e2cd-134">ただし、void ポインターと他のポインター型はキャストを使用して相互に変換できます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="8e2cd-135">ポインターは、`null` にできます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-135">A pointer can be `null`.</span></span> <span data-ttu-id="8e2cd-136">null ポインターに間接演算子を適用すると、実装で定義されている動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="8e2cd-137">ポインターをメソッド間で引き渡すと、未定義の動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="8e2cd-138">たとえば、`in`、`out` または `ref` パラメーターを介してポインターをローカル変数に返したり、関数の結果として返したりするメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-138">Consider a method that returns a pointer to a local variable through an `in`, `out` or `ref` parameter or as the function result.</span></span> <span data-ttu-id="8e2cd-139">ポインターが固定ブロックに設定されていた場合は、そのポインターが指す変数が既に固定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="8e2cd-140">次の表は、unsafe コンテキストでポインターに使用できる演算子とステートメントの一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="8e2cd-141">演算子/ステートメント</span><span class="sxs-lookup"><span data-stu-id="8e2cd-141">Operator/Statement</span></span>|<span data-ttu-id="8e2cd-142">使用</span><span class="sxs-lookup"><span data-stu-id="8e2cd-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="8e2cd-143">ポインターの間接参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="8e2cd-144">ポインター経由で構造体のメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="8e2cd-145">[]</span><span class="sxs-lookup"><span data-stu-id="8e2cd-145">[]</span></span>|<span data-ttu-id="8e2cd-146">ポインターにインデックスを付けます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="8e2cd-147">変数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="8e2cd-148">++ および --</span><span class="sxs-lookup"><span data-stu-id="8e2cd-148">++ and --</span></span>|<span data-ttu-id="8e2cd-149">ポインターをインクリメントおよびデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="8e2cd-150">+ および -</span><span class="sxs-lookup"><span data-stu-id="8e2cd-150">+ and -</span></span>|<span data-ttu-id="8e2cd-151">ポインター演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="8e2cd-152">==、!=、\<、>、\<=、>=</span><span class="sxs-lookup"><span data-stu-id="8e2cd-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="8e2cd-153">ポインターを比較します。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="8e2cd-154">スタックにメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="8e2cd-155">`fixed` ステートメント</span><span class="sxs-lookup"><span data-stu-id="8e2cd-155">`fixed` statement</span></span>|<span data-ttu-id="8e2cd-156">変数を一時的に固定して、そのアドレスを取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8e2cd-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="8e2cd-157">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="8e2cd-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e2cd-158">参照</span><span class="sxs-lookup"><span data-stu-id="8e2cd-158">See Also</span></span>  
 [<span data-ttu-id="8e2cd-159">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8e2cd-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8e2cd-160">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="8e2cd-160">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="8e2cd-161">ポインター変換</span><span class="sxs-lookup"><span data-stu-id="8e2cd-161">Pointer Conversions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [<span data-ttu-id="8e2cd-162">ポインター式</span><span class="sxs-lookup"><span data-stu-id="8e2cd-162">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="8e2cd-163">型</span><span class="sxs-lookup"><span data-stu-id="8e2cd-163">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="8e2cd-164">unsafe</span><span class="sxs-lookup"><span data-stu-id="8e2cd-164">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="8e2cd-165">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="8e2cd-165">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="8e2cd-166">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8e2cd-166">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)  
 [<span data-ttu-id="8e2cd-167">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="8e2cd-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
