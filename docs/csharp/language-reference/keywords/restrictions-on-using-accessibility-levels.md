---
title: "アクセシビリティ レベルの使用に関する制限事項 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アクセス修飾子 [C#], アクセシビリティ レベルの制限事項"
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# アクセシビリティ レベルの使用に関する制限事項 (C# リファレンス)
宣言で型を指定する場合、その型のアクセシビリティ レベルがメンバーまたは他の型のアクセシビリティ レベルに依存するかどうかをチェックします。  たとえば、直接基本クラスは、少なくともその派生クラスと同程度にアクセス可能である必要があります。  次の宣言はコンパイラ エラーになりますが、それは基本クラス `BaseClass` のアクセシビリティが `MyClass` のアクセシビリティよりも低いためです。  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 宣言されたアクセシビリティ レベルの制限を次の表にまとめて示します。  
  
|コンテキスト|解説|  
|------------|--------|  
|[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)|クラスの型の直接基本クラスは、少なくとも、クラスの型自体と同程度にアクセス可能である必要があります。|  
|[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)|インターフェイスの型の明示的な基本インターフェイスは、少なくとも、インターフェイスの型自体と同程度にアクセス可能である必要があります。|  
|[デリゲート](../../../csharp/programming-guide/delegates/index.md)|デリゲート型の戻り値の型およびパラメーターの型は、少なくとも、デリゲート型自体と同程度にアクセス可能である必要があります。|  
|[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)|定数の型は、少なくとも定数自体と同程度にアクセス可能である必要があります。|  
|[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)|フィールドの型は、少なくともフィールド自体と同程度にアクセス可能である必要があります。|  
|[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)|メソッドの戻り値の型およびパラメーターの型は、少なくとも、メソッド自体と同程度にアクセス可能である必要があります。|  
|[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)|プロパティの型は、少なくともプロパティ自体と同程度にアクセス可能である必要があります。|  
|[イベント](../../../csharp/programming-guide/events/index.md)|イベントの型は、少なくともイベント自体と同程度にアクセス可能である必要があります。|  
|[インデクサー](../../../csharp/programming-guide/indexers/index.md)|インデクサーの型およびパラメーターの型は、少なくとも、インデクサー自体と同程度にアクセス可能である必要があります。|  
|[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|演算子の戻り値の型およびパラメーターの型は、少なくとも、演算子自体と同程度にアクセス可能である必要があります。|  
|[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)|コンストラクターのパラメーターの型は、少なくともコンストラクター自体と同程度にアクセス可能である必要があります。|  
  
## 使用例  
 各種の型の不適切な宣言の例を次に示します。  各宣言へのコメントに、予期されるコンパイラ エラーを示します。  
  
```  
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
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)