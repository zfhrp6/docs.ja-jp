---
title: "オブジェクト変数または With ブロック変数が設定されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 820ef0115a6a27d77f10f4e41d95576bbd79bfa3
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a>オブジェクト変数または With ブロック変数が設定されていません。
無効なオブジェクト変数を参照しています。   このエラーが発生する原因は複数あります。  
  
-   型を指定せず、変数が宣言されました。 型を指定せず、変数が宣言されている場合は、既定値は入力`Object`します。  
  
     宣言された変数など`Dim x`型であると`Object;`で宣言された変数`Dim x As String`型であると`String`です。  
  
    > [!TIP]
    >  `Option Strict`ステートメントでは、暗黙の型の指定が禁止されて、`Object`型です。 型を省略すると、コンパイル時エラーが発生します。 参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。  
  
-   設定されているオブジェクトを参照しようとしています。`Nothing`  
  
     」を参照してください。  
  
-   適切に宣言されていない、配列変数の要素にアクセスしようとするとします。  
  
     としての配列の宣言など`products() As String`配列の要素を参照しようとする場合、エラーが発生`products(3) = "Widget"`します。 配列は、要素が存在しない、オブジェクトとして扱われます。  
  
-   アクセス コード内にしようとすると、`With...End With`ブロックを初期化する前にブロックします。   A`With...End With`ブロックを実行することで初期化する必要があります、`With`ステートメントのエントリ ポイントです。  
  
> [!NOTE]
>  以前のバージョンの Visual Basic または VBA でこのエラーを使用せず、変数に値を割り当てることによってもにトリガーされる、`Set`キーワード (`x = "name"`の代わりに`Set x = "name"`)。 `Set`キーワードは Visual Basic .Net で無効になります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  設定`Option Strict`に`On`ファイルの先頭に次のコードを追加することで。  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  有効にしたくない場合`Option Strict`、せず、型指定されている変数がある場合、コードを検索 (`Dim x`の代わりに`Dim x As String`) し、目的の型を宣言に追加します。  
  
3.  設定されている、オブジェクト変数を参照していないことを確認`Nothing`します。  コード内のキーワードの`Nothing`設定されていないオブジェクトになるように、コードを修正して`Nothing`を参照した後になるまでです。  
  
4.  アクセスする前に、配列変数の寸法はことを確認します。 最初に、配列を作成するときに、ディメンションを割り当てることができますか (`Dim x(5) As String`の代わりに`Dim x() As String`)、またはを使用して、`ReDim`最初にアクセスする前に、配列の次元を設定するキーワードです。  
  
5.  必ず、`With`ブロックが実行することによって初期化されて、`With`ステートメントのエントリ ポイントです。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
