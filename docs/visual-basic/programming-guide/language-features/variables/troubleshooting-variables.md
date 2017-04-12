---
title: "Visual Basic における変数のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 9cddf7ced50c42514ebc9a613f49adee31edde0b
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-variables-in-visual-basic"></a>Visual Basic における変数のトラブルシューティング
このページの一覧で変数を使用するときに発生する一般的な問題について[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
## <a name="unable-to-access-members-of-an-object"></a>オブジェクトのメンバーにアクセスできない  
 コードからオブジェクトのプロパティまたはメソッドにアクセスしようとしたときに、発生する可能性があるエラーは&2; つあります。  
  
-   オブジェクト変数を特定の型として宣言した後、その型で定義されていないメンバーを参照すると、コンパイラによってエラー メッセージが生成されることがあります。  
  
-   実行時<xref:System.MemberAccessException>オブジェクト変数に割り当てられているオブジェクトがアクセスしようとして、コードのメンバーを公開していないときに発生します</xref:System.MemberAccessException>。 変数の場合[Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)、メンバーがない場合に、この例外を取得することもできます`Public`します。 この原因は、遅延バインディングで許可されているのは、 `Public` メンバーへのアクセスのみのためです。  
  
 ときに、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)セットの型チェック`On`、オブジェクト変数が宣言するクラスのプロパティとメソッドのみにアクセスできます。 次に例を示します。  

 [!code-vb[VbVbalrVariables&#2;](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 この例では`p`のメンバーのみを使用して、<xref:System.Object>変数名は、クラス自体、`Left`プロパティ</xref:System.Object>。 これに対して、`q`型として宣言された<xref:System.Windows.Forms.Label>、すべてのメソッドとプロパティを使用できるように、<xref:System.Windows.Forms.Label>クラス、<xref:System.Windows.Forms>名前空間</xref:System.Windows.Forms></xref:System.Windows.Forms.Label></xref:System.Windows.Forms.Label>。  
  
### <a name="correct-approach"></a>修正方法  
 特定のクラスのオブジェクトにあるすべてのメンバーにアクセスできるようにするには、オブジェクト変数をできる限りそのクラスの型で宣言します。 設定する必要がある場合はコンパイル時に入力オブジェクトを把握していない場合の例については、これを行うことはできません、`Option Strict`に`Off`を指定して変数を宣言し、 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)します。 これにより任意の型のオブジェクトを変数に代入できます。また、現在変数に代入されているオブジェクトが受け入れ可能な型であることを確認する必要があります。 使用することができます、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)この判断を行うためです。  
  
## <a name="other-components-cannot-access-your-variable"></a>他のコンポーネントが変数にアクセスできない  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]名前は*大文字*します。 2 つの名前の違いが英字の大文字と小文字の違いだけの場合、コンパイラでは&2; つを同じ名前と解釈します。 たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。  
  
 しかし、共通言語ランタイム (CLR) のバインディングでは *大文字と小文字が区別されます* 。 このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。 たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。 後でクラスを再コンパイルして要素の名前を `abc`に変更すると、このクラスを使用していた他のアセンブリがこの要素にアクセスできなくなります。 したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。  
  
 詳細については、次を参照してください。[共通言語ランタイム](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)します。  
  
### <a name="correct-approach"></a>修正方法  
 他のコンポーネントから変数にアクセスできるようにするには、その変数の名前を、大文字と小文字が区別されるものとして扱います。 作成したクラスまたはモジュールをテストするときには、他のアセンブリが適切な変数にバインドされることを確認します。 コンポーネントの公開後は、大文字と小文字の変更を含め、既存の変数名は変更しないようにします。  
  
## <a name="wrong-variable-being-used"></a>誤った変数が使用される  
 同じ名前の&1; つ以上の変数がある場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラはその名前への参照を解決しようとしています。 変数のスコープが異なる場合、コンパイラは、参照を最も狭いスコープの宣言に解決します。 変数のスコープが同じ場合、解決は失敗し、コンパイラはエラーを発行します。 詳細については、次を参照してください。[宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
### <a name="correct-approach"></a>修正方法  
 同じ名前でスコープが異なる変数を使わないようにします。 他のアセンブリまたはプロジェクトを使用している場合は、その外部コンポーネントで定義された名前を使うことはできるだけ避けてください。 同じ名前の変数が複数ある場合は、変数への参照ごとに修飾子を付けるようにしてください。 詳細については、次を参照してください。[宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
## <a name="see-also"></a>関連項目  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [方法: オブジェクトのメンバーにアクセス](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [方法: オブジェクト変数が指す型を確認](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
