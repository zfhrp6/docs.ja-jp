---
title: "遅延バインディングされたオーバー ロードの解決には適用できません &#39;です。&lt;procedurename&gt;&#39;へのアクセスのインスタンスがインターフェイス型であるためです。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>遅延バインディングされたオーバー ロードの解決には適用できません &#39;です。&lt;procedurename&gt;&#39;へのアクセスのインスタンスがインターフェイス型であるためです。
オーバー ロードされたプロパティまたはプロシージャへの参照を解決するのには、コンパイラがしようとしていますが、型の引数であるため、参照が失敗した`Object`と参照元のオブジェクトには、インターフェイスのデータ型。 `Object`引数は、遅延バインディングとして参照を解決するのには、コンパイラを強制します。  
  
 このような場合は、コンパイラは、基になるインターフェイスの代わりに、実装するクラスをオーバー ロードを解決します。 クラスのオーバー ロードされたバージョンのいずれかの名前を変更、コンパイラでは、名前が異なるため、オーバー ロードするには、そのバージョンは考慮されません。 これで、コンパイラを無視する、名前を変更したバージョンの参照を解決するのには、適切な選択されている可能性があります。  
  
 **エラー ID:** BC30933  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して`CType`から引数をキャストする`Object`を呼び出したいオーバー ロードのシグネチャで指定された型にします。  
  
     注意を参照しているオブジェクトは基になるインターフェイスにキャストも効果はありません。 このエラーを回避する引数をキャストする必要があります。  
  
## <a name="example"></a>例  
 次の例では、オーバー ロードされたへの呼び出し`Sub`コンパイル時にこのエラーが発生するプロシージャ。  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 コンパイラへの呼び出しを許可された場合、上記の例では`s1`が書き込まれると、解決が行わクラスを通じて`c1`インターフェイスではなく`i1`です。 つまり、コンパイラは見なしません`s2`名前が異なるため`c1`で定義されている適切な選択である場合でも、`i1`です。  
  
 次のコード行のいずれかへの呼び出しを変更することで、エラーを修正することができます。  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 前の行のコードに明示的にキャスト、`Object`変数`o1`オーバー ロードでは定義されているパラメーターの型のいずれかにします。  
  
## <a name="see-also"></a>関連項目  
 [プロシージャのオーバーロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [オーバーロードの解決](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)
