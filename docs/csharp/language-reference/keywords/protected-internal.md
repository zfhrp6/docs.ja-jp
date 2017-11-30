---
title: "保護された内部 (c# リファレンス)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a>保護された内部 (c# リファレンス)
`protected internal`キーワードの組み合わせは、メンバー アクセス修飾子。 プロテクト内部メンバーは、現在のアセンブリとは、含んでいるクラスから派生した型からアクセス可能です。 `protected internal` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。 
   
## <a name="example"></a>例  
 基底クラスのプロテクト内部メンバーは、含んでいるアセンブリ内の任意の型からアクセスします。 派生クラス型の変数を使用して、アクセスが行われる場合にのみ、別のアセンブリ内にある派生クラスではアクセスもできます。 たとえば、次のコード セグメントを考えてみます。  

```
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
  
```  
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
 この例には、2 つのファイル (`Assembly1.cs` と `Assembly2.cs`) が含まれています。 最初のファイルにはパブリック基底クラスが含まれています`BaseClass`、および別のクラス、`TestAccess`です。 `BaseClass`プロテクトの内部メンバーを所有している`myValue`、によってアクセスされる、`TestAccess`型です。 2 番目のファイルへのアクセスに`myValue`のインスタンスを通じて`BaseClass`、派生クラスのインスタンスを使用してこのメンバーへのアクセス中にエラーが生成されます`DerivedClass`は成功します。 

 構造体のメンバーにすることはできません`protected internal`のため、構造体は継承できません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [Internal virtual キーワードのセキュリティに関する注意事項](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
