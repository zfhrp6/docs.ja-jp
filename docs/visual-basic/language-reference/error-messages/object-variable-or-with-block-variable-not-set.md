---
title: オブジェクト変数または With ブロック変数が設定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2bd1be83f57dbdc7a64b407dc1052074e19c74b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597665"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>オブジェクト変数または With ブロック変数が設定されていません。
無効なオブジェクト変数を参照しています。   このエラーが発生する原因は複数あります。  
  
-   変数は、型を指定せずに宣言されました。 型を指定せず、変数を宣言している場合、既定値は入力`Object`です。  
  
     たとえば、変数を使用して宣言`Dim x`型になります`Object;`で宣言された変数`Dim x As String`型になります`String`です。  
  
    > [!TIP]
    >  `Option Strict`ステートメントで暗黙の型の指定は許可されていません、`Object`型です。 型を省略すると、コンパイル時エラーが発生します。 参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。  
  
-   設定されているオブジェクトを参照しようとしています `Nothing`  
  
     である必要があります。  
  
-   適切に宣言されていない配列変数の要素にアクセスしようとするとします。  
  
     たとえば、配列として宣言されている`products() As String`配列の要素を参照しようとする場合、エラーをトリガーする`products(3) = "Widget"`です。 配列は、要素が存在しないと、オブジェクトとして扱われます。  
  
-   アクセス コード内にしようとすると、`With...End With`ブロック、ブロックが初期化される前にします。   A`With...End With`ブロックを実行することで初期化する必要があります、`With`ステートメントのエントリ ポイントです。  
  
> [!NOTE]
>  以前のバージョンの Visual Basic または VBA でこのエラーを使用せず、変数に値を割り当てることによってもにトリガーされる、`Set`キーワード (`x = "name"`の代わりに`Set x = "name"`)。 `Set`キーワードは Visual Basic .Net で無効になりました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  設定`Option Strict`に`On`ファイルの先頭に次のコードを追加することで。  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  有効にしたくない場合`Option Strict`、せず、型指定されている変数がある場合、コードを検索 (`Dim x`の代わりに`Dim x As String`) し、目的の型を宣言に追加します。  
  
3.  設定されているオブジェクト変数を参照していないことを確認`Nothing`です。  コード内のキーワードの`Nothing`設定されていないオブジェクトになるように、コードを修正および`Nothing`後を参照していることになるまでです。  
  
4.  アクセスする前に、配列変数の寸法はことを確認します。 最初に、配列を作成するときに、ディメンションを割り当てることができますか (`Dim x(5) As String`の代わりに`Dim x() As String`)、または使用、`ReDim`キーワードを最初にアクセスする前に、配列の次元を設定します。  
  
5.  確認、`With`ブロックが実行することによって初期化されて、`With`ステートメントのエントリ ポイントです。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
