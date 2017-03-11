---
title: "Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30933"
  - "bc30933"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "overload resolution, with late-bound argument"
  - "BC30933"
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラがオーバーロードされたプロパティまたはプロシージャへの参照の解決を試みましたが、引数が `Object` 型で、参照元のオブジェクトのデータ型がインターフェイス型であるため、参照が失敗しました。  引数が `Object` 型である場合、コンパイラは遅延バインディングで参照を解決します。  
  
 このような状況では、コンパイラは基のインターフェイスを調べてではなく、実装しているクラスを調べてオーバーロードを解決します。  そのクラスがオーバーロードされたいずれかのクラスの名前を変更していると、コンパイラは名前が違うためにそれをオーバーロードされたクラスと見なしません。  このため、コンパイラは名前が変更されたクラスを無視します。よって、このクラスは参照の解決先として正しい場合でも選択されません。  
  
 **Error ID:** BC30933  
  
### このエラーを解決するには  
  
-   `CType` を使用して、`Object` 型の引数を、呼び出そうとしているオーバーロードのシグネチャに指定された型にキャストします。  
  
     参照元のオブジェクトを基のインターフェイスにキャストしても意味がありません。  このエラーを防ぐには、引数をキャストする必要があります。  
  
## 使用例  
 オーバーロードされた `Sub` プロシージャを、コンパイル時にこのエラーが発生する方法で呼び出す例を次に示します。  
  
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
  
 この例では、コンパイラが定義どおりに `s1` の呼び出しを許可したとすると、`i1` インターフェイスではなく `c1` クラスを介して解決が行われます。  この場合、コンパイラは `s2` の名前が `c1` のときの名前と違うため、`i1` の定義によれば `s2` を選択するのが正しいにもかかわらずこれを無視します。  
  
 このエラーを修正するには、呼び出しの部分を次のいずれかのコード行に変更します。  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 これらのコード行はどちらも、`Object` 型の変数である `o1` を、オーバーロードの際に定義されたいずれかのパラメーター型に明示的にキャストします。  
  
## 参照  
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Overload Resolution](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)