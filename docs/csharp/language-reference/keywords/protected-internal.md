---
title: protected internal (C# リファレンス)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="protected-internal-c-reference"></a>protected internal (C# リファレンス)
キーワード組み合わせ `protected internal` はメンバー アクセス修飾子です。 protected internal メンバーには、現在のアセンブリから、または包含クラスから派生した型からアクセスできます。 `protected internal` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。 
   
## <a name="example"></a>例  
 基底クラスのプロテクト内部メンバーは、包含アセンブリ内の任意の型からアクセスします。 派生クラス型の変数経由でアクセスする場合にのみ、別のアセンブリにある派生クラスでもアクセスできます。 たとえば、次のコード セグメントを考えてみます。  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```csharp  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 この例には、2 つのファイル (`Assembly1.cs` と `Assembly2.cs`) が含まれています。 最初のファイルには public 基底クラスである `BaseClass` ともう 1 つのクラスである `TestAccess` が含まれています。 `BaseClass` は protected internal メンバーの `myValue` を持っています。これは `TestAccess` 型にアクセスされます。 2 番目のファイルでは、`BaseClass` のインスタンス経由で `myValue` にアクセスしようとするとエラーが発生します。一方で、派生クラス `DerivedClass` のインスタンスからこのメンバーにアクセスすると成功します。 

 構造体は継承できないため、構造体メンバーは `protected internal` になりません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [Internal Virtual キーワードのセキュリティ関連事項](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
