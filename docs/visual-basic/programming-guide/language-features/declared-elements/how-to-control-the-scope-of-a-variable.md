---
title: "How to: Control the Scope of a Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], scope"
  - "declared elements, scope"
  - "visibility, declared elements"
  - "variables [Visual Basic], visibility"
  - "scope, declared elements"
  - "scope, variables"
  - "scope, Visual Basic"
  - "declared elements, visibility"
  - "visibility, variables"
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Control the Scope of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

通常、変数が宣言された領域内全体がその変数の*スコープ*となります。つまり、その範囲から変数を参照できます。  場合によっては、変数の*アクセス レベル*がスコープに影響を及ぼします。  
  
 詳細については、「[Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)」を参照してください。  
  
## ブロックまたはプロシージャ レベルのスコープ  
  
#### 変数をブロック内でのみ参照できるようにするには  
  
-   変数の [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を、そのブロックの開始ステートメントと終了ステートメントの間に置きます。たとえば、`For` ループの `For` ステートメントと `Next` ステートメントの間です。  
  
     これにより、ブロック内でのみ変数が参照できます。  
  
#### 変数をプロシージャ内でのみ参照できるようにするには  
  
-   変数の `Dim` ステートメントを、プロシージャの内側の、しかも何のブロック内 \(`With`...`End With` ブロックなど\) にも属さない場所に記述します。  
  
     これにより、プロシージャに含まれている各ブロックの内部も含めたプロシージャの内部からのみ変数を参照できます。  
  
## モジュールまたは名前空間レベルのスコープ  
 便宜上、モジュール、クラス、および構造体に対して、*モジュール レベル* という 1 つの用語を使用します。  モジュール レベルの変数のアクセス レベルによってスコープが決まります。  また、モジュール、クラス、または構造体を含んでいる名前空間もスコープに影響します。  
  
#### モジュール、クラス、または構造体全体にわたって変数を参照できるようにするには  
  
1.  変数の `Dim` ステートメントを、モジュール、クラス、または構造体の内側の、しかも何のプロシージャ内にも属さない場所に記述します。  
  
2.  `Dim` ステートメントには [Private](../../../../visual-basic/language-reference/modifiers/private.md) キーワードを含めます。  
  
3.  これにより、モジュール、クラス、または構造体のどこからでも変数を参照できます。外側からは参照できません。  
  
#### 名前空間全体にわたって変数を参照できるようにするには  
  
1.  変数の `Dim` ステートメントを、モジュール、クラス、または構造体の内側の、しかも何のプロシージャ内にも属さない場所に記述します。  
  
2.  `Dim` ステートメントには [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) キーワードまたは [Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワードを含めます。  
  
3.  これにより、モジュール、クラス、または構造体を含む名前空間内のどこからでも変数を参照できます。  
  
## 使用例  
 次の例では、モジュール レベルで変数を宣言し、モジュール内のコードからのみ参照できるように制限しています。  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 上の例では、`demonstrateScope` モジュールで定義されているすべてのプロシージャから、`String` 型の変数 `strMsg` を参照できます。  `usePrivateVariable` プロシージャを呼び出すと、文字列変数 `strMsg` の内容がダイアログ ボックスに表示されます。  
  
 上の例を次のように変更すると、宣言した名前空間内のすべてのコードで文字列変数 `strMsg` を参照できるようになります。  
  
```  
Public strMsg As String  
```  
  
## 信頼性の高いプログラミング  
 変数のスコープが狭いほど、同じ名前の別の変数を誤って参照してしまう可能性は少なくなります。  また、参照先との一致に関する問題も最小化できます。  
  
## .NET Framework セキュリティ  
 変数のスコープが狭いほど、悪意のあるコードによって変数が不正に使用される可能性が少なくなります。  
  
## 参照  
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)