---
title: アクセシビリティ レベルの使用に関する制限事項 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172410"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>アクセシビリティ レベルの使用に関する制限事項 (C# リファレンス)
宣言で型を指定する場合、その型のアクセシビリティ レベルがメンバーまたは他の型のアクセシビリティ レベルに依存するかどうかをチェックしてください。 たとえば、直接基底クラスは、少なくともその派生クラスと同程度にアクセス可能である必要があります。 次の宣言はコンパイラ エラーになりますが、それは基底クラス `BaseClass` のアクセシビリティが `MyClass` のアクセシビリティよりも低いためです。  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 宣言されたアクセシビリティ レベルの制限を次の表にまとめます。  
  
|コンテキスト|コメント|  
|-------------|-------------|  
|[クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)|クラスの型の直接基底クラスは、少なくとも、クラスの型自体と同程度にアクセス可能である必要があります。|  
|[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)|インターフェイスの型の明示的な基本インターフェイスは、少なくとも、インターフェイスの型自体と同程度にアクセス可能である必要があります。|  
|[デリゲート](../../../csharp/programming-guide/delegates/index.md)|デリゲート型の戻り値の型およびパラメーターの型は、少なくとも、デリゲート型自体と同程度にアクセス可能である必要があります。|  
|[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)|定数の型は、少なくとも定数自体と同程度にアクセス可能である必要があります。|  
|[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)|フィールドの型は、少なくともフィールド自体と同程度にアクセス可能である必要があります。|  
|[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)|メソッドの戻り値の型およびパラメーターの型は、少なくとも、メソッド自体と同程度にアクセス可能である必要があります。|  
|[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)|プロパティの型は、少なくともプロパティ自体と同程度にアクセス可能である必要があります。|  
|[イベント](../../../csharp/programming-guide/events/index.md)|イベントの型は、少なくともイベント自体と同程度にアクセス可能である必要があります。|  
|[インデクサー](../../../csharp/programming-guide/indexers/index.md)|インデクサーの型とパラメーターの型は、少なくとも、インデクサー自体と同程度にアクセス可能である必要があります。|  
|[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|演算子の戻り値の型とパラメーターの型は、少なくとも、演算子自体と同程度にアクセス可能である必要があります。|  
|[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)|コンストラクターのパラメーターの型は、少なくとも、コンストラクター自体と同程度にアクセス可能である必要があります。|  
  
## <a name="example"></a>例  
 さまざまな型の不適切な宣言の例を次に示します。 各宣言の後のコメントは、予期されるコンパイラ エラーを示しています。  
  
```csharp  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
