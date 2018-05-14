---
title: sizeof (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sizeof-c-reference"></a>sizeof (C# リファレンス)
アンマネージ型のサイズ (バイト単位) を取得するときに使用します。 アンマネージ型には、以下の表に示す組み込み型のほか、次の型も含まれます。  
  
-   列挙型  
  
-   ポインター型  
  
-   参照型のフィールドやプロパティが含まれないユーザー定義の構造体  
  
 次の例は、`int` のサイズを取得する方法を示しています。  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>コメント  
 C# バージョン 2.0 以降、組み込み型に `sizeof` を適用するときに、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) モードを使用する必要がなくなりました。  
  
 `sizeof` 演算子はオーバーロードできません。 `sizeof` 演算子により返される値の型は `int` です。 次の表に、特定の組み込み型をオペランドとする `sizeof` 式と、代用される定数値を示します。  
  
|正規表現|定数値|  
|----------------|--------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 (Unicode)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 struct など、その他の型については、`sizeof` 演算子はアンセーフ コード ブロックでのみ使用できます。 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> メソッドを使用できますが、このメソッドによって返される値は常に `sizeof` によって返される値と同じとは限りません。 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> は、型のマーシャリング後にサイズを返します。一方、`sizeof` は、共通言語ランタイムによって割り当てられたサイズ (埋め込みを含む) を返します。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [enum](../../../csharp/language-reference/keywords/enum.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [定数](../../../csharp/programming-guide/classes-and-structs/constants.md)
