---
title: "ポインター型 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 19
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
ms.openlocfilehash: 1a4ebc69762f18dc630100b544c18df0f43734ac
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-types-c-programming-guide"></a>ポインター型 (C# プログラミング ガイド)
unsafe コンテキストの型には、ポインター型、値型、または参照型を設定できます。 ポインター型の宣言は、次のいずれかの形式になります。  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 次の型はいずれもポインター型になります。  
  
-   [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[char](../../../csharp/language-reference/keywords/char.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md)、または [bool](../../../csharp/language-reference/keywords/bool.md)。  
  
-   任意の[列挙](../../../csharp/language-reference/keywords/enum.md)型。  
  
-   任意のポインター型。  
  
-   アンマネージ型のフィールドのみを含むユーザー定義の struct 型。  
  
 ポインター型は [object](../../../csharp/language-reference/keywords/object.md) を継承せず、ポインター型と `object` の間で変換を行う方法はありません。 また、ボックス化とボックス化解除もポインターをサポートしません。 ただし、異なるポインター型の間で変換したり、ポインター型と整数型の間で変換したりすることはできます。  
  
 同じ 1 つの宣言で複数のポインターを宣言する場合、アスタリスク (*) は基底の型だけに記述します。各ポインター名のプレフィックスとしては使用しません。 例:  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 オブジェクト参照は、それを指すポインターがあってもガベージ コレクションされる可能性があるため、ポインターによって参照や参照を含む[構造体](../../../csharp/language-reference/keywords/struct.md)を指すことはできません。 ガベージ コレクターは、オブジェクトを指すポインター型があるかどうかを追跡しません。  
  
 `myType*` 型のポインター変数の値は、`myType` 型の変数のアドレスです。 ポインター型の宣言の例を次に示します。  
  
|例|説明|  
|-------------|-----------------|  
|`int* p`|`p` は、整数へのポインターです。|  
|`int** p`|`p` は、整数へのポインターのポインターです。|  
|`int*[] p`|`p` は、整数へのポインターの 1 次元配列です。|  
|`char* p`|`p` は、char へのポインターです。|  
|`void* p`|`p` は、未知の型へのポインターです。|  
  
 ポインター間接演算子 * を使用すると、ポインター変数が指す位置にあるコンテンツにアクセスできます。 たとえば、次のような宣言があるとします。  
  
```  
int* myVariable;  
```  
  
 この例の式 `*myVariable` は、`int` に含まれているアドレスの位置にある `myVariable` 変数を示しています。  
  
 トピック「[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)」および「[ポインター変換](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)」に、ポインターの例がいくつか記載されています。  次の例は、`unsafe` キーワードと `fixed` ステートメントの必要性、および内部ポインターのインクリメント方法を示しています。  このコードは、コンソール アプリケーションの Main 関数に貼り付けて実行することができます  (**プロジェクト デザイナー**でアンセーフ コードを有効にすることを忘れないでください。**[プロジェクト]** を選択し、メニュー バーの **[プロパティ]** をクリックし、**[ビルド]** タブで **[アンセーフ コードの許可]** を選択します)。  
  
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
  
 間接演算子は、`void*` 型のポインターに適用できません。 ただし、void ポインターと他のポインター型はキャストを使用して相互に変換できます。  
  
 ポインターは、`null` にできます。 null ポインターに間接演算子を適用すると、実装で定義されている動作が発生します。  
  
 ポインターをメソッド間で引き渡すと、未定義の動作が発生する可能性があります。 たとえば、Out パラメーターや Ref パラメーターを介してポインターをローカル変数に返したり、関数の結果として返したりする場合です。 ポインターが固定ブロックに設定されていた場合は、そのポインターが指す変数が既に固定されていない可能性があります。  
  
 次の表は、unsafe コンテキストでポインターに使用できる演算子とステートメントの一覧を示しています。  
  
|演算子/ステートメント|用途|  
|-------------------------|---------|  
|*|ポインターの間接参照を実行します。|  
|->|ポインター経由で構造体のメンバーにアクセスします。|  
|[]|ポインターにインデックスを付けます。|  
|`&`|変数のアドレスを取得します。|  
|++ および --|ポインターをインクリメントおよびデクリメントします。|  
|+ および -|ポインター演算を実行します。|  
|==、!=、\<、>、\<=、>=|ポインターを比較します。|  
|`stackalloc`|スタックにメモリを割り当てます。|  
|`fixed` ステートメント|変数を一時的に固定して、そのアドレスを取得できるようにします。|  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [ポインター変換](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)   
 [ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)

