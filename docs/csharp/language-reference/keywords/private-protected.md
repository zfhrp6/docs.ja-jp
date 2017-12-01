---
title: "private protected (c# リファレンス)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a>private protected (c# リファレンス)
`private protected`キーワードの組み合わせは、メンバー アクセス修飾子。 プライベート、プロテクト メンバーは、含んでいるアセンブリ内でのみが、外側のクラスから派生した型からアクセス可能です。 `private protected` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。 
   
## <a name="example"></a>例  
 変数の静的な型が派生クラス型である場合にのみ、基底クラスのプライベート、プロテクト メンバーは、含んでいるアセンブリでの派生型からアクセス可能です。 たとえば、次のコード セグメントを考えてみます。  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 この例には、2 つのファイル (`Assembly1.cs` と `Assembly2.cs`) が含まれています。 最初のファイルにはパブリック基底クラスが含まれています`BaseClass`、および、その派生型`DerivedClass1`です。 `BaseClass`プライベートのプロテクト メンバーを所有している`myValue`、どの`DerivedClass1`に 2 つの方法でアクセスしようとしています。 最初の試行にアクセスする`myValue`のインスタンスを通じて`BaseClass`でエラーが発生します。 ただし、継承されたメンバーとして使用しようとすると、`DerivedClass1`は成功します。
2 番目のファイルへのアクセスに`myValue`の継承されたメンバーと`DerivedClass2`Assembly1 での派生型からアクセス可能なだけ、エラーが生成されます。 

 構造体のメンバーにすることはできません`private protected`のため、構造体は継承できません。  
  
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
