---
title: "Type Promotion (Visual Basic) | Microsoft Docs"
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
  - "declared elements, scope"
  - "visibility, declared elements"
  - "Partial keyword, unexpected results with type promotion"
  - "scope, declared elements"
  - "scope, Visual Basic"
  - "type promotion"
  - "declared elements, visibility"
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Type Promotion (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

モジュール内でプログラミング要素を宣言すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、そのスコープをモジュールが含まれている名前空間にまで広げます。  これを、*型の上位変換*と呼びます。  
  
 モジュールのスケルトン定義およびそのモジュールの 2 つのメンバーを、次の例に示します。  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 `projModule` 内部で、モジュール レベルで宣言されたプログラミング要素は `projNamespace` に上位変換されます。  前の例では、`basicEnum` および `innerClass` は上位変換されますが、`numberSub` はモジュール レベルで宣言されていないため上位変換されません。  
  
## 型の上位変換による効果  
 型の上位変換による効果は、修飾文字列にモジュール名を含める必要がなくなるということです。  次の例では、前の例のプロシージャに対して 2 つの呼び出しを行っています。  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 前の例では、最初の呼び出しで完全な修飾文字列を使用しています。  しかし、型の上位変換によりこれは必要ありません。  2 番目の呼び出しでもモジュールのメンバーにアクセスしていますが、修飾文字列に `projModule` を含めていません。  
  
## 型の上位変換の無効化  
 名前空間に既にモジュール メンバーと同じ名前のメンバーがある場合、そのモジュール メンバーに対する型の上位変換は無効になります。  列挙型のスケルトン定義および同じ名前空間内のモジュールを、次の例に示します。  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 この例では、同じ名前の列挙型が名前空間レベルで既に存在するため、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は `abc` クラスを `thisNameSpace` に上位変換できません。  `abcSub` にアクセスするには、完全な修飾文字列 `thisNamespace.thisModule.abc.abcSub` を指定する必要があります。  しかし、クラス `xyz` は上位変換されたままなので、短い修飾文字 `thisNamespace.xyz.xyzSub` を使用して `xyzSub` にアクセスできます。  
  
### 部分型に対する型の上位変換の無効化  
 モジュール内のクラスまたは構造体で [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) キーワードが使用されている場合、名前空間に同じ名前のメンバーがあるかどうかに関係なく、そのクラスまたは構造体に対する型の上位変換は自動的に無効化されます。  モジュール内のその他の要素は、そのまま型の上位変換の対象となります。  
  
 **結果。**部分定義の型の上位変換の無効化は、予期しない結果、さらにコンパイル エラーを生じさせる可能性があります。  クラスのスケルトン部分定義、そのうちの 1 つはモジュール内にある場合を、次の例に示します。  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 前の例では、開発者は `sampleClass` の 2 つの部分定義がコンパイラによってマージされることを想定しています。  しかし、コンパイラでは `sampleModule` 内の部分定義の上位変換は考慮されません。  その結果、両方とも名前は `sampleClass` ですがパスの修飾が異なる、2 つの独立し、区別されたクラスをコンパイルしようとします。  
  
 コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。  
  
## 推奨  
 プログラミングでは、次の方法に従うことをお勧めします。  
  
-   **一意の名前。**プログラミング要素の名前付けについて完全に制御する場合、どのような場合でも一意の名前を使用することをお勧めします。  名前がまったく同じであると余分に修飾する必要があり、コードが読み取りにくくなります。  また名前が同じであると軽度のエラーが発生し、予期しない結果が生じる可能性もあります。  
  
-   **完全修飾。**同一の名前空間内でモジュールと他の要素を使用して作業する場合、最も安全な方法はすべてのプログラミング要素に対して常に、完全修飾を使用することです。  あるモジュール メンバーの上位変換が行われず、そのメンバーを完全に修飾しない場合、誤って別のプログラミング要素にアクセスしてしまう可能性があります。  
  
## 参照  
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)